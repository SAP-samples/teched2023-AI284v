# Exercise 5 - Process a work contract using Document Information Extraction and LLMs

In this exercise, you'll extract information from a custom document - in this case, a work contract. The Document Information Extraction service doesn't support custom document types out of the box. So, you'll create a custom schema to define the fields that you want to extract from a work contract document using LLMs (Large Language Models).

## Exercise 5.1 Access schema configuration

1. Open the Document Information Extraction application, as described in the tutorial: [Use Trial to Set Up Account for Document Information Extraction and Go to Application](https://developers.sap.com/tutorials/cp-aibus-dox-booster-app.html).


    >If you **HAVE NOT** just used the **Set up account for Document Information Extraction** booster to create a service instance for Document Information Extraction and subscribe to the Document Information Extraction application, observe the following:

    >- To access the [Schema Configuration](https://help.sap.com/viewer/5fa7265b9ff64d73bac7cec61ee55ae6/SHIP/en-US/3c7862e30fc2488ea95f58f1d77e424e.html) feature, ensure that you use the `blocks_of_100` plan to create the service instance for Document Information Extraction Trial.

    <br>![](/exercises/ex5/images/plan.png)


    >- And make sure you're assigned to the role collection: `Document_Information_Extraction_UI_Templates_Admin_trial`. For more details on how to assign role collections, see step 2 in the tutorial: [Use Trial to Subscribe to Document Information Extraction Trial UI](https://developers.sap.com/tutorials/cp-aibus-dox-ui-sub.html).

    <br>![](/exercises/ex5/images/roles.png)


    >- After assigning new role collections, **Log Off** from the UI application to see all features you're now entitled to try out.

    <br>![](/exercises/ex5/images/log-off.png)


2. To create a custom schema, click the wheels icon and choose **Schema Configuration**.

    <br>![](/exercises/ex5/images/access-schema-configuration.png)

Here, you find the SAP schemas. The Document Information Extraction application includes preconfigured SAP schemas for the following standard document types: purchase order, payment advice, and invoice. In addition, there’s an SAP schema for custom documents (`SAP_OCROnly_schema`). You can’t delete or change SAP schemas. You can use them as they are, or create copies and adapt the list of fields according to your needs.

<br>![](/exercises/ex5/images/sap-schemas.png)


>**CAUTION:**

>When using the free tier option for Document Information Extraction or a trial account, be aware of the technical limits listed in [Free Tier Option and Trial Account Technical Constraints](https://help.sap.com/docs/document-information-extraction/document-information-extraction/free-tier-option-and-trial-account-technical-constraints).



## Exercise 5.2 Create schema

To create your own schema, click **Create** and a dialog opens.

<br>![](/exercises/ex5/images/create-schema.png)

In the dialog, enter a name for your custom schema, `work_contract_schema`, for example. Note that the name can't include blanks. Further, select `Custom` as your **Document Type** and `Document` for **OCR Engine Type**.

Click **Create** to create the schema.

<br>![](/exercises/ex5/images/create-schema-dialog.png)

Now, your schema shows up in the list. Access the schema by clicking on it.

<br>![](/exercises/ex5/images/access-schema.png)



## Exercise 5.3 Add data fields (header fields and line item fields)

To add your first header field, click **Add**.

<br>![](/exercises/ex5/images/add-field.png)

For each custom field, you've to enter name and data type. The available data types are `string`, `number`, `date`, `discount`, `currency`, and `country/region`. Default extractors aren't available for custom documents. Adding a description is optional.

As your first header field, add the company name in your work contract.

1. Enter the name for your field, `companyName`, for example.

2. Enter the following description for this field: `Name of the company`.

3. Select `string` for the `Data Type`.

4. Select `auto` for the `Setup Type` and click **Add** to create the header field. Note that when you use the setup type `auto` without a default extractor, LLMs are then used to extract the information from the document.

    <br>![](/exercises/ex5/images/add-companyName.png)

The field now displays in your list of header fields, where you again find all the information that you've just entered. You can edit or delete the field by clicking the respective icons on the right.

<br>![](/exercises/ex5/images/added-name.png)

Click **Add** again to open the `Add Data Field` dialog.

1. Enter the name for your second header field, `employeeName`, for example.

2. Enter the following description for this field: `Name of the employee`.

3. Select `string` for the `Data Type`.

4. Select `auto` for the `Setup Type` and click **Add** to create the field.

    <br>![](/exercises/ex5/images/add-employeeName.png)

Go ahead and create the list of header fields as shown in the table and image below. Pay attention to the different data types. Don't forget to add a description for all fields (as in the image). Feel free to extend or reduce the list of fields.

|  Field Type		    |  Field Name           | Data Type     | Setup Type   
|  :------------------- |  :-------------------	| :----------   | :----------    
|  header field         |  `companyName`        | string        | auto       
|  header field         |  `employeeName`       | string        | auto
|  header field         |  `limitedContract`    | string        | auto           
|  header field         |  `salary`             | number        | auto       
|  header field         |  `startDate`          | date          | auto       
             

<br>![](/exercises/ex5/images/all-fields.png)



## Exercise 5.4 Activate schema

Once you've added all fields, the schema needs to be activated so that it can be used to extract information from documents. Right now, the schema has the status `DRAFT`, indicating that it can't be used yet.

To activate the schema, click **Activate**.

<br>![](/exercises/ex5/images/activate.png)

Now, the status of your schema changes to `ACTIVE`. To make changes to your schema, you've to **Deactivate** it first.

<br>![](/exercises/ex5/images/active.png)

Congratulations, you've now created and activated your custom schema for work contract documents.



## Exercise 5.5 Get extraction results

1.  Access **Document** on the left navigation pane and click **+** to upload a new document.

    <br>![](/exercises/ex5/images/add-document.png)

2. On the Select Document screen, choose `Custom` for the **Document Type**.

3. Select the **Schema** you created (`work_contract_schema`).

4. Drop the file directly or click **+** to upload the [work contract](https://github.com/SAP-samples/teched2023-AI284v/blob/main/exercises/ex5/files/work_contract.pdf) sample document.

5. Click **Step 2**.

    <br>![](/exercises/ex5/images/upload.png)

6. Click **Step 3** and then click **Review**.

7. Review your selection. Click **Edit** if you want to change anything. Click **Confirm**.

    <br>![](/exercises/ex5/images/review.png)

    The document status changes from `PENDING` to `READY`.

    <br>![](/exercises/ex5/images/ready.png)

8. Click the document row and **Extraction Results** to see the information extracted from the document using LLMs and the schema you created.

    <br>![](/exercises/ex5/images/results.png)



## Summary

You've now successfully extracted information from a work contract document using the Schema Configuration feature from Document Information Extraction and LLMs.

Congratulations, you've completed all the exercises.
