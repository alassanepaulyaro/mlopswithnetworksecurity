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