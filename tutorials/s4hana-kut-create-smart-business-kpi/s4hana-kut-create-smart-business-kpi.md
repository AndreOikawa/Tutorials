---
title: Create a Smart Business KPI from an Analytical Query
description: Create a KPI to analyze a specific key figure (e.g., cost per employee) and display this on the SAP Fiori launchpad.
auto_validation: true
primary_tag: topic>abap-development
tags: [  tutorial>intermediate, topic>abap-development, products>sap-s-4hana ]
time: 30
---

## Details
### You will learn  
- How to create a KPI to analyze a specific key figure
- How to display a specific key figure on the SAP Fiori launchpad


---

[ACCORDION-BEGIN [Step 1: ](Log into SAP Fiori launchpad)]
First you need to log into the Fiori Launchpad.
Click this link in your browser: [Link will be available soon]

You should see this page:

![ Fiori Launchpad login screen](kut_smbkpi_01.png)

Log on with your user and password
>Your your user is your desktop number. Your password will be given to you by your instructor.

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Execute the KPI Workspace)]

In the Fiori Launchpad, from the group KPI Design select the App KPI Workspace and double click on it as on the below picture:

![Apps on the Fiori Launchpad](kut_smbkpi_02.png)

[DONE]
[ACCORDION-END]


[ACCORDION-BEGIN [Step 3: ](Get started with KPI Creation)]

1. After you have successfully executed the App KPI Workspace, the below window gets open.
![Apps on the Fiori Launchpad](kut_smbkpi_03.png)

2. In the KPI Workplace window, click on the + Add on the bottom left toolbar to create a KPI as depicted below:

    ![Create Report](kut_smbkpi_04.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Maintain parameters of KPI)]

1. In the create KPI window maintain the relevant field from Parameters as follow:

    |  Field Name         | Value
    |  :------------------| :-------------
    |  Title              | `XXX_ APSEMTAGSTATISTIC`
    |  Description        | `XXX_ APSEMTAGSTATISTIC`

    > Replace **`XXXX`** with your initials !
    ![Maintain Parameters](kut_smbkpi_05.png)

2. In the create KPI window maintain all the relevant fields for Data Source as follow:

    - CDS View:  In the search button for the CDS view, enter `APSEM`. The List of CDS views for which the user has access permissions and starting with `APSEM` are shown.

3. Select the CDS view: `ZC_APSEMTAGSTATISTICAL`  as shown on the below picture.

    ![Maintain Data Source](kut_smbkpi_06.png)

4. `OData` Service: In the search fields for the selected `OData` CDS  view the list of `OData` services available is displayed. Select the `OData` Service `/sap/opu/odata/sap/ZC_APSEMTAGSTATISTICAL_CDS`

    ![Maintain OData Service](kut_smbkpi_07.png)

5. After selecting the CDS View and the OData select the Entity Set which you would use for defining the KPI. In the search field, open the list of available Entity set and select the relevant one as shown on the below picture.

    ![Maintain Entity Set](kut_smbkpi_08.png)

6. The Selection of the Entity Set would bring all the measures available in the set in the search view. Here chooses the measure **`NetIncomeAmtByNumberofEmpl`**

    ![Maintain Measure](kut_smbkpi_09.png)

7. At the end of the measure selection, you should have the following selections complete for creating the KPI:
 CDS view, associated OData, Entity Set contained in the OData and finally the measure with which you would create the KPI. To continue click **Activate and add Evaluation** button.

    ![Maintain Measure condt](kut_smbkpi_10.png)

8. On the Save Transport screen, select and click on the **Local Object** button.

    ![Maintain Local Object ](kut_smbkpi_11.png)


[VALIDATE_1]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Create evaluation for the KPI)]

The **Evaluation window** gets open with `prefilled` data.

![Evaluation Data ](kut_smbkpi_12.png)

The evaluation would define the KPI based on **`AmountInGlobalCurrency`**, or any other dimensions.

1. Maintain:

    |  Field Name          | Value
    |  :-------------------| :-------------
    |  Evaluation          | `Evaluation_XXXX`

    >Replace XXXX with your initials !

    ![Maintain Evaluation ](kut_smbkpi_13.png)

2. Maintain the field **Scaling Factor** with **`Auto`** and **Decimal Precision** with **`Auto`**

    ![Maintain Scaling Factor ](kut_smbkpi_14.png)

