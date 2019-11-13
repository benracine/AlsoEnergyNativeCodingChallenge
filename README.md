![](http://www.alsoenergy.com/wp/wp-content/uploads/FullColor_BlackTag-e1413573042293.png)

# Instructions
- You will need Visual Studio to complete challenges outlined below. We suggest you utilize one of the community editions provided at https://www.visualstudio.com/downloads/
- Clone this repo to your local machine
- Use it to create a new repo on GitHub under your own account (please don't use GitHub fork to accomplish this)
- Complete any of challenges described below or provide an alternative representative sample of code or classes that is solely your work product. 
  (If you maintain a github project where you are the sole contributor, please feel free to submit a link and description of what we should review in the repository.)
- Send us an email with a link to your repo and any instructions or details you want to share about key features, performance optimizations or creative problem solving skills that they exemplify.

## Part 1. Console Application
- Assume this application will have a high load and focus should be on achieving the best performance.
- Create a console application in Visual Studio
- Create a function to sum up all the even numbers in a supplied List<int> parameter and return the result.
- Create a function that will make an http GET request to a given URL and dump out the result in Console. (Be ready to discuss what external tools you can use to validate the behavior, that your program is indeed making the request for ex: fiddler, wireshark...)  
- Create a function which will print out the numbers in a List<int> to the console in a loop with a configurable delay (print the number out every 500ms, or every 1000ms ). Make sure the function can be called from a thread. 
- Add a collection to track which thread is the first to report each number and print the results of the collection after the threads have both completed.
- In your program create 2 threads, configure your initial thread to print a number out every 500ms, configure your 2nd thread to print out numbers in reverse every 1000ms. 
- Your application should block untill all the numbers and results are printed out to the console.
  
Example output for an input int array of 1,2,3,4,5:
t1: 1
t2: 5
t1: 2
t1: 3
t2: 4
t1: 4
t1: 5
t2: 3
t2: 2
t2: 1

1: t1
2: t1
3: t1
4: t2
5: t2
  

## Part 2. Web Application
- Create a secondary application this time start a empty web application and provide a RESTful endpoint that returns the current time (including seconds) to the client when called. Use the debug web server (no need to configure IIS).
- Have your console application call the  web application you created in order to receive the current date time and print it in the console window.
- Add an optional query string parameter that can be added to your server requests to simulate an http 500 error code coming back to the client.
- Add a unit test to test the endpoint.

## Part 3. SQL
- Assume that this table will have a high load and millions of rows.
- Obtain a SQL server for your system https://www.microsoft.com/en-us/sql-server/sql-server-downloads
- Create a new database instance called ae_code_challange
- Create a new table called server_response_log.
- Add columns to the table for a logging table that will collect the following data:
  - Start time:  time when the request was sent to the server
  - End time: time when a response was received from the server (or a timeout occurred)
  - HTTP status code: response HTTP Status Code (if available)
  - Response text: Response received from the server as a string (ASCII Encoding should be fine)
  - Error code: ( 1 -> HTTP StatusCode 200 response received from the server, 2 -> Another HTTP StatusCode received from the server, -999 timeout)
- Add any necessary indexes or other performance improvements.
- Update your console application to insert a row into the server_response_log table every time a request is made to the server.
- Simulate 3 cases of responses from the server, please have these cases available in your console application for us to be able to easily run.
  - HTTP 200 with a timestamp
  - HTTP 500 no timestamp, server error
  - Timeout
 - Add a stored procedure to return the most recent 5 Response text and Start times occurring within the timespan passed into the procedure.
 - Add a view to show the count of each error code per hour and the error code.
 - Add a unit test for each simulated case, the stored procedure and the view.