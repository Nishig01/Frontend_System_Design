See Wiki to learn Frontend System Design
| Topic                      | Description                                | Status         |
| -------------------------- | ------------------------------------------ | -------------- |
| 🌐 Frontend Architecture   | Monolithic vs Micro-frontend, SPA patterns | 📝 In Progress |
| ⚡ Performance Optimization | Core Web Vitals, Lazy Loading, Caching     | 📝 Planned     |
| 📱 Responsive Design       | Mobile-first, CSS Grid, Flexbox            | 📝 Planned     |
| 🔄 State Management        | Redux, Zustand, Context API                | 📝 Planned     |
| ⚙️ Build Tools             | Vite, Webpack, esbuild                     | 📝 Planned     |
| 🛡️ Security               | XSS, CSRF, CORS, Helmet                    | 📝 Planned     |
| 📊 Monitoring              | Error Tracking, Performance Analytics      | 📝 Planned     |


# **Networks**

# How web works - 
* Request Response on the web application. Response tab has HTML which has JS, CSS files included ![alt](https://miro.medium.com/1*com05M0CL8Xev6v_P5ELZA.jpeg)
* There are many servers how to identify-IP address
* Domain name -> 

![alt](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTUZNSvQ4645NZAm1JtpWVwhhPC8D3ovCRzSw&s) 
* Cell Tower- IPS(internet provider service)<-> DNS(domain name system) & IPS(internet provider service)->Server-database->ISP->Router-> wireless/ optical fiber-> Laptop

So, we have multiple routers -wireless and wired connections

![alt](https://media.licdn.com/dms/image/v2/D4D12AQFPnjQSoMGFnQ/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1720309560745?e=1771459200&v=beta&t=PX8v1IhFWCKWhD40PJiLTE2YClFrX8iTrGCe2PbuYUI)
![alt](https://www.baeldung.com/wp-content/uploads/sites/4/2020/08/Domain-Namespace_v1-1024x727-1.png)
* Optical fibres across globe
![alt](https://www.rcrwireless.com/wp-content/uploads/2016/01/Screen-Shot-2016-01-13-at-2.00.42-PM.png)
* How ISP architecture works 
![alt](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*JdqUAqez8jnoDlfY0p-0ow.png)
[Internet](https://medium.com/@thk1106/%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-%E7%B6%B2%E9%9A%9B%E7%B6%B2%E8%B7%AF-618c36f589a1)
Global ISP -Regional ISP -Local ISP
when you are running something on browser-->(check if caches has stored domain and IP address mappingg stored)
Caching check is done at 
* Browser(cache,service worker)
* Operating
* Router
* ISP
Example -https://glitch.com/~service-worker-stale-while-revalidate Go to network tab and check there are some of the cached data from service worker. [text](https://jcs.wtf/service-worker-stale-while-revalidate/)

1.Peering which google uses skips the part of going through different stages. In this from google data sent directly to the user. 
2.Netfllix rents space from ISP keep its data there to communicate directly to the user instead of going through multiple routes in order to stream the data.

DNS 
where every detail of every company stored-->https://shop.whois.com/domain-registration/index.php

Server->
TCP -checks if the server is available
server sends back syn+acknowledgement
![alt](https://mintcdn.com/checkly-422f444a/6qveEuGHBRjnnvr2/images/learn/images/tcp_tls_handshake.png?fit=max&auto=format&n=6qveEuGHBRjnnvr2&q=85&s=9e94e3318adad876352f053260711afc)
##How websites works-->
1. Initially a DNS request is made where we get to know the IP address.
2. We do TCP handshake to check if server is available.
3. SSL handshake. urls with https:// do extra handshake known as SSL handshake for security purposes to encrypt data we are exchanging..
4. HTTP GET Requests are done.
Try to reduce the first minimum data to 14kb to perceive fast rendering to user.
![alt](https://i-blog.csdnimg.cn/blog_migrate/d4cac98a68c9e66e3a61285744ed33f2.png)
* The exchange of certificate happens at SSL and ClientKey is used for encryption of data.
![alt](https://i-blog.csdnimg.cn/blog_migrate/a981dc47de42cca6cb1edb79fbdac947.png)
* How your web page renders? How is the HTML, CSS, JS rendered when received from server.
* Parse HTML to construct the DOM(1. [parsing](https://medium.com/get-started/topics?redirectTo=https%3A%2F%2Fmedium.com%2Fa-layman%2Fhow-browser-works-when-rendering-a-web-page-f49c09bec475%3Fsource%3D--------------------------------------------%26skipOnboarding%3D1#3074))
* Fetch CSS and JS resources (The rendering will be blocked until the JS downloading is completed)
* Parse CSS and build the CSSOM tree (2. [style calculation](https://medium.com/get-started/topics?redirectTo=https%3A%2F%2Fmedium.com%2Fa-layman%2Fhow-browser-works-when-rendering-a-web-page-f49c09bec475%3Fsource%3D--------------------------------------------%26skipOnboarding%3D1#95eb)) 
* Execute JS
* Merge DOM and CSSOM into the Render tree
* Build the layout tree (3. [layout](https://medium.com/get-started/topics?redirectTo=https%3A%2F%2Fmedium.com%2Fa-layman%2Fhow-browser-works-when-rendering-a-web-page-f49c09bec475%3Fsource%3D--------------------------------------------%26skipOnboarding%3D1#f51d))
* Build the paint tree (4. [paint](https://medium.com/get-started/topics?redirectTo=https%3A%2F%2Fmedium.com%2Fa-layman%2Fhow-browser-works-when-rendering-a-web-page-f49c09bec475%3Fsource%3D--------------------------------------------%26skipOnboarding%3D1#fc2e))
* Turn layers information into pixels on the screen (5. c[ompositing](https://medium.com/get-started/topics?redirectTo=https%3A%2F%2Fmedium.com%2Fa-layman%2Fhow-browser-works-when-rendering-a-web-page-f49c09bec475%3Fsource%3D--------------------------------------------%26skipOnboarding%3D1#84f9))
https://medium.com/a-layman/how-browser-works-when-rendering-a-web-page-f49c09bec475
![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*M2PbmrQLfnY39hYpp_0z2w.png)
![DOM CSSOM Render tree](https://web.dev/static/articles/critical-rendering-path/render-tree-construction/image/dom-cssom-are-combined-8de5805b2061e.png)
[how modern browser works](https://addyo.substack.com/p/how-modern-browsers-work)
![alt](https://miro.medium.com/v2/resize:fit:2000/1*GuWInZljjvtDpdeT6O0emA.png)
![alt](https://substackcdn.com/image/fetch/$s_!x62F!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F37778d69-97f7-432e-8028-39675d784a6f_1600x1116.png)
* Parsiing is a blocking task. it blocks all tasks.
Parse of the HTML-> HTML converted to DOM nodes, anywhere external resources css, js seen those are brought.
[text](https://cdroma.me/eng/how-the-browser-renders-a-web-page/)
![alt](https://cloud.cdroma.me/upload/2900d46cf4572086bb3a71a2004f4bc81603967819483.png)
![alt](https://cloud.cdroma.me/upload/de89cbe7244a704261ec4bd7d8a5bd131603969108205.png)
![alt](https://cloud.cdroma.me/upload/e40b18af0d79d7d86179c457aa28005a1603970058277.jpeg)
![alt](https://cloud.cdroma.me/upload/89913c1fdfbfb97c923543839a4ebe9c1603970486086.png)
![alt](https://cloud.cdroma.me/upload/1211290eccd89fc9d039a0787e5628bd1603970868819.png)
![alt](https://cloud.cdroma.me/upload/92b92971efe1e76b06f45518935c281f1603971427741.png)
* Popups, layouts, flyers last step

# Communication Protocols
HTTP - (Web browsing)
TCP Connection -the initial communication (are you available)
HTTP REQ
HTTP RES

HTTP/3 - (Header Compression, Faster, Improved Performance, Better network Congestion) (IOT)
(QUIC)
UDP connection is established

HTTPS - (Web browsing)
TCP Connection
public key
session key
encrypted data

WebSocket - once http connection is done it upgrades to web socket (for live chat)
HTTP Upgrade
Full Duplex

TCP - ensures no packet is dropped while communication. we can consider this as path
This happens in 3 stages
SYN - are you available
SYN+ACK
ACK

UDP - doesn't guarantee package transfer (it may get drop). Its fast.
Req
Res

SMTP - (email)
sender ->SMTP Server -> receiver

FTP - (uploading docs)
Control Channel
Data Channel

![](https://i.ytimg.com/vi/P6SZLcGE4us/hqdefault.jpg)

![](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6f9e43fa-84d5-4875-817c-c2e1af75d16e_1280x1664.gif)
1. HTTP (HyperText Transfer Protocol)
HTTP is a protocol for fetching resources such as HTML documents. It is the foundation of any data exchange on the Web and it is a client-server protocol.
2. HTTP/3
HTTP/3 is the next major revision of the HTTP. It runs on QUIC, a new transport protocol designed for mobile-heavy internet usage. It relies on UDP instead of TCP, which enables faster web page responsiveness. VR applications demand more bandwidth to render intricate details of a virtual scene and will likely benefit from migrating to HTTP/3 powered by QUIC.
3.HTTPS (HyperText Transfer Protocol Secure)
HTTPS extends HTTP and uses encryption for secure communications.
4. WebSocket
 WebSocket is a protocol that provides full-duplex communications over TCP. Clients establish WebSockets to receive real-time updates from the back-end services. Unlike REST, which always “pulls” data, WebSocket enables data to be “pushed”. Applications, like online gaming, stock trading, and messaging apps leverage WebSocket for real-time communication.
5. TCP (Transmission Control Protocol)
 TCP is is designed to send packets across the internet and ensure the successful delivery of data and messages over networks. Many application-layer protocols build on top of TCP.
6. UDP (User Datagram Protocol)
 UDP sends packets directly to a target computer, without establishing a connection first. UDP is commonly used in time-sensitive communications where occasionally dropping packets is better than waiting. Voice and video traffic are often sent using this protocol.
7.SMTP (Simple Mail Transfer Protocol)
SMTP is a standard protocol to transfer electronic mail from one user to another.
8.FTP (File Transfer Protocol)
FTP is used to transfer computer files between client and server. It has separate connections for the control channel and data channel. Reference:https://medium.com/must-know-computer-science/system-design-client-server-communication-674818ca448d

Rest APIs
Overview 
HTTP Req/Res with Headers
HTTP Methods
HTTP Status Codes
Best Practices + Examples
