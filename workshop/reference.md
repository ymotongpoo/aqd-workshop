### Amazon Q Developer Reference Card

**Keyboard Shortcuts**

You can control how you invoke Amazon Q Developer via the various key shortcuts, including customising these to how you work.

![keyboard shortcuts for Amazon Q Developer](/images/q-vscode-view-keyboard.png)

One of the key short cuts to know when you are working in the inline editor, is the < and > arrows. These allow you to cycle through suggestions when you are prompted by Amazon Q Developer.

**Amazon Q Commands**

* **/** - brings up all available options with Amazon Q 
* **/clear** - clears up the current conversation, resetting the context
* **/dev** - invokes Amazon Q Developer Agent for software development
* **/doc** - invokes Amazon Q Developer Agent that writes documentation for your project
* **/review** - invokes Amazon Q Developer Agent that will review the security of your project
* **/test** - invokes Amazon Q Developer Agent that generates unit tests for your functions (Python and Java)
* **/transform** - invokes Amazon Q Developer Agent for code transformation
* **@workspace** - uses files in your project workspace as additional context

**Amazon Q Logs**

There are a number of logs that are created by the Amazon Q Developer plugin:

* **Amazon Q Logs** - the main directory to review what the Amazon Q plugin is doing 

**Chat interface context Size**

You can enter 4000 characters in Amazon Q Developers chat interface.

**@workspace**

This is a beta capability, and sometimes you might find the indexing getting stuck or generating errors in the log files. To reset this you can go into settings and untick the Workspace settings, wait a moment and then re-enable it. If that fails, you can delete the cache directory that is created by the index server. The index will get automatically regenerated. To find the directory, use the Amazon Q Language Server log file.

**Amazon Q Quotas**

Refer to the Amazon Q [documentation page here](https://aws.amazon.com/q/developer/pricing/) for the very latest updates.With the professional Tier you also get additional capabilities not available with the Free Tier, so refer to the page above for more info.