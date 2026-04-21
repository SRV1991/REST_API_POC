# REST API POC

## Project Overview
This REST API Proof of Concept (POC) demonstrates the basic functionalities of a RESTful service. The project includes endpoints for CRUD operations and is built to be deployed on IIS.

## IIS Deployment Instructions

### Prerequisites
1. **Windows Server**: Ensure you have a Windows Server with IIS installed.
2. **.NET Framework**: Verify that the appropriate version of the .NET Framework is installed on your server.
3. **IIS Features**: Make sure the following features are enabled in IIS:
   - Application Development Features: .NET Extensibility, ASP.NET
   - Management Tools: IIS Management Console

### Steps to Deploy
1. **Publish the Project**:
   - Right-click on the project in Visual Studio.
   - Select **Publish**.
   - Choose a target and publish method, then follow the prompts to create a published version of your API.

2. **Open IIS Manager**:
   - Press `Windows + R`, type `inetmgr`, and hit Enter.

3. **Create a New Application Pool**:
   - In the Connections pane, right-click on **Application Pools** and select **Add Application Pool**.
   - Set a name for the pool and select the .NET Framework version.
   - Click **OK**.

4. **Set Up a New Website**:
   - Right-click on **Sites** and select **Add Website**.
   - Fill in the site name, select the physical path where you published your project, and set the binding options (host name, port).
   - Under the **Application Pool** section, select the application pool you just created.
   - Click **OK**.

5. **Configure Permissions**:
   - Navigate to the folder where your published files exist.
   - Right-click the folder and go to **Properties** -> **Security**.
   - Click **Edit** and add the user **IIS_IUSRS** with adequate permissions (Read & Execute, List folder contents).

6. **Start the Website**:
   - In IIS Manager, right-click on your new site and select **Manage Website** -> **Start**.

7. **Test the Deployment**:
   - Open a web browser and enter the URL of your newly created site to ensure it is running properly. You should see the API's welcome message or a default response.

### Troubleshooting Tips
- If you encounter a 500 internal server error, check the IIS logs located in `C:\inetpub\logs\LogFiles` for detailed error messages.
- Ensure the firewall is configured to allow traffic on the port you selected during binding.

### Conclusion
Following these steps, you should have your REST API deployed and running on IIS without any issues. For further customization and configuration, refer to the official Microsoft documentation on IIS and ASP.NET deployment.