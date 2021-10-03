# Facturas de Debitoor a Holded

Webapp escrita en VUE para importar las facturas de Debitoor en Holded. Como el csv exportado de Debitoor no es una maravilla, consumimos la api que si tiene los datos más estructurados y limpios.

> Nota: És un proyecto personal, puede que no se adapte a todos los casos.

## Instrucciones

1. Subir a /views/json el archivo _facturas.json_ exportado desde la api de debitoor en el endpoint invoices/v8
2. Con el plugin [Downlaod table as csv](https://chrome.google.com/webstore/detail/download-table-as-csv/jgeonblahchgiadgojdjilffklaihalj) de Chrome exporto la tabla html a CSV.
3. Subir en Holded y listo
