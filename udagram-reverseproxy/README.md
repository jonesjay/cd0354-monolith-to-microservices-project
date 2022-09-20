Reverseproxy service will assist add another layer between frontend and backend APIs so that the frontend only uses a single endpoint and doesn't realize its being deployed separaately.

The Nginx container exposes the 8080 port. In the server section, it will route localhost.com:8080/api/v0/feed requests to backend-user:8080 container.Similarly localhost.com:8080/api/v0/user requests will be routed. 

The architecture will look like this.
            |----------   AWS Cloud -----------------------------------|
            |----------------- Region ------------------------------|  |
            |                                                       |  | 
            |                                |----Backend Service 1    | 
Client------|---Frontend----ReverseProxy-----|                       
            |                                |----Backend Service 2
            |