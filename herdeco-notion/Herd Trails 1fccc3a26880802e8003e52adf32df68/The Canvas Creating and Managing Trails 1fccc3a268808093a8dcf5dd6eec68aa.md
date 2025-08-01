# The Canvas: Creating and Managing Trails

# Creating a Trail

<aside>
💡

Before creating a Trail, I highly recommend you [**reference this example](https://herd.eco/trails/0197137c-2be8-7c84-a6dd-69a6daa97026/walk)** of what the final Trail will look like when shared. We plan to support viewing the underlying Trail as well as forking it in the future.

</aside>

To get started, your Herd account will need to be allowlisted by the team. Once trail creation has been activated for your account. click the “Trails” button on the sidebar. You may then proceed to create a new trail on Base or Ethereum.

![Idea Board - start trail (1).jpg](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/Idea_Board_-_start_trail_(1).jpg)

# Adding a Step

Trails are a linear set of write functions to be executed. There is no ability to add branching logic or conditions at this time. As the creator, you are purely prefilling inputs to as many function inputs as you can/want before sharing it with others to execute. Think of it like pre-filling a form.

Initially the Trail creator is dropped into this view after creating a trail:

![image.png](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/image.png)

There are three ways to add a node right now:

1. **Write Function:** Directly select a write function from a contract to add by either pasting a contract address or selecting one from Sage’s memory.
    1. See [Primer on Herd Explorer/Sage Chat](Primer%20on%20Herd%20Explorer%20Sage%20Chat%201fccc3a268808022babfce4a84500764.md) for an intro to Sage.
2. **Swap**: We use [Relay](https://www.relay.link/bridge) as a component to easily swap between chains/tokens. If using the Trails API, it uses 0x instead. You can specify two tokens, and an amount to be swapped.
3. **From Transactions:** This adds a write function from the contract called at the start of a transaction. We take the “to” address and all the inputs and create a step node with pre-filled inputs for you. More details on this option in the section below.

You can add nodes in between steps by clicking the [+] button on the vertical connecting line. For adding read/source nodes, you can click on the add button to the right of each write node.

### Add steps from past transactions in a given wallet address

The easiest way to add new trail nodes is in bulk from any wallet’s transactions. From the “Add Step” node, click “From Transactions → Search and Add Transactions” to get the view below.

This allows you to reference past transactions for any wallet and select/order multiple directly:

![image.png](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/image%201.png)

# Editing a Step (Adding Source Data Nodes)

Once you have added a step, you can click on the new node to pull up the edit panel. Below is a quick visual overview of the panel:

![Idea Board - edit panel (1).jpg](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/Idea_Board_-_edit_panel_(1).jpg)

When a node is selected, any other nodes that have a purple outline are sources of data for this one, and any other nodes that have a blue outline are targets (rely on this one for data).

### Derive Methods

All function inputs show up here with an input field and a “derive method” dropdown. 

1. **`user_input`**: the user will be required to enter an input when they go through the trail
2. **`relational`**: this value will come from another node in the trail (a function input/output or an event). More on this later.
3. **`step_execution`**: this means getting the transaction hash from an execution of a specific primary node/step, and is only used in event nodes (to look up event data in that transaction).
4. **`creator_hardcoded`:** you hardcode a value for the user
5. **`user_wallet`:** the user’s connected wallet address will be used here
6. **`code`:** write ****arbitrary typescript code to transform inputs and outputs

<aside>
⚠️

Before a Trail is considering valid/publishable, all non-**`user_input`** fields will have to have a value. All inputs are **`creator_hardcoded`** by default, meaning you will have to pick a value for the user.

</aside>

### Relational Selection

Typically, you would get relational data by calling a bunch of APIs/RPCs yourself to navigate past transactions or do `eth_call`’s against contracts. We simplify this by allowing you select the relevant data and create a data node for it. These data nodes will show up horizontally (to the right of the write function node).

In the example above, I deploy a Split (a new contract) from a Split Factory. Then, I want to use the created Split address as the fee recipient for a Clanker token I deploy. This will create an event data node to the right, from which i can set the `transaction` relation to be the `createSplit` function step from the step beforehand.

**Basically, the logical flow is that:** `createSplit()` → emits a `SplitCreated()` event → `splitAddress` from event used in input on `deployToken()` on Clanker.

Please watch the video overview at the top of the page to understand this process better.

<aside>
💡

The relational popup will only show contracts that are in the Trail or in Sage memory. For transactions, it will only show past steps in the Trail.

</aside>

<aside>
🔑

If you set the relational input to be a read function, that read function can have a `user_input` input as well that will be shown together to the user all in the same step. Think of it as you’re building up all required input for a form from across different functions, which will roll up into this step.

</aside>

### Code

Select “code” in a derive method then “+ new code node” to create a code node. It comes with a default addition function, but you can edit this easily to do anything you want. Easiest way is to click the “copy” button and paste it into chatgpt/claude and ask it do write the code for you - then paste it back in here and save it.

*We’ll have more docs and examples on code soon, I know this is very barebones* 🙂

### Decimals

You’ll see a “decimals” input field under any “int” type field, which must be hardcoded by the creator.

On-chain there is no concept of “decimals”. In order to work around this, developers have had to add a bunch of zeros to basically simulate decimals. So for USDC (which has 6 decimals), if I want to transfer 5 USDC it will actually show up as `5000000` (`5*10^6`). You can see the decimals by checking the `decimals()` read function on any token.

Decimals are commonly used for stuff like percentages as well, and can vary between 4-6 decimals. Please be very careful in setting decimals correctly. It is best to take a look at past transactions calling a given function for reference as to what number of decimals are correct. The Sage agent can still hallucinate here, so be careful and verify the amount is correct.

### Arrays

Arrays can always be added to by the user, but you can define “defaults” and also “hardcoded” elements. For example, you can add yourself to a split array and the user won’t be able to remove your address. 

Defaults help simplify array elements on the consumer side, for example you should fill in the “decimal” defaults so the user does not have to worry about decimals on an array. Defaults can be edited by clicking “edit array defaults” next to the array value, which will pop up this form. An new elements you add (or the user adds) will copy from these default inputs first.

Arrays also come with a max length param, where you can optionally set a maximum number of elements for the user if needed.

![image.png](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/image%202.png)

## Read Nodes

Any node in the trail can be turned into a “read” node by clicking the read checkbox. This will tell the LLM/user that the data from that node can be useful for informing the next steps by the user. 

You’ll be able to see and test this in the “read data” section when you go to the trail overlook after publishing.

## Adding Descriptions and Intents for the User

You can add an intent in the “Customization” tab on the left side edit panel. This will be shown to the user as a “Creator says:” on the step.

![image.png](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/image%203.png)

You can also add an “intent” to each input by clicking the book icon within “edit inputs”.

Here is an example of what the user sees when executing a trail:

![image.png](The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa/image%204.png)

# Publishing

When your Trail is ready, go to the top left and click “Publish”. You will have to link your Farcaster account, which will be shown to users who use the Trail. 

Once done, you are ready to share the Trail link (which can be found again by clicking the share button next to “Unpublish”) and have a friend “walk” the Trail!

<aside>
💡

Any changes you make to the Trail after publishing will show up immediately. If you break the trail (i.e. inputs are not set) then the Trail will not be usable.

The Trail link is just  `https://herd.eco/trails/{trailId}/overlook`

</aside>

**Learn more here:**

[The Overlook: Sharing and Executing Trails](The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367.md)