sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: المتصفح يبدأ بتنفيذ كود الجافا سكريبت الذي يجلب ملف الـ JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "SPA is cool", "date": "2026-3-10" }, ... ]
    deactivate server

    Note right of browser: المتصفح ينفذ الـ callback ويقوم برسم الملاحظات على الصفحة دون إعادة تحميلها
