### MLOps Project: Phishing Data Detection with Network Security

#### Project Structure

<img src="./Project-structure.png" alt="Project Structure" width="800" height="300">

#### Data Ingestion

<img src="./Data_ingestion.png" alt="Data Ingestion" width="800" height="300">

#### Data Validation

<img src="./data-validation.png" alt="Data Validation" width="800" height="300">

#### Data Transformation

<img src="./data-transformation.png" alt="Data Transformation" width="800" height="300">


#### Train Model

<img src="./train-model.png" alt="Train Model" width="800" height="300">


---

### Steps to Set Up and Connect to a Free MongoDB Cluster

1. **Create a Free Cluster**:
    - Log in to your MongoDB Atlas account and click on the option to create a free cluster.

2. **Choose Cluster Configuration and Deploy**:
    - Follow the steps to configure your cluster (e.g., cloud provider, region, etc.).
    - Click Create to begin the deployment process.

3. **Connect to the Cluster**:
    - Once the deployment is complete, click on Connect.
    - Select the option *Connect with MongoDB Driver* and click Next.
    - Copy the connection string or the full code sample provided.

4. **Set Up User Credentials**:
    - Navigate to the *Security* section in the MongoDB Atlas dashboard.
    - Click on *Quick Start* and create a user by specifying a username and password for the connection.

5. **Use the Connection String**:
    - Replace the `<username>` and `<password>` placeholders in the connection string with the credentials you created.
    - Update the `<your-cluster-url>` with the specific cluster URL provided in the connection string.

6. **Configure Network Access**:
    - **Access Network Settings**:
        - Go to the *Network Access* section in your MongoDB Atlas dashboard.
    - **Add IP Access**:
        - Click on *Add IP Address*.
    - **Allow Access from Anywhere**:
        - In the IP access list entry, select the option to *Allow access from anywhere*, or manually enter the IP address range `0.0.0.0/0`.
    - **Confirm the Changes**:
        - Click *Confirm* to save your settings.

### Steps Connect to DagsHub for model Evaluation


### Connect to DagsHub for model Evaluation

Here are the steps to connect your project from your Git repository to DagsHub:

Step 1: Log in to DagsHub

Go to https://dagshub.com and log in to your account. If you don't have an account, create one by clicking on "Sign up".

Step 2: Create a new repository on DagsHub

Click on the "New Repository" button and select the option to connect to a Git repository. This will create a new repository on DagsHub that is linked to your existing Git repository.

Step 3: Link your Git repository to DagsHub

Follow the prompts to link your Git repository to DagsHub. This will allow you to synchronize your code changes between the two platforms.

Step 4: Configure DagsHub settings

On the page of your DagsHub repository, click on the "Remote" tab at the top of the page. Then, click on "Experiments" and copy the MLflow tracking remote URL.

Next, click on "Data" and select DVC. You can copy your access token from this page.

Step 5: connection to mlflow

To connect to MLflow, you will need to fill in the following information :

>import dagshub
>dagshub.init(repo_owner='username', repo_name='repo_name', mlflow=True)


Step 6: Model Evaluation
After running your code, follow these steps to evaluate your model:

Evaluate Model Performance

1. Go to your project on DagsHub.
2. Click on the "Experiments" tab.
3. You will see information related to model evaluation, including metrics and performance metrics.
4. To see more detailed information, click on the "Go to MLflow UI" button.
5. This will take you to the MLflow UI, where you can view more detailed information about your model's performance, including:

    - Model metrics (e.g. accuracy, precision, recall)
    - Model parameters
    - Model artifacts (e.g. model weights, biases)
    - Experiment history (e.g. previous runs, hyperparameter tuning)

By following these steps, you can evaluate the performance of your model and gain insights into how to improve it.

### Steps: Use FastAPI to Train

After running the command:

> uvicorn app:app --reload

You will get the following output:
Uvicorn running on http://127.0.0.1:8000
This will display the FastAPI Swagger API. Use the following URL to access it:

> http://127.0.0.1:8000/docs

This will display the API documentation, including authentication and default .

To run the training model:

1. Choose the default.
2. Click on the "Try it out" button.
3. Click on the "Execute" button to run the training pipeline.

### Step: Use FastAPI to Predict

Start the FastAPI server by running the following command:

> uvicorn app:app --reload

Access the Swagger API documentation at:

> http://127.0.0.1:8000/docs

In the default section, you will find options for both training and prediction.

To run the prediction pipeline:

1. Select the predict endpoint.
2. Click on the Try it out button.
3. Choose a file from the project folder:
    - Navigate to the valid_data folder.
    - Select the test.csv file.
4. Click on the Execute button.
After execution, you will be able to see the prediction results.

### Step: Connect to AWS S3 Bucket

#### 1. Connect to Your AWS Account
- Log in to your AWS account.

#### 2. Create an IAM User
1. Go to the **IAM** service and create a new user with the name **testsecurity**.
2. Click **Next**.

#### 3. Assign Permissions
1. In the **Permission Options**, choose **Attach policies directly**.
2. Select the **AdministratorAccess** policy.
3. Click **Next**.

#### 4. Review and Create
- On the **Review and Create** page, click **Create User** to finish creating the user.

#### 5. Generate Access Keys
1. After creation, select the **testsecurity** user.
2. Navigate to the **Security Credentials** tab.
3. Under **Access Keys**, click **Create Access Keys**.
4. Choose **Command Line Interface (CLI)** during setup, confirm, and click **Next**.
5. On the **Set Description Tag** page, click **Create Access** to generate the access and secret keys.

