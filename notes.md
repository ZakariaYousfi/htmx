
# Hypermedia
A hypermedia is a media, like text for example, that includes non-linear braching from one location in the media to another using, for example, Hyperlinks embedded in the media. Hypertext, HTML for example, is a hypermedia because we can jump from one location to another using an anchor tag. 

# Hypermedia Control
An element in a hypermedia that describes some interaction, with a remove server for example, by enconding information about the interaction directly and completly within itself. Hyperlinks are an example of this, and in HTML, the anchor tag < a > and the form tag < form > are both hypermedia controls.

# Difference between Hypermedia and media
Hypermedia controls is what differentiate them.

# Hypermedia System
A hypermedia system does not contain only Hypermedia, but other technologies such as: network protocols like HTTP, other media types such as images and videos, hypermedia servers that provide hypermedia APIs, hypermedia clients such as web browsers, and so on. 

# The HTML anchor tag
An HTML tag consists of the tag itself, < a > < /a >, the attributes contained within the tag ,< a href = "link" >, and the content contained inside the tag ,< a href = "link" > content < /a >. the href attribute is what makes the anchor tag a hypermedia control, as it specifies a hypertext reference to another document or fragment of a document. In using the anchor tag, we inform the user that the anchor tag content is clickable, and when clicked, it will issue and HTTP GET request to URL contained in href, and if a response was returned, take the HTML content in the body of the HTTP response and replace the entire screen in the browser with this new HTML content, while also updating the navigation bar and set it to this new URL. 
So, when a link is clicked, a hypermedia client (browser) sends an HTTP (network protocol) GET (method) request to the hypermedia server, which responds with a hypermedia response (the HTML for the new page).

# The HTML form tag
The form tag, same as the anchor tag, contains the tag itself, and the attributes and content within it. the form tag however, has the 'action' attribute instaid of href, and an attribute 'method' that let's us specify the HTTP method (POST for example, is used to modify resources (the state of resources) on the server). the form tag has inside of its content an input tag or other user input grabbing tags like the select tag. which allow to send user data by the medium of the URL parameters incase of a GET request, and by the medium of the request body in the case of a POST request. the same process mentioned earlier for the anchor tag occurs when a user clicks on the button inside the form or presses the enter key when focused on an input.

# Hypermedia-driven application
A hypermedia-driven application is an application built on top of a hypermedia system that respects and utilizes the hypermedia functionality of that underlying system. It is the form tag that makes Hypermedia-Driven Applications possible.

# Single page Applications (SPAs)
In a usual single page application, built for example using react, the anchor tag and form tag hypermedia functionality is almost never used. what is used, is api calls using the javascript fetch method, which leverages JSON to communicate with the web server, and then update the application model that exists in the memory of the browser in the from of a json object, and changes to this model can cause changes to the UI. So, these applications avoid the ever existing hypermedia architecture that exists in the browser. There are times when these applications are appropriate to use, but the other times, it is worth it to consider better alternatives and not jump straight to using these types of tick client side applications.

# Why use hypermedia?
It is an extremely simple approach to building web applications. It is extremely tolerant of content and API changes. It leverages tried and true features of web browsers, such as caching. 
The first two advantages tackle major pain points in modern web developement. the complex nature of SPA infrastructure which often require an entire team to manage, and the JSON api churn, the constant changes made to JSON APIs to support application needs. These problems led to what is called javascript fatigue. A general sense of exhaution experienced by developers with all the hoops that are necessary to jump through to get anything done in modern-day web applications.
The HTML itself didn't offer anything close to the interactivity of modern javascript application frameworks. this was the reason people shifted away from hypermedia, they should have just demanded more interactivity from HTML. which was eventually in the form of javascript that augmented HTML as a hypermedia.

