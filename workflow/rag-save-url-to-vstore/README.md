# Parse URL And Save To Vector Store

<p align="center">
  <img src="../../assets/img/rag_save_url_to_vstore.png" width="1200" />
</p>

## Use in GPT-DB

```bash
gptdb app install rag-save-url-to-vstore
```

Wait 10 seconds, then open the web page of GPT-DB, you will see the new AWEL flow in 
the web page.


Run `rag-save-url-to-vstore` with the following command:

```bash
gptdb run flow -n rag_save_url_to_vstore \
--messages 'https://docs.gptdb.site/docs/latest/awel/'
```

Then it will parse the URL and save the content to the vector store, and you can see the output after the flow is finished.