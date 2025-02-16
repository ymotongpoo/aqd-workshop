![Amazon Q Developer header](/images/q-vscode-header.png)

### Building our application - Part Three (final)

In our final lab we are going to get our application ready for shipping. We are going to do a few things:

* Use the Amazon Q /review feature to identify any issues with our code that we need to fix
* Add documentation to our project, using a combination of /dev as well as creating a README file using the Amazon Q /doc feature

---

**Task 11**

We have some code, but how robust is it? In this lab we are going to use a feature of Amazon Q Developer to scan the project and help us shift left with security. This allows us to proactively detect and then resolve issues in our code, closing that feedback loop. Lets see how this works.

**Don't worry we are not going to spend too much time resolving the issues here, but it is important that you get a feel for how this process works**

Amazon Q Developer has another Agent called /review which will run a series of tests against your project. When you initiate a /review, Amazon Q will review your code against a number of criteria.

* SAST scanning — Detect security vulnerabilities in your source code. Amazon Q identifies various security issues, such as resource leaks, SQL injection, and cross-site scripting.
* Secrets detection — Prevent the exposure of sensitive or confidential information in your code. Amazon Q reviews your code and text files for secrets such as hardcoded passwords, database connection strings, and usernames. Secrets findings include information about the unprotected secret and how to protect it.
* IaC issues — Evaluate the security posture of your infrastructure files. Amazon Q can review your infrastructure as code (IaC) code files to detect misconfiguration, compliance, and security issues.
* Code quality issues — Ensure your code is meeting quality, maintainability, and efficiency standards. Amazon Q generates code issues related to various quality issues, including but not limited to performance, machine learning rules, and AWS best practices.
Code deployment risks — Assess risks related to deploying code. Amazon Q determines if there any risks to deploying or releasing your code, including application performance and disruption to operations.
* Software composition analysis (SCA) — Evaluate third-party code. Amazon Q examines third-party components, libraries, frameworks, and dependencies integrated into your code, ensuring third-party code is secure and up to date.


It does require that your code is version controled via git, so we are going to need to initialize this before we start.

1/ From the Terminal in VSCode, run the following command from the project directory we have been working in

> git init

This will initialise the current project in git - don't worry we are not going to do anything with it as part of this tutorial.

2/ From the chat interface, open up a new tab, and then type in **/** and from the list, select **/review** and hit return to start the review process

3/ You will see there are two options. **/review** allows you to review individual files, or your entire project. If you want to review a specific file, you need to have this open as the active file in the IDE, and then select "Review active file". If you want to review the entire project, you just select "Review workspace".

We are going to review the entire project as this is the first time we are doing a security check of our code, so select that option. You should see something similar to the following:

![Starting a /review](/images/q-vscode-review-start.png)

At the beginning of this project we created a .gitignore file. This is super important as this will control which files the security scan will select. If you do not configure this properly, it will scan all files including the ones in the virtual Python directories and provide you with lots of security details that are not relevant for your application.

It should take around 3-4 minutes for this to complete.

4/ You will notice that once complete, we now have a new section (CODE ISSUES) appear where the chat interface is. We also have a summary of the findings. This is what mine looks like, you may have similar output.

![summary of /review findings](/images/q-vscode-review-finished.png)

Take a few minutes to review the findings. Check the following

* Click on the items and see what happens - it should bring up the offending code in the main editor
* Hover over the icons next to each finding - you should see that there are a number of icons, we will explore these next
* Explore how you can organise the information - you can filter by severity or by source files, so explore those options

5/ You can configure how the CODE ISSUES list appears by dragging it and moving it above or below the CHAT window, allowing you to configure against your personal preference. Try moving it to see what works best for you.

6/ For each issue we have a number of actions we can take:

* View issue (magnifying glass)
* Ignore issue (no entry sign)
* Generate Fix (spanner)
* Explain (via the ..)
* Ignore similar issues (via the ..)

You can configure issues that you want to ignore in the Amazon Q Developer settings. This is useful if you have false positives you want to configure.

7/ Close all your open files in the IDE. Select one Critical Issue and then select the maginfying glass (View Issue) and you should see a new page appear to the left of the chat interface. It should look something like this:

![critical finding](/images/q-vscode-review-critical.png)

Click on the "Explain" button. It will open up the offending source file, and generate an explaination in the chat interface. Review the output.

8/ In the IDE, click on the "Code Issue Details" tab, and click on the "Generate Fix" button. You shoud see the page split as Amazon Q Developer looks to generate code that addresses the issues.You can click on the "Open Diff" to actually see what the suggested code changes would look like.

![review fix](/images/q-vscode-review-fix.png)

