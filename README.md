## Ex. 0.4

```mermaid

    sequenceDiagram
        participant Browser
        participant Server

        Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
        activate server
        Server-->>Browser: REDIRECT to https://studies.cs.helsinki.fi/exampleapp/notes
        deactivate server

        Note right of Browser: The Browser is redirected to /notes

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
        activate server
        Server-->>Browser: HTML Document
        deactivate server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
        activate server
        Server-->>Browser: CSS File
        deactivate server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
        activate server
        Server-->>Browser: JavaScript File
        deactivate server

        Note right of Browser: The Browser starts executing the js code that fetches the JSON from the server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate server
        Server-->>Browser: [{ "content": "Hey, that's a new note", "date": "2023-1-1" }, ... ]
        deactivate server

        Note right of Browser: The browser executes the callback function that renders the notes using the DOM-API

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/favico.ico
        activate server
        Server-->>Browser: HTML Document
        deactivate server

```