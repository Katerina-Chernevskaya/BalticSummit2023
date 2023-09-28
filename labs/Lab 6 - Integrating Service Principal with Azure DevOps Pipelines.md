
<img src="https://github.com/Katerina-Chernevskaya/alm-odyssey/blob/139826d18dd6b82d3a8efb4a2f6b3a3f0599b828/labs/screenshots/lab6/6-ServicePrincipal.png" width="100">

# 1. Create App Registration

1. Navigate to [https://portal.azure.com/](https://portal.azure.com/).

2. In the search field type `registration` and in the drop-down list select `App registration`.

![lab6-ServicePrincipal1.png](./screenshots/lab6/lab6-1.png)

3. Click `New registration` on the `App registrations` page.

4. Enter `ALMSpace` in the `Name` field, keep other fields with predefined values and click `Register`.

![lab6-ServicePrincipal2.png](./screenshots/lab6/lab6-2.png)

5. Once the app registration is created, navigate to `API permissions` on the left-hand menu.

6. Click `+ Add a permission`.

7. In the pop-up window find and choose `Dynamics CRM`.

![lab6-ServicePrincipal3.png](./screenshots/lab6/lab6-3.png)

8. Select `user_impersonation` and click `Add permissions`.

![lab6-ServicePrincipal4.png](./screenshots/lab6/lab6-4.png)

9. Click `Grant admin consent for YOUR COMPANY NAME` and click `Yes` in the pop-up window.

![lab6-ServicePrincipal5.png](./screenshots/lab6/lab6-5.png)

10. Navigate to `Certificates & secrets`.

11. Click `+ New client secret`.

12. Enter `ALMSpaceSecret` in the `Description` field and click `Add`.

![lab6-ServicePrincipal6.png](./screenshots/lab6/lab6-6.png)

13. Copy secret from the `Value` field and store it somewhere (in Notepad for instance).

:exclamation: _Note:
Once you close this tab or navigate somewhere from this screen, the Secret value won't be available for copy._

![lab6-ServicePrincipal7.png](./screenshots/lab6/lab6-7.png)

14. Navigate to `Overview` and copy value from fields `Application (client) ID` and `Directory (tenant) ID`.

![lab6-ServicePrincipal8.png](./screenshots/lab6/lab6-8.png)

***


# 2. Add the Service Principal into Power Platform

1. Navigate to [Power Platform admin center -> Environments](https://admin.powerplatform.microsoft.com/environments).

2. Open `Dev` environment.

3. Click `See all` bellow `Users`.

![lab6-ServicePrincipal9.png](./screenshots/lab6/lab6-9.png)

4. Click `app users list` in the opened screen.

![lab6-ServicePrincipal10.png](./screenshots/lab6/lab6-10.png)

5. Click `+ New app user`, and in the pop-up window click `+ Add an app`.

![lab6-ServicePrincipal11.png](./screenshots/lab6/lab6-11.png)

6. Select `ALMSpace` and click `Add`.

![lab6-ServicePrincipal12.png](./screenshots/lab6/lab6-12.png)


7. Select `Business unit`, add `System Customizer` and `System Administrator` security roles, and click `Create`.

![lab6-ServicePrincipal13.png](./screenshots/lab6/lab6-13.png)


8. Repeat all steps in this section for the `Test` environment.

*** 


# 3. Create Connection in Azure DevOps using App Registration

1. Navigate to your project in Azure DevOps and open `Pipelines` tab on the left-hand menu.

2. Click on three dots for the pipeline that you created in the previous lab, and click `Edit`.

![lab6-ServicePrincipal14.png](./screenshots/lab6/lab6-14.png)

3. Go to the step `Power Platform Export Solution` and switch `Authentication type` to `Service Principal/client secret (support MFA)`. After click `Manage` next to `Service connection`.

![lab6-ServicePrincipal15.png](./screenshots/lab6/lab6-15.png)

4. Click `New service connection`.

5. Select `Power Platform` and click `Next`.

![lab6-ServicePrincipal16.png](./screenshots/lab6/lab6-16.png)

6. Fill in the form:
- `Authentication method` - `Application Id and client secret`.
- `Server URL` - get this value from Power Apps Maker portal (see bellow).
- `Tenant Id` - `Directory (tenant) ID` that you copied on step 1.
- `Application Id` - `Application (client) ID` that you copied on step 1.
- `Client secret of Application Id` - Secret value that you copied on step 1.
- `Service connection name` - `Dev Service Principal`.

:exclamation: _Note:
To find value for_ `Server URL` _field go to Power Apps maker porta, select environment_ `Dev` -> `Settings` -> `Session details`

![lab6-ServicePrincipal17.png](./screenshots/lab6/lab6-17.png)

Click `Save`.
Completed form should look as the following:

![lab6-ServicePrincipal18.png](./screenshots/lab6/lab6-18.png)

7. Go back to your pipeline, refresh `Service connection` field and select `Dev Service Principal`.

![lab6-ServicePrincipal19.png](./screenshots/lab6/lab6-19.png)

8. Before run this updated pipeline, go to your solution and update value of the `Color` environment variable. The new value - `#17A59C`.

***


# 4. Run pipeline

1. Click `Save & queue`, after click `Save and run`.

2. Once the run will be completed successfully, go to `Repos` and check `History` of the `environmentvariablevalues.json` file.

![lab6-ServicePrincipal20.png](./screenshots/lab6/lab6-20.png)

***