You have a number of options. If you are not happy with the suggested code, you can try again and click on the "Regenerate fix" button. If you are happy with the update, you can click on "Accept Fix". When you do this, a few things should happen.

- the code should now have the updated change automatically added for you
- the issue should now disappear from the list of issues

9/ Select a few of the High issues and go through the process - for the purpose of this tutortial we do not need to complete every fix. The important thing is to get comfortable in how this process works.

After you have completed fixing a few, close the **/reivew** tab in the chat interface. Kick off another review and see if the new findings have been addressed.

Thats it for **/review**. We now have made our code a little bit better and have more confidence in shipping it.

---

**Task 12**

Now that my project is ready for the world to see, I have decided that I am going to open source this project as I want to build a community of people who might be interested in helping me improve the code and make it better.

You can ask Amazon Q Developer to provide some guidance on what I need to do.

> **Warning!!** This guidance should be used in conjunction with conversations you have with any folk that you work with on Intelectual Property. This guidance here is only to show you how Amazon Q Developer can help you ONCE you have had those conversations and decided that open source is the way you want to go.

1/ As I think about the best way of using Amazon Q to do this, this is going to need to review all the files in the workspace. There are two ways I could approach this. Using the native Amazon Q Developer Chat interface, or by using the Amazon Q Develoepr Agent for software development (/dev). 

I do not really want to use one of my /dev quotas, so I decide that I am going to use @workspace, and this is the sample prompt I use:

> @workspace I want to open source this project using an Apache 2.0 licence. My company name is Beachgeek Enterprises so please update any copyright messages accordingly. How do I need to update this projects files?

2/ I am happy with the output it provides (see below), but I think it could be improved.

![example output of helping me open source my project](/images/q-vscode-open.png)

I follow this up with some more specific information:

> I want to include SPDX headers in the files, what do these look like

3/ You might need to do this if you have any specific requirements you need to meet that come out with conversations with your open source program office (OSPO) - if you have one.

Explore this and update your code.

---

**Task 13**

Documentation is a critical part of every application, and yet sometimes this is lacking in the code and projects we have to work with. We can use Amazon Q Developer to help us automate this task, updating both documentation in code, as well as creating README files to help others understand how to use this code. Lets create some documentation for our project.

We are going to do this using a number of techniques as I find that as you write code, they can all be used successfully as you code - no need to wait until the end. Taking a step back, as we think about how we approach documenting our project, we might want to:

* document our code (functions, imports, logic, etc) as we go along
* create higher level documentation (README, maintainance or operational, etc) at the very end once the rate of change of the application changes.

We will work from the baseline project code, so stop the application if it is currently running and then from the terminal:

*Documenting code blocks*

There are a number of ways we might approach documenting our code as we write it. We can use:

* Amazon Q inline prompts to add the documentation by selecting the block and then doing CONTROL + I and entering a prompt such as "Doucment this code block"

* Use @workspace and ask it provide documentation for our code. We might use a prompt like this - "@workspace Add doc strings to the app.py and document how the code works, providing doc strings for each function and each route"

* Use the Amazon Q menu integration, selecting a code block and then using the same prompts as above

* Use the Amazon Q Developer Agent for software development (/dev) and ask it to write the documentation for us. We might use a more specific prompt to guide it to what we want documented and the level. We need to counter that by the fact that we will be using one of our quote for /dev. You will need to weigh ypthe size and complexity of your project, against the amount of time/effort you think it might save.

1/ Open up one of the Flask files (routes or models) and then from the VSCode editor, invoke Amazon Q Developers inline prompt (either via the IDE menu integration or by using COMMAND + I). From the prompt use the following prompt:

> add doc strings 

Review what happens, and hit Enter to accept if it you are happy with the output.

2/ Open up a different file in the project (select a Flask route file), and once opened in the editor SELECT a function block. Once this function has been selected, again invoke the inline prompt and enter the following:

> add a doc string

Review the output and then hit ENTER to accept if it you are happy with the output.

You can see that you can add doc strings and document your code either at the individual functio level or across all the functions within the file you are editing.

**Creating README**

Amazon Q Developer recently introduced a new capability that allows you to quickly create README files for your projects. Now that we have completed coding of this project, it probably feels the right time to create our readme.

3/ From the Amazon Q Developer chat interface, type in / and then from the list, select /doc and then hit enter.

4/ You will see that you have two options - as we have not created a README yet, select README

---

### Congratulations!

You now have completed thie workshop, congratulations.

One final ask is to complete a survey. This will unlock some additional content, including 30 tips to help you supercharge your Amazon Q development.

[Take the survey here](https://pulse.aws/survey/1DM5TAZU)

You can return back to the [Starting Page](/README.md) to find out about additional resources that will help you stay on top of new updates and improvements with Amazon Q Developer.
