# Diagrama de nota
* Crea un diagrama similar que describa la situación en la que el usuario crea una nueva nota en la página https://studies.cs.helsinki.fi/exampleapp/notes escribiendo algo en el campo de texto y haciendo clic en el botón Save."


## Solución:

```mermaid
sequenceDiagram

    participant browser
    participant server
Note right of browser:send note to servidor

browser->>server:POST https://studies.cs.helsinki.fi/exampleapp/new_notes
    activate server
    server-->>browser:redirects to /exampleapp/notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
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
    server-->>browser: [{ "content": "solicitud http", "date": "Wed, 25 Sep 2024" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

```

## Explicación:
* El navegador realiza solicitud http post, para enviar la nota que creo el usuario al servidor.
* El servidor recibe los datos y nos da una respuesta. Redirigiendo a exampleapp/note.
* El navegador solicita el archivo html.
* El navegador solicita el archivo css.
* El navegador solicita el archivo js.
* El navegador solicita el JSON.
```
- [https://studies.cs.helsinki.fi/exampleapp/new_note](https://studies.cs.helsinki.fi/exampleapp/new_note)
- [https://studies.cs.helsinki.fi/exampleapp/notes](https://studies.cs.helsinki.fi/exampleapp/notes)
- [https://studies.cs.helsinki.fi/exampleapp/main.css](https://studies.cs.helsinki.fi/exampleapp/main.css)
- [https://studies.cs.helsinki.fi/exampleapp/main.js](https://studies.cs.helsinki.fi/exampleapp/main.js)
- [https://studies.cs.helsinki.fi/exampleapp/data.json](https://studies.cs.helsinki.fi/exampleapp/data.json)
```
