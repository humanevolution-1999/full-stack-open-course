    **Sequence diagram for adding a new note**
    _Sequence Diagram_
    participant browser 
    participant server
    
    //Note - Assuming that the user is already on the notes page 
    //Note- User enters a text and clicks on 'Save' 
    broswer->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note : [{User Text}]
    activate server
    // Note- browser adds the user text to the notes array, updates the notes JSON
    server-->>browser: redirect request to /notes
    activate browser
    
    broswer->>server : GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
  
  
  
