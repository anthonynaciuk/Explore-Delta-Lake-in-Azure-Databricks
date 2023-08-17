# Explore-Delta-Lake-in-Azure-Databricks
Exploring Azure Databricks Delta Lake capabilities 
PROJECT SETUP REQUIREMENTS:

Before you start
You’ll need an Azure subscription in which you have administrative-level access.

Provision an Azure Databricks workspace
In this exercise, you’ll use a script to provision a new Azure Databricks workspace.

In a web browser, sign into the Azure portal at https://portal.azure.com.
Use the [>_] button to the right of the search bar at the top of the page to create a new Cloud Shell in the Azure portal, selecting a PowerShell environment and creating storage if prompted. The cloud shell provides a command line interface in a pane at the bottom of the Azure portal, as shown here:

Azure portal with a cloud shell pane

Note: If you have previously created a cloud shell that uses a Bash environment, use the the drop-down menu at the top left of the cloud shell pane to change it to PowerShell.

Note that you can resize the cloud shell by dragging the separator bar at the top of the pane, or by using the —, ◻, and X icons at the top right of the pane to minimize, maximize, and close the pane. For more information about using the Azure Cloud Shell, see the Azure Cloud Shell documentation.

In the PowerShell pane, enter the following commands to clone this repo:

Code
 rm -r dp-203 -f
 git clone https://github.com/MicrosoftLearning/dp-203-azure-data-engineer dp-203
After the repo has been cloned, enter the following commands to change to the folder for this lab and run the setup.ps1 script it contains:

Code
 cd dp-203/Allfiles/labs/25
 ./setup.ps1
If prompted, choose which subscription you want to use (this will only happen if you have access to multiple Azure subscriptions).

Wait for the script to complete - this typically takes around 5 minutes, but in some cases may take longer. While you are waiting, review the Introduction to Delta Technologies article in the Azure Databricks documentation.
Create a cluster
Azure Databricks is a distributed processing platform that uses Apache Spark clusters to process data in parallel on multiple nodes. Each cluster consists of a driver node to coordinate the work, and worker nodes to perform processing tasks.

Note: In this exercise, you’ll create a single-node cluster to minimize the compute resources used in the lab environment (in which resources may be constrained). In a production environment, you’d typically create a cluster with multiple worker nodes.

In the Azure portal, browse to the dp203-xxxxxxx resource group that was created by the script you ran.
Select the databricksxxxxxxx Azure Databricks Service resource.
In the Overview page for databricksxxxxxxx, use the Launch Workspace button to open your Azure Databricks workspace in a new browser tab; signing in if prompted.
If a What’s your current data project? message is displayed, select Finish to close it. Then view the Azure Databricks workspace portal and note that the sidebar on the left side contains icons for the various tasks you can perform. The sidebar expands to show the names of the task categories.
Select the (+) New task, and then select Cluster.

Note: If a tip is displayed, use the Got it button to close it. This applies to any future tips that may be displayed as you navigate the workspace interface for the first time.

In the New Cluster page, create a new cluster with the following settings:
Cluster name: User Name’s cluster (the default cluster name)
Cluster mode: Single Node
Access mode (if prompted): Single user
Databricks runtime version: 10.4 LTS (Scala 2.12, Spark 3.2.1)
Use Photon Acceleration: Unselected
Node type: Standard_DS3_v2
Terminate after 15 minutes of inactivity
Wait for the cluster to be created. It may take a minute or two.
Note: If your cluster fails to start, your subscription may have insufficient quota in the region where your Azure Databricks workspace is provisioned. See CPU core limit prevents cluster creation for details. If this happens, you can try deleting your workspace and creating a new one in a different region. You can specify a region as a parameter for the setup script like this: ./setup.ps1 eastus

Explore data using a notebook
As in many Spark environments, Databricks supports the use of notebooks to combine notes and interactive code cells that you can use to explore data.

Expand the task bar on the left and select the Workspace tab. Then select the Users folder and in the ▾ menu for the ⌂ your_user_name folder, select Import.
In the Import Notebooks dialog box, select URL and import the notebook from https://github.com/MicrosoftLearning/dp-203-azure-data-engineer/raw/master/Allfiles/labs/25/Delta-Lake.ipynb.
Select ⌂ Home and then open the Delta-Lake notebook you just imported.
Ensure that the notebook is attached to User Name’s cluster, and follow the instructions it contains; running the cells it contains to work with Delta Lake.
Delete Azure Databricks resources
Now you’ve finished exploring Delta Lake in Azure Databricks, you must delete the resources you’ve created to avoid unnecessary Azure costs and free up capacity in your subscription.

Close the Azure Databricks workspace browser tab and return to the Azure portal.
On the Azure portal, on the Home page, select Resource groups.
Select the dp203-xxxxxxx resource group (not the managed resource group), and verify that it contains your Azure Databricks workspace.
At the top of the Overview page for your resource group, select Delete resource group.
Enter the dp203-xxxxxxx resource group name to confirm you want to delete it, and select Delete.

After a few minutes, your resource group and the managed workspace resource groups associated with it will be deleted.
