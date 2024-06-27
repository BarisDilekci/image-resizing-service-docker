# image-resizing-service-docker

## How it works
``` 
1- docker build -t python-app .
```
```
2- docker run --rm -i -t -p 8080:18080 python-app
```

3- New terminal: 
```
   * echo {url} | base64
```
```
4- http://localhost:8080/?urlBase64={url}=&size=150
```

- Accepts HTTP GET or POST, with two parameters:
* urlBase64: Base64 encoded URL
* size: size of a square bounding box, in pixels
Returns the resized image, or an image of the original size if size is less than the original size

## Try it out locally (see note below on dependencies)
* Get a base64 encoded version of an image URL:
  `echo -n "http://storage.googleapis.com/myBucketName/Image_Name.jpg" | base64`
* Use curl to access the service, providing that base64 encoded URL value:
  `time curl http://localhost:18080/?size=800&urlBase64=aHR0cDovL3N0b3J...bi5qcGc= > output.jpg`
