# The Overlook: Sharing and Executing Trails

### Sharing and Using a Trail

Executing a trail is fairly straightforward (reference an [**example trail here**](https://herd.eco/trails/0197137c-2be8-7c84-a6dd-69a6daa97026/walk)). This can be shared as a web link or as a Farcaster Mini App by pasting the trail link (click the share button in the top left on the canvas after publishing). 

The user of a trail will only see **`user_input`** fields, unless they click “Advanced” which will show all inputs that the creator has pre-filled as well.

![image.png](The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367/image.png)

Users walking the trail can simulate a step which provides an AI summary as well as Tenderly Simulation results before confirming the transaction.

<aside>
💡

If there are any read nodes, then there will also be a “read data” section where you can test calling a read node.

</aside>

### Testing Read and Transaction Calls

When you submit a read node or transaction step, you will see a preview of the results.

![image.png](The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367/image%201.png)

You’ll notice this comes with a “LLM prompt”, which is targeted at helping any AI you are working with integrate a read node/transaction step into your app. You can also copy the curl request for testing out API calls easily.

Clicking confirm on the main transaction form will bring you an overview on the inputs to be sent onchain:

![image.png](The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367/image%202.png)

Clicking “send” will then send the transaction payload to your wallet for signing.

### Forking a Trail

You can view and fork a trail by clicking the trail icon on the top left of the trail (the button on the right), and then clicking “fork” at the top left of the screen.

![image.png](The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367/image%203.png)

Note that you must have access to the creator beta to be able to see the button and fork trails. Forking will copy everything from the trail you’re looking at into a trail that you own and manage. We keep track of fork history, which will be used for better attribution towards creators in the future.

### Execution Management

Once you press “Start Trail” with a connected wallet, an execution instance is saved on our end. You can click the button in the top left to access your executions. Each “execution” stores all steps executed with the transaction data.

Clicking on an execution will pull up the execution details with links to the transactions. You can manually paste transactions into an execution or turn on “Test Mode” to manually set any transaction hashes in the trail for easier testing. Take note that executing in “Test Mode” does not save any executions.

<aside>
💡

You can “fork” an execution anytime by clicking “re-execute this step” on the top right of any step you have already executed. This will pull all data from previous steps into a new execution which allows you continue executing from there.

</aside>

### Skipping Steps

You can skip steps anytime by clicking “skip this step”. From the API this is just sending a 0x0000… tx hash to this step number.