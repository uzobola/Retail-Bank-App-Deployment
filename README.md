# RETAIL BANKING APPLICATION

# PURPOSE

This workload presents a practical implementation of a CI/CD pipeline and the application of system design principles. The deployment of the Retail Banking App showcases the end-to-end deployment process for a web application.

# STEPS

## Step 1 - Clone this repository to your GitHub account

GitHub is the source code management tool of choice. Committing the Retail Bank application code to our SCM ensures that as collaboration happens, all changes are tracked, and versions managed appropriately. This step also facilitates integration with automation tools in our CI/CD pipeline, e.g., Jenkins.

## Step 2 - Create an EC2

The AWS EC2 instance provides the infrastructure needed to run the servers required for the application. The advantage of using cloud infrastructure, such as AWS’s EC2, is that it is scalable and enables resources to be allocated based on application requirements.

## Step 3 - Install Jenkins onto the EC2

Jenkins is a DevOps tool that automates the continuous building, testing, and deployment of applications in the CI/CD pipeline. Installing Jenkins ensures that any changes to code are continuously integrated, tested, and deployed. By automating both essential and redundant tasks, Jenkins helps to minimize human errors, improve code quality, and enable faster development and deployment of the application.

## Step 4 & 5 - Log into Jenkins and Create a Multi-Branch Pipeline

Creating an account in Jenkins is required in this step to configure the server, set up pipelines, and manage jobs required by the application. Among the four main types of pipelines, a multi-branch pipeline is the most appropriate for this multi-branched deployment project. This type automatically detects, coordinates, and manages each branch of the code according to their required specifications. This consistent and continuous management helps ensure consistent development, testing, and deployment of the application.

## Step 6 - Connect the GitHub Repository to Jenkins

To automate the build and deployment process, Jenkins needs access to the source code available on the project repository. Connecting the GitHub repository to Jenkins integrates the source code management system within the CI/CD pipeline. This connection gives Jenkins access to the project source code so that builds and tests are automatically triggered whenever changes are pushed to the repository. This again minimizes human errors and ensures that code is always in a deployable state.

## Step 7 – Creating Web Environment and Deploying the Retail Banking Application with AWS

AWS Elastic Beanstalk is a Platform as a Service (PaaS) offered by Amazon Web Services (AWS) that manages the deployment, management, and scaling of web applications and services. As a fully managed service, it facilitates the quick deployment of applications in the cloud without the need to manage the underlying infrastructure.

# ISSUES/TROUBLESHOOTING

### ISSUE #1
I got a 502 Bad Gateway error pointing to the fact that it was a server-side error.

### ISSUE #2
For some reason, I could not get the logs from the console

#### TROUBLESHOOTING STEPS
- Checked the server logs and found out from /var/log/nginx/error.log that although it was trying to listen on port 8000 nothing was running on that port.

Out of the many overkill steps I took, these are the steps that I believe were successful:
1. Installing/re-installing gunicorn (`pip install gunicorn`)
2. Starting the application with python.
3. Mapping the port 8000/starting the application with gunicorn (`gunicorn -w 4 -b 127.0.0.1:8000 application:application`)

# OPTIMIZATION

### #1 What are the benefits of using managed services for cloud infrastructure?

**Costs:** Among the many benefits of using managed services for cloud infrastructure, cost-effectiveness stands out. Managed services allow applications to scale up or scale down as needed, allowing businesses to only pay for the resources they use. This ensures that businesses do not overpay for unused resources, saving costs.

**Flexibility:** Another benefit is the flexibility managed services provide for scaling infrastructure to meet the application’s present performance needs. This is beneficial for businesses that require resources for small to large-scale applications or during periods of consistent or fluctuating demand.

**Faster time to market:** In the case of this Retail Banking app, AWS’s managed services take care of provisioning resources like the virtual machines needed to host the application, deployment, load balancing, scaling, and monitoring the application’s performance. Managing these important aspects takes out the need for manual configuration, allowing developers to save time and focus on moving the application from code creation to market-ready more quickly. This frees up valuable time and effort, enabling faster deployment and reducing the time it takes to get applications up and running.

### #2 What are some issues that a retail bank would face choosing this deployment method and how would you address/resolve them?

**Customization:** A bank might be required by business needs or industry regulations to implement specific configurations that one managed service provider might not offer.
- **Possible Solution:** Utilize multiple cloud providers or combine managed services with self-managed infrastructure where applicable.

**Data Security and Privacy:** Banks have access to sensitive customer information and are responsible for protecting it. Although managed services providers are responsible for the underlying infrastructure, businesses like banks are responsible for protecting sensitive customer data. A breach can have severe consequences. Managed services could introduce vulnerabilities if not properly secured and managed.
- **Possible Solutions:**
  - **Access Control:** Maintaining proper access control and practicing the principles of least privilege. Ensuring that employees and systems only have the minimum access necessary to perform their tasks.
  - **Data Encryption:** Another solution would be to encrypt data at rest or in motion.
  - **Disaster Recovery Plan:** Lastly, it’s not a matter of if there would be a breach but when there would be a breach. Businesses like banks should have a good disaster recovery plan in place to respond to security incidents.

### #3 - What are other disadvantages of using Elastic Beanstalk or similar managed services for deploying applications?

**Application Need:** Although using managed services has many advantages, not all applications are built equally, and not all can benefit from a one-size-fits-all approach. Applications with unique requirements might not find a perfect fit with one managed resource provider and might need to adopt a hybrid cloud strategy. This can increase complexity and might increase costs.

**Limited Control:** Some businesses that utilize managed services infrastructure might have to compromise on certain functionalities and find their limited ability to customize certain configurations a disadvantage.

