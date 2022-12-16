### Receiving error page when navigating to routes other than default
- need to setup custom error response in cloudfront (Error Pages):
HTTP Error Code: 403
Response Page Path: /index.html
HTTP Response Code: 200

HTTP Error Code: 404
Response Page Path: /index.html
HTTP Response Code: 200

https://stackoverflow.com/questions/54611652/angular-routing-is-not-working-with-cloudfront-and-s3
https://i.stack.imgur.com/E5atj.png