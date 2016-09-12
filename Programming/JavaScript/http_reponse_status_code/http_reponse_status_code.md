## HTTP Response Status Code [Back](./../JavaScript.md)

### 1xx Infomational

This class of status code indicates a provisional(臨時的) response, consisting only of the Status-Line and optional headers, and is terminated by an empty line. Since HTTP/1.0 did not define any 1xx status codes, servers **must not** send a 1xx response to an HTTP/1.0 client except under experimental conditions.

#### 100 Continue

The Server has received the request headers and the client should proceed to send the request body (like a POST request). To have a server check the request's headers, a client must send `Expect: 100-continue` as a header in its initial request and receive a `100 Continue` status code in response before sending the body. The response `417 Expectation Failed` indicates the request should not be continued.

#### 101 Switching Protocols

The requester has asked the server to switch protocols and the server has agreed to do so.

#### 102 Processing (WebDAV)

A WebDAV request may contain many sub-requests involving **file operations**, requiring a long time to complete the request. This code indicates that the server has received and is processing the request, but no response is available yet.

### 2xx Success

This class of status codes indicates the action requested by the client was received, understood, accepted, and processed successfully.

#### 200 OK

Standard response for successful HTTP requests.

The actual response will depend on the request method used. In a GET request, the response will contain an entity corresponding to the requested resource. In a POST request, the response will contain an entity describing or containing the result of the action.

#### 201 Created

The request has been fulfilled, resulting in the creation of a new resource.

#### 202 Accepted

The request has been accepted for processing, but the processing has not been completed.

#### 203 Non-Authoritative Information (since HTTP/1.1)

The server is a transforming proxy (e.g. a Web accelerator) that received a 200 OK from its origin, but is returning a modified version of the origin's response.

#### 204 No Content

The server successfully processed the request and is not returning any content.

#### 205 Reset Content

The server successfully processed the request, but is not returning any content. Unlike a 204 response, this response requires that the requester reset the document view.

#### 206 Partial(部分) Content

The server is delivering only part of the resource (byte serving) due to a range header sent by the client. The range header is used by HTTP clients to enable resuming of interrupted downloads, or split a download into multiple simultaneous streams(同步流).

#### 207 Multi-Status(WebDAV)

The message body that follows is an XML message and can contain a number of separate response codes, depending on how many sub-requests were made.

#### 208 Already Reported(WebDAV)

The members of a DAV binding have already been enumerated in a previous reply to this request, and are not being included again.

#### 226 IM Used

The server has fulfilled a request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance. Many of them are used in **URL Redirection**.

### 3xx Redirection

This class of status code indicates the client must take additional action to complete the request.

#### 300 Multiple Choices

Indicates multiple options for the resource from which the client may choose to redirect into.

#### 301 Moved Permanently

This and all future requests should be directed to the given URI.

#### 302 Found

Indicates that the server require the client to perform a temporary redirect. 

#### 303 See Other

The response to the request can be found under another URI using a GET method. When received in response to a POST (or PUT/DELETE), the client should presume that the server has received the data and should issue a redirect with a separate GET message.

#### 304 Not Modified

Indicates that the resource has not been modified since the version specified by the request headers `If-Modified-Since` or `If-None-Match`.