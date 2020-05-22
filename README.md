# aws-lambda
AWS Lambda Presentation

https://iralitv.github.io/aws-lambda-presentation/#/

Youtube video:

https://youtu.be/5Sdzkr-4jDI

## Script

* ####Slide 0
AWS Lambda (or Lambda for short) is a serverless computing service provided by AWS.

* ####Slide 1.1
To understand what AWS Lambda is, we have to first understand what serverless architecture is all about. Serverless applications in general are applications that don’t require any provisioning of servers for them to run. When you run a serverless application, you get the benefit of not worrying about OS setup, patching, or scaling of servers that you would have to consider when you run your application on a physical server.
* ####Slide 1.2
Serverless applications or platforms have four characteristics:
•	No server management
•	Flexible scaling
•	No idle capacity
•	High availability

* ####Slide 2.1
AWS Lambda is used only for the compute layer of a serverless application. The purpose of AWS Lambda is to build event-driven applications that can be triggered by several events in AWS.
* ####Slide 2.2
In the case where you have multiple events, Lambda simply spins up multiple copies of the function to handle the events. In other words, Lambda can be described as a type of function as a service (FaaS).
* ####Slide 2.3
Supported languages are Node.js, Java, Ruby and etc.

* ####Slide 3.1
Three components comprise AWS Lambda:
•	A function. This is the actual code that performs the task.
•	A configuration. This specifies how your function is executed.
•	An event source (optional). This is the event that triggers the function. You can trigger with several AWS services or a third-party service. 

So let’s go to practice!
It was a very basic function, that generate some random number between two given numbers so let’s get going. 

###Screen
Okay so here I’m in AWS log console and we gonna go to compute section. And we gonna click by Lambda to create the first function. So we gonna click Create Function
and now we goona choose the option of creating our function. You can start from simple hello word function or use a blueprint where you can build app from sample code and configuration present. Also you can work with your serverless repo.
I gonna pick blueprint and choose some basic code for our example. Just a simple hello world with nodejs.
We choose this card and click Configure

We choose new role for this function and we gonna give its name generation-lambda-role and we gonna give her some basic permissions. This is enough permissions for this code.

We scroll down and see section with Lambda function code. You can see a runtime with Node.js 12.x, it’s the latest version supported by lambda.
There is the default snippet of code. 

--------------------------

* ####Slide 3.2
exports.handler =  async (event, context) => {
  console.log("EVENT: \n" + JSON.stringify(event, null, 2))
  return context.logStreamName
}

The runtime passes three arguments to the handler method. The first argument is the event object, which contains information from the invoker. The invoker passes this information as a JSON-formatted string when it calls Invoke, and the runtime converts it to an object. When an AWS service invokes your function, the event structure varies by service.

The second argument is the context object, which contains information about the invocation, function, and execution environment. In the preceding example, the function gets the name of the log stream from the context object and returns it to the invoker.

The third argument, callback, is a function that you can call in non-async handlers to send a response. The callback function takes two arguments: an Error and a response. When you call it, Lambda waits for the event loop to be empty and then returns the response or error to the invoker. The response object must be compatible with JSON.stringify.

For async handlers, you return a response, error, or promise to the runtime instead of using callback.

--------------------------

It’s disable to change code right now, but after creating function we’ll can update our code.
So I click on Create function.

Now we are seeing the note about successfully creating our function. And some hit about invoking your function with a test event, we should choose "Test".
So I am not going to set triggers right now we just gonna write the code and setup the function. So here I gonna skip it.
Click Code entry type
There are three ways we can run code with lambda.
The first way is to added your code in your online editor, so this is fun for small snippet of code. You can also upload a zip file and you can upload you file from Amazon S3. So because it is a very small function, I am just gonna take to this codewith online editor.

And next so I am going to name my function and we gonna call it random-number-generator. it lead a description. So run time is node.js we choose itt in previous step.

Okey this handler. It is file name: index.js and handler is the variable that you attached to exports.

So we gonna just delete all this code that amazon gave us.
So the first think that I gonna do is  define a minimal number as zero and the max number 10. And generator numbers. So I define a new variable call generated number  and we gonna use math.floor for rounding, math.random for generate number between zero and one. So we multiple number from math random function by subtraction between max and min number. In the end add min number. 
Now we gonna to return generated number. 

Next thing that you see is Advanced settings each function is run inside in container and that container has the memory are lockated. It is very basic function so we leave the default values 128 MB. So watch out this is timeout if your function doesn’t finish within this time period, Amazon will just kill it and return error message. So you gonna pick this parameter carefully. 
Click Save.
And all we have is congratulation about successful update of our function.
So here a dashboard with all our function. Code, configuration, triggers, monitoring.lets go back to the code. Test this actually code. 
Click test and create our test suit with name generationNumber, then click create. So we can see what has returned number 4 we can see log out put and we can see summary and we can see long the function duration, how match we were build, how much memory we are arelocated and how many memory we so actually used for this function.
So we can click test another time and we get number 6.

* ####Slide 4
And the last thing is pricing of lambda function. Monthly you have 1M requests and 3M seconds of compute time for free. Cool!
* ####Slide 5
So thanks for attention! Bye!