3. Maintain the Input for the mandatory Parameters as define in the CDS view as follow:

    |  Field Name                | Value
    |  :-------------------------| :-------------
    |  To-Period                 | `007`
    |  Category                  | `ATC01`
    |  Fin Statement Version     | `L000`
    |  Fiscal Year               | `2018`
    |  Controlling Area          | `A000`

    ![Maintain Parameters](kut_smbkpi_15.png)

5. Define the Target and the threshold values. To achieve this you need to maintain input values for the Target, Warning and the critical values as follow:

    |  Field Name         | Value
    |  :------------------| :-------------
    |  Critical           | `50000`
    |  Warning            | `500000`
    |  Target             | `425000`

    ![Maintain Threshold](kut_smbkpi_16.png)

6. After the maintenance of the Target, Thresholds and Trend, click **Activate and Configure Tile** to define a visual representation **Tile** for the Evaluation you have defined.

    ![Activation of the Tile](kut_smbkpi_17.png)


[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Choose visualization option and configure )]

In this step you would choose from the various visualization options for the evaluation. You could choose from a Numeric Tile, Comparison Tile, Trend Tile, Actual vs. Target Tile, Comparison Tile Multiple Measures, Blank Tile and Dual Tile

![Selection of the visualization options](kut_smbkpi_18.png)

1. Maintain the Tile configuration by selecting Tile Format, Catalog, to which the Tile will be attached with, the Semantic Object  and the Action as follow:

    |  Field Name         | Value
    |  :------------------| :-------------
    |  Title Format       | `Numeric Tile`
    |  Title              | `XXX_ APSEMTAGSTATISTIC`
    |  Subtile            | `Evaluation_XXXX`
    |  Catalog            | `X-SAP-UI2-CATALOGPAGE:Z_MONJE_TEC`
    |  Cache Duration     | `5 Minutes`
    |  Select Drill-Down  | `Generic`
    |  Semantic Object    | `CostCenter`
    |  Action             | `analyze_xxxx`

    > Select the right catalogue by pushing the drill-down menu for **Catalog**.
    Enter `Z_MONJE_TEC` in the search line and press the magnifying glass button.

    ![Maintain the Tile Configuration](kut_smbkpi_19.png)

2.  Press **Save and Configure Drill Down** to create a generic **Smart Business Drill-Down** for the KPI Tile you previously created.

    ![OK Button](kut_smbkpi_20.png)

[VALIDATE_2]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 7: ](Configure Smart Business drill-down)]

1. In the **Configure KPI Drill-Down Window**, select the KPI Evaluation you worked on in the previous steps.

    ![Configure KPI Drill-down](kut_smbkpi_21.png)

2. Press **Configure** to create a generic Smart Business Drill Down for the KPI Tile you created.
In the Select screen, chooses from the Tab **Dimension** the dimensions for which you would love to configure the Drill-Down report e.g.:

    -	`Cost Center`
    - `Fiscal Period`
    - `Fiscal Year`

    ![Select Dimension](kut_smbkpi_22.png)

3. Afterwards click on the OK button

    ![OK Button](kut_smbkpi_23.png)

4. Maintain the Drill-Down Chart details as follow:


    |  Field Name         | Value
    |  :------------------| :-------------
    |  View Title         | `XXXX_KPIChart`

    >Replace `XXXX` with your initials !

    ![Maintain KPIChart Details](kut_smbkpi_24.png)

5. Afterwards click on the OK button.

6. On the **SAP Smart Business Generic Drill-Down** screen, click on the **Save Configuration** button
as it is shown on the similar picture below.

    ![Save KPIChart Details](kut_smbkpi_25.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 8: ](Execute report)]

1. Return to the Fiori Launchpad, click on the Me Icon (top left corner next to the SAP logo). The Me Area opens on the left  similar to the one shown below:

    ![Report execution](kut_smbkpi_29.png)

2. Click on the App Finder to get it open ...

    ![Report execution](kut_smbkpi_26.png)

    ... and afterwards click on the catalog `Z_MONJE_TEC` similar to the picture below.

    ![Report execution](kut_smbkpi_27.png)

3. Search for  the Tile labeled with **`XXX_ APSEMTAGSTATISTIC`**. The Tile for your report will be displayed.

4. Click on the Tile you found to start the Report.

    ![Report execution](kut_smbkpi_27.png)

5. The KPI Report shows up with a chart or table  depending on how you have configured in the previous step. You should have a Report similar to the one below.

    ![Report execution](kut_smbkpi_28.png)

[DONE]
[ACCORDION-END]

## Next Steps
