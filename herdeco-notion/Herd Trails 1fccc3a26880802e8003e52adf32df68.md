# Herd Trails

## What is a Trail?

A "trail" is a linear sequence of write functions across ethereum contracts, where the creator (the trailblazer) determines how function input values will be derived. The consumer of the trail will fill in user inputs and then submit one transaction for each step.

Here are some key benefits of trails:

- Immediately use any deployed contract with LLM search/support, no waiting for integrations from the Herd team.
- Contract upgrades are automatically tracked, so the creator and consumer will see if a trail is outdated.
- Trails are transparent so that anyone can look at all the function-calling logic. They can be easily shared, used, and forked.
- Creating a trail will automatically generate a sandbox app (shareable as a webpage or a farcaster miniapp).
- Trails include an LLM + API for one line copy/paste into any AI tool to help you own apps, automations, chatbots, or anything else on top.

There are four parts to a trail:

- **🔥 The Trailblazer**: the creator of the trail
- **⚙️ The Canvas**: the place creators will create and edit trails
- **🔭 The Overlook:** a sandbox/miniapp for executing the trail
- **📚 The Guidebook:** a single link that can be pasted to any AI tool for help building an app, automation, or anything else you want with a trail.

## App Documentation

[Primer on Herd Explorer/Sage Chat](Herd%20Trails%201fccc3a26880802e8003e52adf32df68/Primer%20on%20Herd%20Explorer%20Sage%20Chat%201fccc3a268808022babfce4a84500764.md)

[The Canvas: Creating and Managing Trails](Herd%20Trails%201fccc3a26880802e8003e52adf32df68/The%20Canvas%20Creating%20and%20Managing%20Trails%201fccc3a268808093a8dcf5dd6eec68aa.md)

[The Overlook: Sharing and Executing Trails](Herd%20Trails%201fccc3a26880802e8003e52adf32df68/The%20Overlook%20Sharing%20and%20Executing%20Trails%201fccc3a26880805596bdf9ba851ee367.md)

[The Guidebook (LLM + API)](Herd%20Trails%201fccc3a26880802e8003e52adf32df68/The%20Guidebook%20(LLM%20+%20API)%20220cc3a2688080ebb568c2641f7c36af.md)

You can create a trail by clicking the trail icon in your navigation sidebar on the left. Please refer to the documents below for information on how to get started with Trails. Each page below contains some basic video guides and screenshots.

<aside>
💡

Sage chat cannot edit trails right now. We’ll add more LLM feature to make the creator experience better soon 🙂

</aside>

### App Guides

Here’s a simple overview of end-to-end creating a trail and then an app on top:

[https://share.descript.com/view/jiZdPpmdKFe](https://share.descript.com/view/jiZdPpmdKFe)

Here’s a more complex [**trail**](https://herd.eco/trails/0197137c-2be8-7c84-a6dd-69a6daa97026/walk) overlook to help you understand the end product output. The underlying trail can be viewed/forked by clicking the trail icon in the sandbox. Here’s a [**link to an app**](https://v0.dev/chat/trail-api-implementation-Ipk7PqiYLXy) built off the same trail, using the Guidebook.

(video guide on this one above coming soon)

### General Herd UX Notes

- Each trail has one “chat” associated with it that can’t be changed
- ENS and Basenames are generally supported in any address fields in the UI for Explorer/Canvas/Overlook surfaces
- Herd Search works best with protocol and contract names
- For testing trails, it is recommended you publish the trail early on for now. Updating the trail in the canvas UI immediately updates the view on the overlook side.

## Contacting the Team and Community

You can [**DM me for assistance**](https://t.me/andrewhong5297) at any time. Join [**the discord**](https://discord.gg/dqxt4mqfKe) to find other trailblazers to build together with 🙂