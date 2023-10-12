# Exercise 2 - Process a receipt using Document Information Extraction and LLMs

In this exercise, you'll extract information from a custom document - in this case, a lunch receipt. The Document Information Extraction service doesn't support custom document types out of the box. So, you'll create a custom schema to define the fields that you want to extract from a receipt document using LLMs (Large Language Models).

## Exercise 2.1 Create schema

1. Open the Document Information Extraction application, as described in the tutorial: [Use Trial to Set Up Account for Document Information Extraction and Go to Application](https://developers.sap.com/tutorials/cp-aibus-dox-booster-app.html).

2. To access the schema configuration feature, click the wheels icon and choose **Schema Configuration**.

    <br>![](/exercises/ex2/images/access-schema-configuration.png)

3. To create your own schema, click **Create** and a dialog opens.

    <br>![](/exercises/ex2/images/create-schema.png)

4. In the dialog, enter a name for your custom schema, `receipt_schema`, for example. Note that the name can't include blanks. Further, select `Custom` as your **Document Type** and `Document` for **OCR Engine Type**.

5. Click **Create** to create the schema.

    <br>![](/exercises/ex2/images/create-schema-dialog.png)

Now, your schema shows up in the list. 

6. Access the schema by clicking on it.

    <br>![](/exercises/ex2/images/access-schema.png)



## Exercise 2.2 Add data fields

To add your first header field, click **Add**.

<br>![](/exercises/ex2/images/add-field.png)

For each custom field, you've to enter name and data type. The available data types are `string`, `number`, `date`, `discount`, `currency`, and `country/region`. Default extractors aren't available for custom documents. Adding a description is optional.

As your first header field, add the vendor name of your receipt.

1. Enter the name for your field, `vendorName`, for example.

2. Select `string` for the `Data Type`.

3. Select `auto` for the `Setup Type` and click **Add** to create the header field. Note that when you use the setup type `auto` without a default extractor, LLMs are then used to extract the information from the document.

    <br>![](/exercises/ex2/images/add-name.png)

The field now displays in your list of header fields, where you again find all the information that you've just entered. You can edit or delete the field by clicking the respective icons on the right.

<br>![](/exercises/ex2/images/added-name.png)

Click **Add** again to open the `Add Data Field` dialog.

1. Enter the name for your second header field, `vendorAddress`, for example.

2. Select `string` for the `Data Type`.

3. Select `auto` for the `Setup Type` and click **Add** to create the field.

    <br>![](/exercises/ex2/images/add-address.png)

Go ahead and create the list of header fields and line item fields as shown in the table and image below. Pay attention to the different data types and that the last two fields are line item fields (not header fields). Feel free to extend or reduce the list of fields.

|  Field Type		|  Field Name           | Data Type     | Setup Type   
|  :------------------- |  :-------------------	| :----------   | :----------    
|  header field         |  `vendorName`         | string        | auto       
|  header field         |  `vendorAddress`      | string        | auto
|  header field         |  `currency`           | currency      | auto           
|  line item field      |  `description`        | string        | auto       
|  line item field      |  `amount`             | number        | auto       
             

<br>![](/exercises/ex2/images/all-fields.png)



## Exercise 2.3 Activate schema

Once you've added all fields, the schema needs to be activated so that it can be used to extract information from documents. Right now, the schema has the status `DRAFT`, indicating that it can't be used yet.

To activate the schema, click **Activate**.

<br>![](/exercises/ex2/images/activate.png)

Now, the status of your schema changes to `ACTIVE`. To make changes to your schema, you've to **Deactivate** it first.

<br>![](/exercises/ex2/images/active.png)

Congratulations, you've now created and activated your custom schema for receipt documents.



## Exercise 2.4 Get extraction results

1.  Access **Document** on the left navigation pane and click **+** to upload a new document.

    <br>![](/exercises/ex2/images/add-document.png)

2. On the Select Document screen, choose `Custom` for the **Document Type**.

3. Select the **Schema** you created (`receipt_schema`).

4. Drop the file directly or click **+** to upload the [receipt](https://github.com/SAP-samples/teched2023-AI284v/blob/main/exercises/ex2/files/receipt.jpg) sample document ([source](https://en.wikipedia.org/wiki/Receipt#/media/File:ReceiptSwiss.jpg) and [license terms](https://creativecommons.org/licenses/by-sa/3.0/)).

5. Click **Step 2**.

    <br>![](/exercises/ex2/images/upload.png)

6. Click **Step 3** and then click **Review**.

7. Review your selection. Click **Edit** if you want to change anything. Click **Confirm**.

    <br>![](/exercises/ex2/images/review.png)

    The document status changes from `PENDING` to `READY`.

    <br>![](/exercises/ex2/images/ready.png)

8. Click the document row and **Extraction Results** to see the information extracted from the document using LLMs and the schema you created.

    <br>![](/exercises/ex2/images/results.png)



## Summary

You've now successfully extracted information from a receipt document using the Schema Configuration feature from Document Information Extraction and LLMs.

Continue to [Exercise 3 - Process a résumé using Document Information Extraction and LLMs](../ex3/README.md).
