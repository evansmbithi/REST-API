# REST-API to manipulate wordpress posts

<em>Install Basic Authentication plugin in your wordpress website</em>

https://github.com/WP-API/Basic-Auth

<em>Install REST-client extension in vscode to send these requests</em>

https://marketplace.visualstudio.com/items?itemName=humao.rest-client

## OPTIONS
OPTIONS does not provide actual data but a detailed breakdown of all methods (GET/POST) and arguments (e.g per_page -  maximum number of items to be returned in result set; we get maximum 10 posts. but we can change this number to something else).

<pre>
  OPTIONS http://dev.wordpress/wp-json/wp/v2/posts
  Authorization: Basic maestro 123456
</pre>

## GET
if we want the actual data from the posts resource, or the last 10 posts in this blog, we'll send a get request 
display 0 posts per_page

<pre>
  GET http://dev.wordpress/wp-json/wp/v2/posts?per_page=0
</pre>

## POST
Create a new resource
* set up a POST request. 
* add an authorization header 
* Content-Type header (JSON data)
* encode the actual data in JSON { }
* Include title, some content, and a status. 
* The status is not technically required but if it's not set it will automatically be filled in as draft.
* For the post to be public, indicate "status": "publish"
* Author ID will automatically get attributed to the main owner of the site but can be defined, though not a requirement

<pre>
  <code>
    POST http://dev.wordpress/wp-json/wp/v2/posts
    Authorization: Basic maestro 123456
    Content-Type: application/json

    {
      "title" : "Post created via a REST API",
      "content" : "This is the content of a post created via REST API",
      "status" : "publish",
      "author" : 1
    }
  </code>
</pre>

## PUT
Allows one to make changes to a resource
<pre>
  PUT http://dev.wordpress/wp-json/wp/v2/posts/6
  Authorization: Basic maestro 123456
  Content-Type: application/json

  {
    "title" : "Post created (and updated) via a REST API"
  }
</pre>

## DELETE
Delete a post where id=8

<pre>
  DELETE http://dev.wordpress/wordpress/wp-json/wp/v2/posts/8
  Authorization: Basic maestro 123456
</pre>

- The DELETE method does not actually delete a resource. Rather moves it to trash "status": "trash"
- Sending the same DELETE request returns a code "rest_already_trashed"
- To completely delete the resource, the force argument has to be passed as true to bypass Trash.

<pre>
  DELETE http://dev.wordpress/wordpress/wp-json/wp/v2/posts/8?force=true
  Authorization: Basic maestro 123456
</pre>