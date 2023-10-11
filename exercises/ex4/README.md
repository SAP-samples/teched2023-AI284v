# Exercise 4 - Process a birth certificate using Document Information Extraction and LLMs

In this exercise, you'll extract information from a custom document - in this case, a birth certificate. The Document Information Extraction service doesn't support custom document types out of the box. So, you'll create a custom schema to define the fields that you want to extract from a birth certificate document using LLMs (Large Language Models).

## Exercise 4.1 Access schema configuration

1. Open the Document Information Extraction application, as described in the tutorial: [Use Trial to Set Up Account for Document Information Extraction and Go to Application](https://developers.sap.com/tutorials/cp-aibus-dox-booster-app.html).


    >If you **HAVE NOT** just used the **Set up account for Document Information Extraction** booster to create a service instance for Document Information Extraction and subscribe to the Document Information Extraction application, observe the following:

    >- To access the [Schema Configuration](https://help.sap.com/viewer/5fa7265b9ff64d73bac7cec61ee55ae6/SHIP/en-US/3c7862e30fc2488ea95f58f1d77e424e.html) feature, ensure that you use the `blocks_of_100` plan to create the service instance for Document Information Extraction Trial.

    <br>![](/exercises/ex4/images/plan.png)


    >- And make sure you're assigned to the role collection: `Document_Information_Extraction_UI_Templates_Admin_trial`. For more details on how to assign role collections, see step 2 in the tutorial: [Use Trial to Subscribe to Document Information Extraction Trial UI](https://developers.sap.com/tutorials/cp-aibus-dox-ui-sub.html).

    <br>![](/exercises/ex4/images/roles.png)


    >- After assigning new role collections, **Log Off** from the UI application to see all features you're now entitled to try out.

    <br>![](/exercises/ex4/images/log-off.png)


2. To create a custom schema, click the wheels icon and choose **Schema Configuration**.

    <br>![](/exercises/ex4/images/access-schema-configuration.png)

Here, you find the SAP schemas. The Document Information Extraction application includes preconfigured SAP schemas for the following standard document types: purchase order, payment advice, and invoice. In addition, there’s an SAP schema for custom documents (`SAP_OCROnly_schema`). You can’t delete or change SAP schemas. You can use them as they are, or create copies and adapt the list of fields according to your needs.

<br>![](/exercises/ex4/images/sap-schemas.png)


>**CAUTION:**

>When using the free tier option for Document Information Extraction or a trial account, be aware of the technical limits listed in [Free Tier Option and Trial Account Technical Constraints](https://help.sap.com/docs/document-information-extraction/document-information-extraction/free-tier-option-and-trial-account-technical-constraints).



## Exercise 4.2 Create schema

To create your own schema, click **Create** and a dialog opens.

<br>![](/exercises/ex4/images/create-schema.png)

In the dialog, enter a name for your custom schema, `birth_certificate_schema`, for example. Note that the name can't include blanks. Further, select `Custom` as your **Document Type** and `Document` for **OCR Engine Type**.

Click **Create** to create the schema.

<br>![](/exercises/ex4/images/create-schema-dialog.png)

Now, your schema shows up in the list. Access the schema by clicking on it.

<br>![](/exercises/ex4/images/access-schema.png)



## Exercise 4.3 Add data fields (header fields and line item fields)

To add your first header field, click **Add**.

<br>![](/exercises/ex4/images/add-field.png)

For each custom field, you've to enter name and data type. The available data types are `string`, `number`, `date`, `discount`, `currency`, and `country/region`. Default extractors aren't available for custom documents. Adding a description is optional.

As your first header field, add the child name in the birth certificate.

1. Enter the name for your field, `name`, for example.
   
2. Enter the following description for this field: `Name of child (first name and last name)`.

3. Select `string` for the `Data Type`.

4. Select `auto` for the `Setup Type` and click **Add** to create the header field. Note that when you use the setup type `auto` without a default extractor, LLMs are then used to extract the information from the document.

    <br>![](/exercises/ex4/images/add-name.png)

The field now displays in your list of header fields, where you again find all the information that you've just entered. You can edit or delete the field by clicking the respective icons on the right.

<br>![](/exercises/ex4/images/added-name.png)

Click **Add** again to open the `Add Data Field` dialog.

1. Enter the name for your second header field, `birthDate`, for example.

2. Select `date` for the `Data Type`.

3. Select `auto` for the `Setup Type` and click **Add** to create the field.

    <br>![](/exercises/ex4/images/add-birthDate.png)

Go ahead and create the list of header fields as shown in the table and image below. Pay attention to the different data types. Feel free to extend or reduce the list of fields.

|  Field Type		    |  Field Name             | Data Type     | Setup Type   
|  :------------------- |  :-------------------	  | :----------   | :----------    
|  header field         |  `name`                 | string        | auto       
|  header field         |  `birthDate`            | date          | auto
|  header field         |  `motherName`           | string        | auto           
|  header field         |  `fatherName`           | string        | auto       
|  header field         |  `registrationNumber`   | string        | auto       
             

<br>![](/exercises/ex4/images/all-fields.png)



## Exercise 4.4 Activate schema

Once you've added all fields, the schema needs to be activated so that it can be used to extract information from documents. Right now, the schema has the status `DRAFT`, indicating that it can't be used yet.

To activate the schema, click **Activate**.

<br>![](/exercises/ex4/images/activate.png)

Now, the status of your schema changes to `ACTIVE`. To make changes to your schema, you've to **Deactivate** it first.

<br>![](/exercises/ex4/images/active.png)

Congratulations, you've now created and activated your custom schema for birth certificate documents.



## Exercise 4.5 Get extraction results

1.  Access **Document** on the left navigation pane and click **+** to upload a new document.

    <br>![](/exercises/ex4/images/add-document.png)

2. On the Select Document screen, choose `Custom` for the **Document Type**.

3. Select the **Schema** you created (`birth_certificate_schema`).

4. Drop the file directly or click **+** to upload the [birth certificate](https://github.com/SAP-samples/teched2023-AI284v/blob/main/exercises/ex4/files/birth_certificate.png) sample document.

5. Click **Step 2**.

    <br>![](/exercises/ex4/images/upload.png)

6. Click **Step 3** and then click **Review**.

7. Review your selection. Click **Edit** if you want to change anything. Click **Confirm**.

    <br>![](/exercises/ex4/images/review.png)

    The document status changes from `PENDING` to `READY`.

    <br>![](/exercises/ex4/images/ready.png)

8. Click the document row and **Extraction Results** to see the information extracted from the document using LLMs and the schema you created.

    <br>![](/exercises/ex4/images/results.png)

   

## Summary

You've now successfully extracted information from a birth certificate document using the Schema Configuration feature from Document Information Extraction and LLMs.

Continue to [Exercise 5 - Process a work contract using Document Information Extraction and LLMs](../ex5/README.md).