# A mix of SPAs and MPA
Multiple page applications is a term given for applications that uses hypermedia. figures in the developement community argue for mixing SPAs and MPAs. SPAs when we need interactivity and MPAs when we need it not. but it turns out, rather than having an SPA with a bit of hypermedia around the edges, you can often create a web application that is primarily or entirely hypermedia-driven, and that still statisfies the interactivity that users require. This approach incredibly simplifies the application and leads to a much less complex application. It is all about adopting a hypermedia-first approach.

# HTMX
HTMX is a hypermedia-oriented library. while HTMX and the old web 1.0 approaches intersect in their usage of hypermedia as their core technology and architecture, it's not quite right to call applications using HTMX as MPAs.

# Hypermedia-driven applications (HDAs)
A web application that uses hypermedia and hypermedia exchanges as its primary mechanism for communicating with a server.

# An HTMX example
the following is an HTMX code:
< button hx-get="/contacts/1" hx-target="#contact-ui"> 
                                                Fetch Contact 
    < button />
it translates to: when this button is clicked, make a get request to /contacts/1 and if a response is sent back, replace the HTML element that has the id contact-ui with the HTML in the response. So, the reponse returned is not a JSON response like with other frameworks, but an HTML response. The button from the code earlier is exchanging hypermedia with the server, just like the anchor and form tag. HTMX added functionality to this button, so it is extending HTML as a hypermedia. In the previous code, the javascript usage wasn't explicit, but HTMX  uses javascript under the hood to extend HTML. 

# Last words on using HTMX vs reactive solutions
if there is a lot of interactivity in a website, let's say a spreadsheet application, then HTMX might not be the perfect fit, because updating a single cell can induce a lot of changes in the sheet. whoever, if the spreadsheet application has a settings page, that would not have a lot of interactivity and thus, using HTMX there would be fitting. If the page is a product page like an amazon page for example, then HTMX is fitting because most of the content is text and images, and there is no need for a lot of interactivity. It's all about the amount of interactivity versus the staticness of the page. So, it's better to use HTMX whenever it fits. A hybrid approach is always best. Why complicate things when a simple approach can do?

# Div soup
using divs as buttons is bad since clicking the tab button won't focus on it, plus there is no way for assistive tools to tell that it's a button. the workaround is to use the role attribute and set it at "button" and the tabindex attribute set at "0". This just doesn't feel right, plus at the source code level it won't be easy to spot them. This is called Div soup, falling back to div and span tags instead of using more meaningful tags.

# HTMX best practices
Use HTTP status codes the way they should be used, 200 for success, 301 for moved permanently, 302 found moved temporarily and the new url sent back in the location response header, 303 moved temporarily but must use a GET request only to retrieve it, 401 for unauthorized (user not authenticated), 403 forbidden, 404 not found, 500 internal server error. 
Use of HTTP response caching. basically, in the response, we tell the client that he shouldn't make another request for a certain period of time because our response won't change. we use the Cache-Control header in the response by including the max-age value set to a number of seconds. Another header we can use is Vary which allows us to select a bunch of headers so that we can say cache responses that contain those specific combination of headers, useful when some headers affect the form of the server response.

# HTMX is backend friendly
HTMX is backend friendly. If you use a frontend web application like react, you would feel pressured to use a javascript backend like node or deno. And if your application demands some bigData or AI in the backend, you would lean towards using python, making it harder to share code on both sides of the stack if they both used javascript. HTMX frees us from these technical considerations.

# HATEOAS: Hypermedia as the engine of Application state
Hypermedia responses to requests are html. In a typical javascript framework, the response is JSON. usually, JSON responses are very minimal, and they don't tell much, and knowledge from the frontend about the response is needed. In Hypermedia driven applications, this isn't the case, as we must return an HTML containing all the things we require (state) in a well represented HTML document. So a typical javascript framework uses the javascript model for state because the JSON response will contain key value pairs used to update the state which might be containted in an object (think redux). HTMX on the other hand has the state expressed in the HTML response. So, hypermedia is the engine of the application state. The Hypermedia client (browser) doesn't need to mess around with the response (e.g. JSON), but it just needs to represent it (HTML).





