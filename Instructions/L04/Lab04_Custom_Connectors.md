---
title: Lab 4 – Custom Connectors
---

# Scenario

In this lab, you will build a custom connector for A Datum’s Risk Score
API.

# High-level lab objectives

-   Build a custom connector

-   Modify the cloud flow to use the connector

# Exercise \#1: Create a custom connector

## Task \#1: Create a new solution

1.  Navigate to <https://make.powerapps.com/> and make sure you are in
    the Dev environment.

2.  Select **Solutions** and click **+ New solution**. We are creating a
    new solution to keep the custom connector separate from the flow
    that uses it which is the current requirement of using a custom
    connector.

3.  Enter **Builder Risk Service** for Display name, select
    **Relecloud** for Publisher, and click **Create**.

> <img src="./media/image1.png" style="width:2.83188in;height:4.30309in"
> alt="create your new solution as described" />

## Task \#2: Create custom connector

1.  Click to open the **Builder Risk Service** solution you created.

2.  Click **+ New** and select **Automation \| Custom connector**.

> <img src="./media/image2.png" style="width:5.55718in;height:1.4546in"
> alt="add a new custom connector" />

3.  Enter **Builder Risk Service** for name.

> <img src="./media/image3.png" style="width:5.67783in;height:1.08522in"
> alt="name the connector" />

4.  Enter **Builder risk service** for Description, enter
    **adatumbuilderrisktest.azurewebsites.net** for Host, and click
    **Create connector**.

> <img src="./media/image4.png" style="width:5.71305in;height:3.95275in"
> alt="create the connector" />

## Task \#3: Import Open API 

1.  Navigate to <https://adatumbuilderrisktest.azurewebsites.net/>

2.  Click **Download Logo** and save the logo on your machine.

3.  Click on the **API Key** link.

> <img src="./media/image5.png" style="width:3.96299in;height:3.03067in"
> alt="download API key" />

4.  Copy the **API Key** and save it on a notepad.

5.  Click **Return to home**.

6.  Click on the **API documentation** link.

7.  Review the documentation.

8.  Close the documentation browser tab or window, after you finish
    reviewing.

9.  Click on the **Open API definition file** link.

> <img src="./media/image6.png" style="width:4.04345in;height:3.0922in"
> alt="click to review definition" />

10. Right click and select **Save as**.

> <img src="./media/image7.png" style="width:5.4423in;height:2.52055in"
> alt="save file" />

11. Save the file on your machine.

12. Navigate to <https://make.powerapps.com/> and make sure you are in
    the Dev environment.

13. Expand **Dataverse** and select **Custom Connectors**.

> <img src="./media/image8.png" style="width:5.09775in;height:2.56794in"
> alt="expand connector list" />

14. Click on the **…** more actions button of **the Builder Risk**
    Service custom connector and select **Update from OpenAPI file**.

> <img src="./media/image9.png" style="width:5.71908in;height:1.82937in"
> alt="locate and update the OpenAPI file" />

15. Click **Import**.

16. Select the **swagger.json** file you saved to your machine and click
    **Open**.

17. Click **Continue**.

> <img src="./media/image10.png" style="width:2.95238in;height:2.321in"
> alt="Import the file" />

18. Click **Upload** logo.

> <img src="./media/image11.png" style="width:5.32586in;height:2.37501in"
> alt="upload the logo you saved" />

19. Select the logo you downloaded and click **Open**.

20. Enter **Builder risk service** for Description, enter
    **adatumbuilderrisktest.azurewebsites.net** for Host, and select the
    **Security** tab.

> <img src="./media/image12.png" style="width:5.20134in;height:3.60426in"
> alt="enter details as described" />

21. Select the definitions tab and see the operation imported.

22. Turn on **Swagger editor**.

> <img src="./media/image13.png" style="width:6.09335in;height:2.71987in"
> alt="toggle swagger editor" />

23. Show swagger editor and then turn off the **Swager editor**

24. Select Update connector and wait for the connector to be updated.

25. Do not navigate away from this page.

## Task \#4: Test connector

1.  Select the **Test** tab and click **+ New connection**.

> <img src="./media/image14.png" style="width:5.34118in;height:2.00351in"
> alt="select new connection" />

2.  Paste your **API Key** and click **Create**.

3.  Select **Custom Connectors** and click **Edit**.

> <img src="./media/image15.png" style="width:4.91639in;height:1.53532in"
> alt="edit the selected item" />

4.  Select the **Test** tab again.

5.  Make sure the connection you created is selected as connection.

6.  Enter **Contoso** for builderName, **7165 Brock Lane Renton, WA
    61795 U.S**. for propertyAddress, **JG7165** for loanNumber,
    **645000** for loanAmount, **500000** for creditAvailable,
    **100000** for drawAmount, and click **Test operation**.

