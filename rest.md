# REST

 * To create a rest resource annotate the class with ```@RestResource(urlMapping='/Accounts/*```
 * The base URL is https://instance.salesforce.com/services/apexrest/ and the rest of the mapping is appended to that.
 * Class must be **global** and the methods must be **global static**
 * The ```@HttpGet``` or ```@HttpPost``` annotations need to be used on the methods
 * Use the following to get the compelete URL of the request 

```java
RestRequest req = RestContext.request;
String merchId = req.requestURI.substring(req.requestURI.lastIndexOf('/') + 1);
```

In the above example we are splitting the URL and taking the last index


 * The workbench can be used to test REST APIs
 * In the case of HTTP POST arguments passed to the method are automatically deserialized
 
 ```java
 @HttpPost
 global static String createMerchandise(String name,
 	String description, Decimal price, Double inventory) {
 	Merchandise__c m = new Merchandise__c(
		Name=name,
		Description__c=description,
 		Price__c=price,
 		Total_Inventory__c=inventory);
	insert m;
 	return m.Id;
 }

 ```
 The input to this is
 ```json
{
  "name" : "Eraser",
  "description" : "White eraser",
  "price" : 0.75,
  "inventory" : 1000
}
 ```
 
 ## Simple Apex Rest Callout
 
 ```java
 public class HttpCalloutSample {

  // Pass in the endpoint to be used using the string url
  public String getCalloutResponseContents(String url) {

    // Instantiate a new http object
    Http h = new Http();

     // Instantiate a new HTTP request, specify the method (GET) as well as the endpoint
    HttpRequest req = new HttpRequest();
    req.setEndpoint(url);
    req.setMethod('GET');

    // Send the request, and return a response
    HttpResponse res = h.send(req);
    return res.getBody();
  }
}
 ```
