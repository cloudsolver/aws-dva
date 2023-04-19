AWS CloudFormation enables you to use a template file to create and delete a collection of resources together as a single unit (a stack). #AWSService 

#UseCase for #CostOptimized dev environment.
- Delete templates at 5pm Friday and recreate at 8am on Monday. This is also a good way to save the environment. #Sustainable 
- Declarative programming is supported automatically.
- Leverage existing templates and also diagrams are created!

**Templates**
- Blueprints for building AWS resources
**Stacks**
- A single unit that includes all the resources build via the template
**Change Sets**
- Summary of proposed changes that can be generated before updating a running stack. e.g. renaming a database will delete the database (and the data) - good to know.

![[cloudformation designer.png]]
Fig. CloudFormation Designer

I find it quite impractical. JSON is unusable, YAML is readable but it's super clunky.