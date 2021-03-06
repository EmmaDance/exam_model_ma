# exam_model_ma

Exam Model Mobile Applications

Given a server with the following API:

- http GET /books
  - Return a list of books. Each book has an id, title and a creation date.
  - The server will obey the If-Modified-Since http headers and will return 304 - Not Modified if the values were already returned or 200 - Ok with the latest content.
  - With the latest content the server will also set the Last-Modified header to be used on next calls.
- http POST /book
  - Used to create a new book, all the properties will be submitted in the message body.
  - On success the server will return 201 - Created or 400 - Bad Request on errors.
- ws
  - The server will also provide a websocket connection to be used to retrieve notifications.
  - Each time the server will receive a new book it will push the new content to all connected ws clients.

We should develop a client app with the following requirements:

- The app will display the list of books received from the server.
- While online the list of books will be retrieved using the /books api call.
- The user will be allowed to add new books, using /book api calls.
- When offline the app should not allow the user to create new books and shall display the local persisted data.
- While performing server call a progress indicator will be displayed.
- To synchronize the device content either a 10 second polling calls should be used or the client should connect using websokets to receive the updates. 
- On all user actions and server calls we should see add a trace in logs. 
- When leaving the app all pending calls should be canceled.
