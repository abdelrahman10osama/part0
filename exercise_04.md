sequenceDiagram
    participant browser
    participant server

    Note right of browser: المستخدم يكتب ملاحظة ويضغط على زر Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: الخادم يستلم البيانات، يحفظها في قاعدة البيانات
    server-->>browser: HTTP status code 302 (URL redirect to /notes)
    deactivate server

    Note right of browser: المتصفح يعيد تحميل صفحة الملاحظات بناءً على أمر الخادم

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

    Note right of browser: المتصفح يبدأ بتنفيذ كود الجافا سكريبت لجلب البيانات المحدثة

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "ملاحظتك الجديدة", "date": "2026-3-10" }, ... ]
    deactivate server

    Note right of browser: المتصفح ينفذ الـ callback function ويعرض القائمة الجديدة للملاحظات