#### 6. Configure AWS CLI
To use the keys, open a terminal in your project folder (e.g., in VS Code), and run:

> aws configure

You will be prompted to enter the following information:
- AWS Access Key ID: Enter the access key.
- AWS Secret Access Key: Enter the secret key.
- Default region name: Press Enter to leave it empty or specify a region.
- Default output format: Press Enter to leave it empty.

#### 7. Verify Connection and Start the App
Once the connection to your AWS S3 bucket is established, run the application:
> uvicorn app:app --reload

#### 8. Run the Training Model
To run the training model:

    1. Access the Swagger API documentation at http://127.0.0.1:8000/docs.
    2. In the default section, select the training endpoint.
    3. Click on the Try it out button.
    4. Execute the request to start the training pipeline.

#### 9. Check S3 Bucket
Finally, you can view the artifacts and final model in your S3 bucket.


### Step: Step: Docker Image Push to AWS ECR
To push your Docker image to AWS ECR, follow these steps:

#### 1. Create a New Repository in AWS ECR
1. Go to the Amazon Elastic Container Registry (ECR) dashboard.
2. Click on "Create repository" and enter the following details:
    - Repository name: networksecurity
    - Image tag mutability: Choose Mutable
    - Encryption: Choose AES-256
3. Click "Create repository" to create the new repository.
4. After creation, copy the AWS ECR URL.

#### 2. Create Actions Secrets and Variables
1. Go to your project settings.
2. Click on "Security" under the settings menu.
3. Click on "Actions" and then click on "Secrets".
4. Add the following new secret repository secrets:
    - **`AWS_ECR_LOGIN_URI`**: The ECR URI you copied.
    - **`AWS_ACCESS_KEY_ID`**: Your AWS Access Key.
    - **`AWS_SECRET_ACCESS_KEY`**: Your AWS Secret Access Key.
    - **`AWS_REGION`**: The AWS region where your ECR is located.
    - **`ECR_REPOSITORY_NAME`**: The name of your ECR repository.

### Step: Setting Up an EC2 Instance for GitHub Actions Runner

#### Launch an EC2 Instance
1. Go to your EC2 dashboard and click on **Instances Running**.
2. Click on **Launch an Instance**.
3. Add a name and tags:
   - Name: `networksecurity`
4. Choose **Application and OS Images**:
   - Select: `Ubuntu`.
5. Create or use an existing **Key Pair**.
6. On **Network Settings**, ensure the following are checked:
   - Allow SSH traffic from anywhere.
   - Allow HTTPS traffic from the internet.
   - Allow HTTP traffic from the internet.

#### After Instance Creation
1. Go to the **Instances** tab and click on your **Instance ID**.
2. Click on **Connect**, use the default configuration, and click on **Connect**.

---

#### Connect to Your Instance
Run the following commands on the EC2 terminal:

> sudo apt-get update -y
> sudo apt-get upgrade -y

#### Install Docker on the EC2 terminal
Download the Docker installation script
> curl -fsSL https://get.docker.com -o get-docker.sh

Run the script to install Docker
> sudo sh get-docker.sh

Add your user to the Docker group
> sudo usermod -aG docker ubuntu

Apply group changes
> newgrp docker

#### Configure a Self-Hosted GitHub Runner

    1. Go to your project's GitHub Repository > Settings > Actions > Runners.
    2. Click on Add New Self-Hosted Runner.
    3. Choose Runner Image: Linux.
    4. Follow the displayed instructions. Run the following commands on the EC2 terminal:

#### Download the Runner on the EC2 terminal
Create a folder for the runner
> mkdir actions-runner && cd actions-runner

Download the latest runner package
> curl -o actions-runner-linux-x64-2.321.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.321.0/actions-runner-linux-x64-2.321.0.tar.gz

Optional: Validate the hash
> echo "ba46ba7ce3a4d7236b16fbe44419fb453bc08f866b24f04d549ec89f1722a29e  actions-runner-linux-x64-2.321.0.tar.gz" | shasum -a 256 -c

Extract the installer
> tar xzf ./actions-runner-linux-x64-2.321.0.tar.gz


#### Configure the Runner on the EC2 terminal
Start the configuration process
> ./config.sh --url https://github.com/alassanepaulyaro/mlopswithnetworksecurity --token AF6UF7YAIUXKNI4WTLI6YHTHR2AOG

During Configuration:
- Enter the name of the runner group to add this runner to: [Press Enter for Default]
- Enter the name of the runner: self-hosted
- Enter any additional labels (e.g., label-1,label-2): [Press Enter to skip]
- Enter the name of the work folder: [Press Enter for _work]

#### Start the Runner on the EC2 terminal
Run the runner
> ./run.sh

####  Verify Runner Status
1. Go back to Runners in your GitHub repository settings.
2. You should see the status of the runner (self-hosted) as Idle.

#### EC2 - Update Security Group and Access Flask API

1. On your EC2 instance, go to the **Security Group** associated with your instance.
2. Click on **Edit Inbound Rules**.
3. Add a new inbound rule with the following details:
   - **Type**: Custom TCP
   - **Port Range**: 8080
   - **Source**: 0.0.0.0/0 (or a more restrictive IP range for better security).
4. Save the changes.

### Access the Flask API
After updating the security group, you can access your Flask API running on the EC2 instance using <EC2_PUBLIC_IP>:8080