# SpringTodo backend
A simple todo application REST API developed using Spring Boot.

## Overview
Used **Spring Data JPA** for CRUD operations on a **Postgres** database, deployed the application using **AWS Elastic Beanstalk** with EC2 and RDS.

## Features
1. CRUD operation
2. CICD with [Github Action](https://github.com/features/actions) and [Jib](https://github.com/GoogleContainerTools/jib#readme)

## Architecture Diagram
[Diagram](https://asset.cloudinary.com/yilin1234/cc4ff5421104eb7ef191133eac54663d)

## Live version
[my todolist](https://amazing-kashata-3786cd.netlify.app/)

## frontend repository
[link](https://github.com/yi-lin-1234/todolist-app)

## Challenges & Learnings

<details>
<summary>Challenge 1: Netlify only allows HTTPS, so I needed to configure HTTPS for my website.</summary>

Solution:

1. I acquired a domain from AWS Route 53, named "yilin321.com".
2. I requested an ACM SSL certificate for this domain to ensure secure HTTPS connections.
3. I configured an AWS Load Balancer to listen on port 443 (HTTPS) using my SSL-certified domain.
4. I created an A record using Route 53 to point "yilin321.com" to my Elastic Beanstalk endpoint.
5. Now, when my Netlify React app sends an Axios request to "yilin321.com", the request will be sent from "yilin321.com" to the Elastic Beanstalk Load Balancer, which will allow HTTPS connections.
6. By following these steps, I was able to configure HTTPS for my website and ensure secure connections for my users.

Useful resources:
1. [aws doc](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/configuring-https.html)
2. [stackoverflow](https://stackoverflow.com/questions/68291078/https-request-to-aws-elastic-beanstalk-returns-neterr-cert-common-name-invalid)

![IMG_51283D26D1CE-1](https://user-images.githubusercontent.com/92185695/226241597-b92a6446-9031-4b43-8f6b-1aac50810ad3.jpeg)

</details>

<details>
<summary>Challenge 2: Elastic Beanstalk Health Check Failure</summary>

Solution:

1. By default, Elastic Load Balancer (ELB) checks the root path ("/") of my application to ensure it's healthy. However, if my REST API doesn't have a "/" path, the ELB will return a 404 error and mark the instance as unhealthy.
2. To fix the health check failure, I add a "/" path to your REST API. 

Useful resources:
1. [stackoverflow post](https://stackoverflow.com/questions/50212033/awselb-health-is-failing-or-not-available-for-all-instances)

</details>
<details>
<summary>Challenge 3: react router refresh problem on netlify</summary>

Solution:

1. React Router is a popular routing library used with React that provides a way to handle navigation in a single-page application. One common issue with React Router is the problem of refreshing the page on Netlify, which can cause issues with server-side rendering and client-side rendering.

2. To handle the refresh problem on Netlify, I set up a _redirects file in your public directory with the following content:

    ```/*    /index.html   200```

3. This tells Netlify to serve the index.html file for all routes, and to return a 200 status code, which indicates success. This will ensure that when the user refreshes the page, the server will serve the index.html file, and the client-side routing will kick in as expected.

Useful resources:
1. [stackoverflow post](https://rexben.medium.com/how-to-fix-page-not-found-on-netlify-with-react-router-dom-e0520692be5)
</details>

<details>
<summary>Challenge 4: CORS error</summary>

Solution:

1. To enable CORS in a Spring Boot application, I use the @CrossOrigin annotation on my controller.

Useful resources:
1. [baeldung post](https://www.baeldung.com/spring-cors)
2. [youtube video explain CROS](https://www.youtube.com/watch?v=4KHiSt0oLJ0)
</details>

<details>
<summary>Challenge 5: git ask me to pull new change I don't have everytime when I try to push to remote github</summary>

Solution:

1. pull the change because when I github action create new commit on previous push

![IMG_EF33682E3012-1](https://user-images.githubusercontent.com/92185695/226248600-f936ee0d-f878-4639-8d9b-c006c44b6be0.jpeg)


</details>