> <img src="./media/image16.png" style="width:4.27346in;height:3.70458in"
> alt="enter details as described" />

7.  The test should run successfully, and you should receive a score and
    a reason.

> <img src="./media/image17.png" style="width:4.53297in;height:2.69073in"
> alt="review results" />

8.  Click **Update connector** and wait for the update to complete.

# Exercise \#2: Modify cloud flow to use connector

## Task \#1: Use custom connector in flow

1.  Navigate to <https://make.powerapps.com/> and make sure you are in
    the Dev environment.

2.  Select **Solutions** and open the **Construction Funding** solution.

3.  Select **Cloud flows**, select **Process Construction Funding
    Request** flow and click **Edit**.

> <img src="./media/image18.png" style="width:6.16521in;height:2.13411in"
> alt="locate and edit the flow" />

4.  Click **+** insert new step after the **Check if loan number found**
    condition and select **Add an action.**

> <img src="./media/image19.png" style="width:6.10693in;height:2.34295in"
> alt="add a new step" />

5.  Select **Get a row by ID** Microsoft Dataverse.

> <img src="./media/image20.png" style="width:4.62991in;height:3.03467in"
> alt="select get a row by ID action" />

6.  Select **Loans** for Table name, click on the **Row ID** field and
    select **LoanID** from the dynamic content pane.

> <img src="./media/image21.png" style="width:5.913in;height:2.47512in"
> alt="enter details as described" />

7.  Rename the step **Get loan**.

8.  Go to the **+** Insert a new step button after the **Run inspection
    process** and select **Add an action**.

> <img src="./media/image22.png" style="width:5.60254in;height:1.46515in"
> alt="add an action" />

9.  Go to the **Custom** tab and select **Builder Risk Service**.

> <img src="./media/image23.png" style="width:4.68659in;height:2.0619in"
> alt="add the custom action you provided" />

10. Select the **Calculate Risk Score** action.

11. Enter **Risk Service** for Connection name, paste the API Key you
    copied earlier, and click **Create**.

> <img src="./media/image24.png" style="width:5.10998in;height:2.1739in"
> alt="enter details as described" />

12. Click on the **builderName** field and select **Builder** from the
    dynamic content pane.

> <img src="./media/image25.png" style="width:5.58591in;height:2.37401in"
> alt="enter details as described" />

13. Click on the **propertyAddress** field and select **Address** from
    the dynamic content pane.

14. Click on the **loanNumber** field and select **Loan Number** from
    the dynamic content pane.

15. Click on the **loanDate** field and select **Loan Date** from the
    dynamic content pane.

16. Click on the **loanAmount** field and select **Loan Amount** form
    the dynamic content pane.

17. Click on the **creditAvailable** field and select **Credit
    Available** from the dynamic content pane.

18. Enter **80000** for drawAmount.

19. The calculate risk score step should now look like the image below.

> <img src="./media/image26.png" style="width:5.28654in;height:3.12929in"
> alt="review the details" />

20. Click on the **+** Insert a new step after the **Calculate Risk
    Score** step and select **Add an action**.

> <img src="./media/image27.png" style="width:5.35444in;height:2.08021in"
> alt="add an action" />

21. Select **Update a row** Microsoft Dataverse.

22. Select **Loan Draws** for Table name, click on the **Row ID** field
    and select **Loan Draw** from the dynamic content pane.

23. Click on the **Risk Score** field and select **score** from the
    dynamic content pane.

24. Select **Risk Scored** for Status reason.

25. Rename the step **Update loan draw risk score**.

26. The update loan draw step should look like the image below.

> <img src="./media/image28.png" style="width:3.97423in;height:5.11577in"
> alt="review the details" />

27. Click to expand the **Run inspection process** step.

28. Remove the **PropertyAddress** value and select **Address** from the
    dynamic content pane.

> <img src="./media/image29.png" style="width:4.91691in;height:2.72092in"
> alt="enter details as described" />

29. Expand the **Run funding process** step.

30. Remove the **RiskScore** value and select **Score** from the dynamic
    content pane.

> <img src="./media/image30.png" style="width:5.19373in;height:3.15009in"
> alt="enter details as described" />

31. Click **Save** and wait for the flow to be saved.

## Task \#2: Test the flow

1.  Click **Test**.

2.  Select **Manually** and click **Save & Test**.

3.  Send an email to <Funding@yourdomain.onmicrosoft.com> make sure the
    subject of the email is **PS7765**.

4.  Flow test should succeed.

5.  Expand the **Calculate Risk Score** step.

6.  The output should look like the image below.

> <img src="./media/image31.png" style="width:4.53889in;height:2.07153in"
> alt="test the flow" />

7.  You should also receive an email with the subject Funding Approved.
