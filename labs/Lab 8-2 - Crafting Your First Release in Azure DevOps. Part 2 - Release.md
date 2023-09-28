As we transition from construction to launch, welcome to the **Release Rocket Refinement Runway**. This is where our meticulously assembled projects get their final checks, ensuring they're ready to soar flawlessly in the vast expanse of the development universe. Here, we delve deep into the art of configuring releases, ensuring every component is primed for a flawless lift-off.

At this runway, master the nuances of setting up release pipelines, capturing the essence of perfection and readiness. The excitement is palpable, as we prepare our projects for their moment of glory, ensuring they take flight with precision, grace, and boundless potential in the vast cosmos of development.

<img src="https://github.com/Katerina-Chernevskaya/BalticSummit2023/blob/a0a2c0c73428b9088a249b573ee761f4e3987418/labs/screenshots/lab8-2/8-2-DeploymentDock.png" width="100">

# 1. Create Release

1. Navigate to `Releases`.

2. Select `New pipeline`.

![lab8-Release1.png](./screenshots/lab8-2/lab8-1.png)

3. Select `Empty job`.

![lab8-Release2.png](./screenshots/lab8-2/lab8-2.png)

4. Close information pane.

![lab8-Release3.png](./screenshots/lab8-2/lab8-3.png)

5. Click `+ Add an artifact`

![lab8-Release4.png](./screenshots/lab8-2/lab8-4.png)

6. Fill in the following fields:
- `Source (build pipeline)` - select `ALM Odyssey-Build` (the name of the Build pipeline).
- `Source alias` - `drop`.

![lab8-Release5.png](./screenshots/lab8-2/lab8-5.png)

7. Click `Add`.

8. Click `1 job, 0 task`.

![lab8-Release6.png](./screenshots/lab8-2/lab8-6.png)

9. Add the following tasks:
- `Power Platform Tool Installer`
- `Power Platform Import Solution`

![lab8-Release7.png](./screenshots/lab8-2/lab8-7.png)

***


# 2. Configure task Power Platform Import Solution

### Filed: Authentication type

Select `Service Principal/client secret (support MFA)`

### Field: Service connection

Select `Test Service Principal`

### Field: Solution Input File

Click on three dots, select `GalacticGuide_managed.zip` and click `OK`.

![lab8-Release8.png](./screenshots/lab8-2/lab8-8.png)

### Field: Use deployment settings file

Ensure that you check this field.

### Field: Deployment Settings File

Click on three dots, select `GalacticGuide.json` and click `OK`.

![lab8-Release9.png](./screenshots/lab8-2/lab8-9.png)

### Section: Advanced

Check `Import as a Managed solution`.

![lab8-Release10.png](./screenshots/lab8-2/lab8-10.png)

***


# 3. Save and create Release

1. Click `Save`, then click `OK`.

2. Click `Create release, then click `Create`.

![lab8-Release11.png](./screenshots/lab8-2/lab8-11.png)

***

# 4. Check Test environment

1. Go to `Test` environment.

2. Open the solution `Galactic Guide`.

3. Open the environment variable `Color` and check that the `Current Value` is `#FF66C4` (as we defined in the Settings file).

![lab8-Release15.png](./screenshots/lab8-2/lab8-12.png)

4. Share the app with your account and Play it. You should see something like this (according to your app that you created in the Lab 3):

![lab8-Release16.png](./screenshots/lab8-2/lab8-13.png)

***








