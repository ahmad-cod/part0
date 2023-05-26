```mermaid

    sequenceDiagram
        participant B as Browser
        participant S as Server

        B->>+S: POST https://studies.cs.helsinki.fi/exampleapp/new_note
        activate server
        S-->>B: REDIRECT to https://studies.cs.helsinki.fi/exampleapp/notes
        deactivate server

        Note right of B: The Browser is redirected to /notes

        B->>S: GET https://studies.cs.helsinki.fi/exampleapp/notes
        activate server
        S-->>B: HTML Document
        deactivate server

        B->>S: GET https://studies.cs.helsinki.fi/exampleapp/main.css
        activate server
        S-->>B: CSS File
        deactivate server

        B->>S: GET https://studies.cs.helsinki.fi/exampleapp/main.js
        activate server
        S-->>B: JavaScript File
        deactivate server

        Note right of B: The Browser starts executing the js code that fetches the JSON from the server

        B->>S: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate server
        S-->>B: [{ "content": "Hey, that's a new note", "date": "2023-1-1" }, ... ]
        deactivate server

        Note right of browser: The browser executes the callback function that renders the notes using the DOM-API

        B->>S: GET https://studies.cs.helsinki.fi/exampleapp/favico.ico
        activate server
        S-->>B: HTML Document
        deactivate server

```