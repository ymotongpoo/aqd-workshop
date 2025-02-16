![Amazon Q Developer header](/images/q-vscode-header.png)

### Building our application - Part Two

**Overview**

In part twp of this lab we are going to take the data model that we created and start to build our application. We are going to use Amazon Q Developer Agent for software development to automate the creation of this code. Amazon Q Developer Agent for software development takes your prompt and then breaks this down into a series of tasks. As it starts to reason about those tasks, it will start to review the existing files you have in your project (in this case, our sql code) and then start writing code. Once Amazon Q has finished, it will present the final output for review, allowing you to test and review the code. At this point you can then provide feedback to adjust or accept the code as is.

This process take around 5-6 minutes, so plenty of chance for you to grab a drink or have a stretch.

---

**Task 7** 

So far we have used one modality of the AI Coding Assistant (the chat interface, and quickly looked at inline editing too). These are great but require us to do the actual writing of the code. Agents changes that, allowing you to delegate the task of creating files to them.

In this lab we are going to use Amazon Q Develoepr Agent for software development to CREATE code. As we are using the free tier (we have signed in using our Builder ID's) we have limited quota per month, so use carefully.

We want to ensure we maximise the accuracy of the code these agents create, so we are going to use some common techniques that provide additional context to help steer the AI Coding Assistant agents of Amazon Q Developer. We have kind of seen an example of this already when we setup the DBA.md file and used @workspace. 

We are going to create a **scaffold** for our project, where we will put extra context which will help Amazon Q Developer create code that we want. A scaffold is a document written in markdown where you outline the specifics of what you want the code to look like. It might be specifics such as directory structure and programming languages, or include personal preferences too such as which libraries and frameworks you want to use.

The best way to see what these look like is to create one.

1/ Close all current open files/tabs in VSCode. Close all Amazon Q chat windows.

2/ Create a new directory called **"spec"** and within this create a file called **"SPEC.md"**.

Copy the following into this file:

```
When creating new Python code, use the following guidance

- Use Flask as the web framework
- Follow Flask's application factory pattern
- Use environment variables for configuration
- Implement Flask-SQLAlchemy for database operations

Use the following project structure

├── src
├── src/static/
├── src/models/
├── src/routes/
├── src/templates/
├── src/extensions.py
├ app.py
├ requirements.txt

```

Save this file.

3/ We initiate Amazon Q Developer Agent for software development via the Amazon Q Developer chat interface.

Open up the Amazon Q Developer Chat interface, and from the prompt enter hit the / key, and from the pop up select **/dev** and hit enter. You should now copy the prompt below and then hit enter again.

```
Build a simple Customer Survey application. 

- Use the data mode in the customer-feedback.sql
- Generate a web application that can be used in a browser
- Users will need to register with an email address to login
- When Users login, a Dashboard will be displayed that provides a simple explanation of what the application does.
- From the home Dashboard, Users will be displays any available Customer Surveys that they have been created
- When Users are viewing their Customer Surveys, they will have the ability to view the results
- When Users are viewing the Dashboard, any available Customer Surveys will provide a link that can be shared so people can submit feedback on a specific survey
-  Provide a simple web design that can be updated easily using CSS
-  Review project layout details in spec.md
-  Ensure the database is initialised properly
``` 

This is what it should look ike:

![Kicking off /dev](/images/q-vscode-kickoff-dev.png)

After a few minutes, you should start to see Amazon Q Developer Agent for software development start to do its thing.

![/dev starting](/images/q-vscode-dev-starting.png)

This process is likely to take 6-10 minutes, but keep an eye on what is happening as the status of tasks will be updating in realtime, as well as it displaying what files it is using and what files it will be creating.

> **Warning!** Remember that once you fire off an invocation of /dev this will be one of your alloted attempts for the month. There is a **Stop** button, but this will only stop the current generation. This is equivilant of using the "Provide Feedback and re-generate" button.

**This is a great time to stretch your legs, grab a coffee**

4/ Once it has completed, you should see something like the following (although the files and layout you get will be different).

![/dev finished](/images/q-vscode-dev-finish-2.png)
![/dev finished](/images/q-vscode-dev-finish-1.png)


You can now click on the individual the "Code Suggestions" box. Review the code. As you begin to use these tools on a daily basis, you will need to think about a review process that works for you. This is what I am currently doing, but you should think about what works for you:

* Did the code produce what I expected? Did it follow the guiding prompt well enough?
* Do I understand the code
* Can I spot any obvious issues or omissions

This is just a few of the things I think about when reviewing the ouput. Once I have reviewed the code, there are two options:

1. If you are happy, use the feedback icon (Thumb UP or Thumb DOWN) to provide feedback before hitting the "Insert Code" button.
2. If you want the Agent to do more work, then use the "Provide feedback and regenerate"

When I have run this prompt, the output provided can go one of two ways: the first is that it generates working code, but the code only provides an API, and the second is working code that also provides a web application that you can begin using.

If I get the first, I typically select the **"Provide feedback and regenerate"** button. These are some of the prompts you might get if you got the first options (API), but you can review these and think of perhaps better ones.

* Can you provide full working code. Ensure you provide code that will create a web application that users can use via a web browser.
* Provide updated code that will allow a user to use this via a web browser
* Update the code generated so that the application can be used by a web browser. Provide sample html files and css so that I can adjust the look and feel of the application

Once you have either reviewed and are happy with the code, or provided feedback for regeneration and are then good with the output, you will hit the Accept Code and you will now find you have the start of your application. The next task is going to be running it.

---

**Task 8**

So we have some code, but code is only good if it runs. AI Coding Assistants are getting better all the time, and whilst they are still not perfect, we can use them to help troubleshoot and fix any issues we might have to get our application up and running.

1/ Making sure you still have your virtual Python environment activated (you should see the (.ven) at the start within the terminal), run the following command to install the Python dependencies

> pip install -r requirements.txxt

2/ We can now run our application by using the following command:

```
python app.py
```

With a but of luck, your application should start and you will be able to access it via a browser. Make sure you use http://127.0.0.1:5000 when accessing the local Flask application.

If your application does not work, don't worry. Welcome to the world of your trusty AI debugging assistant. Use the Amazon Q chat interface to help you. To maximise the effectiveness, do the following: 

* close all your VSCode tabs and just leave the app.py open. This helps provide Amazon Q with the right context. 
* review the error message and just select the most important part of the error to help Amazon Q focus on the right thing
* review error messages either in the terminal or in the web browser to help isolated the best error message
* sometimes you will need to add further information (context) to help Amazon Q troubleshoot the issue and give you the right information
* you will get better solutions if you are able to identify the most likely area where your code is failing - keep that file open in VSCode to provide Amazon Q Developer with context, or using @workspace if you are unsure

You can use prompts along the lines of:

* Starting the app generated << insert error >> - how do I fix
* How do I fix this error - << insert error message >>

You might also need to have follow up prompts. You might fix one issue, only to have another one. Continue to cycle through the errors using the same process. 

Don't worry,it might take you a few minutes to chase down all the errors until you are able to start the application!

3/ With our application now running, open a browser and try and register and login. Are you able to log in successfully, or do you get an error? If you are using the code in the repo, you should be ok and be able to register and login. If you are using your own code, then try registering a user and see how you get on. 

4/ After you have logged in, try creating a customer survey. Once created, complete one to make sure the application is working ok. You might notice something - whilst you can create surveys and complete them, there is no way you can currently view the results of a survey. We will fix thatin the next task.

---

**Task 9**

We often need to add new features to applications, whether these are code bases we know and understand, or not. In this lab we are going to add the ability to export survey data as a csv file.

If you have the app currently running, exit (CTRL + C) as we are going to reset back to the workshop codebase.

1/ Close all files/tabs open, and close any tabs you have open in the Amazon Q chat interface.

2/ We can now start thinking about how to export the survey data. A big part of using tools like Amazon Q Developer, is thinking about and breaking down problems BEFORE we ask for code. Sometimes you might use the Chat interface questions to help better understand your options (so not code related). For example, you might ask Amazon Q about different export data file types. This is critical to make sure that you craft the prompt that will help you achieve what you are looking to do. In this instance, having thought about it, this is what I want to do:

* I want to export data in CSV file format
* I want to provide a link on the results page to export the data
* I want to use the survey name as the export file name
* I want the option to exclude email addresses if provided from the export

Thinking about what changes we might need to make, it is likely we are going to impact multiple files. I decided that @workspace is probably going to be the best option here.

> @workspace Update the code to this application to add the ability yo export the results of a customer survey as a CSV file. The export file name should be the same as the survey. The export should only appear on the results page.
> @workspace add a new button on the feedback.html that will allow the user to export the survey data.

Review the output and follow the tasks. You might encounter a few errors and issues, typically along the lines of:

* the export code does not work due to outdated methods
* check that the export code is actually exporting the correct data from the tables
* the export code generates errors such as " TypeError: a bytes-like object is required, not 'str'" or "ValueError: Files must be opened in binary mode or use BytesIO."

After you clear the errors, you should get a download file. Whilst this is good, it is not really what we are looking for. Lets build upon this and ask a follow up prompt, making sure to keep the survey.py route open.

> Update the export code so that the export includes the name of the survey, description, as well as all the responses

Update the code and do another export. Almost there, one final update

> Update the export code so that the export includes the name of the survey, description, as well as all the responses. Use one line per survey response.

Review the code and then follow the instructions. Try exporting again, and this time the export might look more useful.


> **Hint!** Sometimes Amazon Q can get the table fields mixed up, so check these are right.

3/ What if we wanted to provide an JSON response instead of just exporting a CSV file? Lets see how easy this is using Amazon Q.

Close all tabs/files, except the survey route. At the bottom of the page, use the Amazon Q inline prompt (COMMAND + I ) and enter the following:

> add a new route to export the survey data in json format, including all the survey details and responses

Review the output and make changes. This is the code it produced when I ran this:

---

**Task 10**

We have a solid working application, but there are still things to be done. In this lab we will add an about page that explains how to use this application.To make it a bit more interesting, we will add a fun capability to displays some Yoda wisdoms. 

As we have mentioned previously, context is everything. To make sure that AI Coding Assistants provide us with the best guidance, we need to make sure we provide them with good context. 

1/ Close all the open files/tabs, and open up the main route file (probably called routes/main.py) and from a new chat tab in the Amazon Q chat interface ask the following prompt:

> @workspace Add a new route for an About page that will be used to provide information to the end users

Review and follow the instructions. After making the changes you should now see a new navigation item on your application.

2/ Close all open tabs and open up the main route file again (which you just added the about route to). Move your cursor above the existing routes. We are going to use the inline prompt to add a new function. This function will return a wisdom of the day from master Yoda. 

After pressing COMMAND + I, enter the following:

> create a function that creates a number of messages from Jedi Yoda, and returns a random one

This is the code that Amazon Q generated for me, it should look broadly similar to yours.

```
import random

def get_yoda_message():
    yoda_quotes = [
        "Do or do not, there is no try.",
        "Size matters not. Look at me. Judge me by my size, do you?",
        "Fear is the path to the dark side.",
        "Wars not make one great.",
        "Luminous beings are we, not this crude matter.",
        "Always pass on what you have learned.",
        "Patience you must have, my young Padawan.",
        "In a dark place we find ourselves, and a little more knowledge lights our way.",
        "When nine hundred years old you reach, look as good you will not.",
        "Difficult to see. Always in motion is the future."
    ]
    return random.choice(yoda_quotes)
```

3/ Now select the about route that we just created (highlight the entire block) and using the COMMAND + I inline prompt, enter the following (change this if the page you created in 1/ was named differently)

> update this route so that it passess a yoda_quote to the about.html page

It should be a simple change that it makes. Review and accept the change. This has only changed the route, we still need to make the corresponding change to the about page.

4/ Open up the about.html page, select all the code and again use COMMAND + I, this time using the prompt:

> update this html so that it displays a "Yoda Message of the day" using the yoda_quote=yoda_quote data passed into this file

After saving the changes, check out the about.html page.

---

**Complete:** You now have a working application, made some improvements and optimisations, now we are ready for the last few tasks we need to do as a developer. Proceed to the final lab, [Part Three](building-our-app-part-3.md)





