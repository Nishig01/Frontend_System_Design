# Communication
## Overview
Communication Techniques
1. Short Polling - where you are continuously asking server if its ready
2. Long Polling - data once fully prepared you will get data
3. Web Sockets - you want to request in between you can give it, and whatever is ready from server is given to you
4. Server side events - you didn't wanted something still you will get the extra data.
5. Web hooks - after client is done it asks server to send data.
Reference:https://medium.com/must-know-computer-science/system-design-client-server-communication-674818ca448d
### ** Short Polling**
Key attributes: 
- Short Live Connection
- No Persistent connection
- Less resource utility
- Problem with scale
Examples: Real time system, Notification, Analysis
![](https://media2.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fe5j0yhr4nqvg6zb7wygr.png)
Reference:https://dev.to/simranjit884/understanding-short-polling-a-simple-approach-to-client-server-communication-3ldm

* Server-Side (Node.js with Express)
First, set up a simple Express server that responds to client requests.

`// server.js
const express = require('express');
const app = express();
const port = 3000;

let data = { message: "Hello, World!" };

app.get('/poll', (req, res) => {
    res.json(data);
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
* Client Side
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Short Polling Example</title>
</head>
<body>
    <h1>Short Polling Example</h1>
    <div id="data"></div>

    <script>
        function fetchData() {
            fetch('http://localhost:3000/poll')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('data').innerText = data.message;
                })
                .catch(error => console.error('Error fetching data:', error));
        }

        // Poll the server every 5 seconds
        setInterval(fetchData, 5000);

        // Initial fetch
        fetchData();
    </script>
</body>
</html>`

https://medium.com/@anoopnayak1/exploring-real-time-communication-in-web-development-short-polling-vs-long-polling-ec571f5e8af8
https://medium.com/@primedruk312/short-polling-vs-long-polling-1bfae9165cec
![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*b3T7Z5GonDo__72j2OUDmQ.png)

Real-Time Stock Data Updates with WebSockets ![](https://dz2cdn1.dzone.com/storage/temp/15389446-1637610523913.png)

### **Long Polling**
![](https://www.karanpratapsingh.com/_next/image?url=%2Fstatic%2Fcourses%2Fsystem-design%2Fchapter-III%2Flong-polling-websockets-server-sent-events%2Flong-polling.png&w=3840&q=75)

### **Web Sockets**
![](https://www.karanpratapsingh.com/_next/image?url=%2Fstatic%2Fcourses%2Fsystem-design%2Fchapter-III%2Flong-polling-websockets-server-sent-events%2Fwebsockets.png&w=3840&q=75)

### **Server Sent Events**
![](https://www.karanpratapsingh.com/_next/image?url=%2Fstatic%2Fcourses%2Fsystem-design%2Fchapter-III%2Flong-polling-websockets-server-sent-events%2Fserver-sent-events.png&w=3840&q=75)
-Long live unidirectional communication
-Single HTTP connection

**Uses**: Feeds, Notifications, Monitoring dashboard

**Challenges: **
-Browser Compatibility
-Connection Limit
-Connection Timeout
-Background tab behavior
-Resource utilisation
-Load balancer
-Sticky connection
-Proxy/firewall
-Testing
-Broadcasting

https://www.karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events

### **WEB hooks**
* -Real time communication
* -Event driven
* -POST REST API(payload, in authorisation secret key is present) is used
* -Retry
* -Verification/Acknowledge

**Usecases**:
-Notification System.
-Data Synchronisation.
-Automation. (CI/CD pipeline)

![](https://miro.medium.com/v2/resize:fit:635/1*9UWFkbauaRonzmdhxFkSGg.jpeg)
