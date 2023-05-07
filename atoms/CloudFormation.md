AWS CloudFormation enables you to use a template file to create and delete a collection of resources together as a single unit (a stack). #AWSService 

#UseCase for #CostOptimized dev environment.
- Delete templates at 5pm Friday and recreate at 8am on Monday. This is also a good way to save the environment. #Sustainable 
- Declarative programming is supported automatically.
- Leverage existing templates and also diagrams are created!
- [[SAM]] sits on top of CF.
---

#Q What are the main components of CloudFormation?
See:
**Answer**:  Resources, Parameters, Mappings, Outputs, Conditionals, Metadata. Also, References an Functions as helpers.

| Component           | Description                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------- |
| Resources           | Mandatory declaration of resources.                                                         |
| Parameters          | Dynamic inputs to the template.                                                             |
| Mappings            | Static variables for your template.                                                         |
| Outputs             | References to what was created.                                                             |
| Conditionals        | Logic                                                                                       |
| Metadata            | Include arbitrary metadata in JSON or YAML                                                  |
| References (Helper) | obtain the value of a specific attribute of a resource defined in the same or another stack |
| Functions (Helper)  | manipulate values or perform calculations based on input parameters                                                                                            |

Table. CloudFormation

---

#Q What are **Parameters**?
Answer: Parameters enable you to pass values to your templates when you create or update a stack. These values can include information such as instance sizes, key pair names, and database passwords. By using parameters, you can create more flexible and reusable templates that can be used for different environments or use cases.
`Fn::Ref` or simply `!Ref`. You don't know the value up front.

#Q What are **pseudo-parameters**?
Answer: Pseudo-parameters, on the other hand, are predefined by CloudFormation and are available for use in all stacks. They provide information about the stack and its environment. Pseudo-parameters cannot be changed and their values are automatically populated by CloudFormation during stack creation or update. Examples of pseudo-parameters include `AWS::Region`, which returns the region in which the stack is being created or updated, and `AWS::StackName`, which returns the name of the stack.

---

#Q What are **Mappings** and how do you access them ?
Answer: This is hard coded reference KV pairs. You know the values up front. Use `!FindInMap [MapName, FirstLevelKey, SecondLevelKey`

---

#Q What are **Outputs** ?
Cross stack references can be created so that experts in a company can create and maintain their portion of the cloud formation stacks. Outputs are a way to provide information about the resources that were created by the CloudFormation stack. They enable you to expose useful information about the resources that can be used by other stacks or applications.
`Fn::ImportValue` and `!ImportValue` are used to import the outputs into a cloud-formation thereby linking them.

---
#Q What are **Conditions**?
Logical controls that can execute based on logic.
![[CloudFormation Conditions.png]]

**Stacks**
- A single unit that includes all the resources build via the template.
- Nested Stacks are reused.
- Cross stacks use Output and is shared.
- Stack Sets are created by admin accounts- these are across multiple accounts and regions.
**Change Sets**
While it does not tell us if it will succeed, it will give us a summary of proposed changes that can be generated before updating a running stack. e.g. renaming a database will delete the database (and the data) - good to know. `Fn::And`, 
![[cloudformation designer.png]]
Fig. CloudFormation Designer

I find it quite impractical. JSON is unusable, YAML is readable but it's super clunky.

#Q How is CloudFormation Rolledback Handled with Notifications?
Answer: CF needs SNS Integration Enabled. If CF fails, the stack will delete and the last known successful stack.
![[Pasted image 20230501184645.png]]
Fig

---

#Q What are the limitations of CloudFormation?
Answer: It will not allow you to dynamically or programmatically generate resources. It is all declarative.  Almost all resource types are available, when they are not, you can use AWS Lambda Custom Resources.
