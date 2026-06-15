# Steps


1. Build storage containers for **each** layer (an extra container named *landing* is used to facilitate the data ingestion pipeline, as well as imitate a file store)

<img width="868" height="231" alt="{F5BF66F8-939A-43AA-B9F8-876BF765A870}" src="https://github.com/user-attachments/assets/9d090575-d54f-4c9d-baa4-828c3a3d16f1" />

----

2. Upload the dataset from your local file store to the *landing* container in the cloud.

<img width="1018" height="313" alt="{B077538E-911F-447B-B57D-E83880DB1E68}" src="https://github.com/user-attachments/assets/351c9a0c-ea25-4ec5-a70a-adc2946f2775" />

----

3. In Azure Data Factory, create a **Linked Service** connecting our storage accounts to our data factory. 

<img width="435" height="258" alt="{00701EA4-5352-4D8B-A31D-216D4CD9A68F}" src="https://github.com/user-attachments/assets/70831f3e-ada1-418f-988c-d0ed07a393dd" />

----

4. Create *Source* and *Sink* datasets for the pipeline. The Source dataset has it's filepath set as the directory of the **landing** container, while the sink dataset's filepath is set as the **bronze** container.

<img width="737" height="133" alt="{A65BC946-8B02-40D5-94B3-F5FB30A0AE47}" src="https://github.com/user-attachments/assets/0f504020-69ed-4758-a91d-a5206a06a685" />



<img width="735" height="136" alt="{D0BBBCD2-2482-48BB-9C7C-CDEEA1153997}" src="https://github.com/user-attachments/assets/459eceee-57ea-44d2-ab08-a620d828737b" />

----

5. Configure our pipeline, set our sink and source datasets we created earlier.

<img width="500" height="296" alt="{F9A9735D-A687-4F64-A4D4-9CEB6663EED2}" src="https://github.com/user-attachments/assets/f2a8c62e-b3bc-41b5-9647-30b321cb685c" />

----

6. Validate our pipeline and trigger a run.

<img width="828" height="204" alt="{D298FFFF-AC1E-4C7E-9FE1-88A79F77C053}" src="https://github.com/user-attachments/assets/b9198b34-81df-4135-a685-06e4b131b9b8" />

----

7. Check the **bronze** container to verify our pipeline run.

<img width="1006" height="280" alt="{E91D5FA8-C7E0-4A75-B219-1967A7CFBF6A}" src="https://github.com/user-attachments/assets/8b275ad5-47eb-41d6-8795-9a8ba3b0f62a" />

----

### Bronze Layer is successfully built.
