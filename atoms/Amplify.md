#Q What is amplify and what are the main features?
See: 
Answer: It is a set of tools to get started with web and mobile applications (like Elastic Beanstalk). It's like Netlify or Vercel but built by AWS. The following commands are usefule`amplify init` to create an application with auth, storage, ML etc. and best practices implemented. `amplify add auth` adds authentication and authorization with [[Cognito]] and provides pre-built UI components. `amplify add api` create API and [[DynamoDB]] with local to cloud data sync. `amplify add hosting` setups up CICD, Monitoring, Custom Domains, Redirect and Custom Headers.

#Q How does it perform E2E testing?
See:
Answer: Run `preTest`, `test` and `postTest` specified in `amplify.yml`. Use Cypress testing framework that emulates the web browser. 