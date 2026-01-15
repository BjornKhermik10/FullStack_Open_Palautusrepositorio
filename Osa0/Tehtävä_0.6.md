sequenceDiagram
    participant browser
    participant server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    
    Note right of browser: The browser DOES NOT! execute the callback function that renders the notes, 
                          but sends the new note as a JSON-string afterwhich the new note is rendered onto
                          the existing list.
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 Created (JSON: {"message":"note created"}) [{"content": "test", "date": "2026-1-15" }, ... ]
    deactivate server

    Note right of browser: The site is not reloaded and no more GET or POST requests are made.
