# REST-API to manipulate wordpress posts

<em>Install REST-client extension in vscode to send these requests</em>

https://marketplace.visualstudio.com/items?itemName=humao.rest-client

OPTIONS does not provide actual data but a detailed breakdown of all methods (GET/POST) and arguments (e.g pre_page -  maximum number of items to be returned in result set; we get maximum 10 posts; but we can change this number to something else).

OPTIONS http://dev.wordpress/wp-json/wp/v2/posts
Authorization: Basic maestro 123456

if we want the actual data from the posts resource, or the last 10 posts in this blog, we'll send a get request 
display 0 posts per_page

GET http://dev.wordpress/wp-json/wp/v2/posts?per_page=0

Create a new resource
* set up a POST request. 
* add an authorization header 
* Content-Type header (JSON data)
* encode the actual data in JSON { }
* Include title, some content, and a status. 
* The status is not technically required but if it's not set it will automatically be filled in as draft.
* For the post to be public, indicate "status": "publish"
* Author ID will automatically get attributed to the main owner of the site but can be defined, though not a requirement

POST http://dev.wordpress/wp-json/wp/v2/posts
Authorization: Basic maestro 123456
Content-Type: application/json

<code>
<pre>
{
  "title" : "Post created via a REST API",
  "content" : "This is the content of a post created via REST API",
  "status" : "publish",
  "author" : 1
}
</pre>
</code>