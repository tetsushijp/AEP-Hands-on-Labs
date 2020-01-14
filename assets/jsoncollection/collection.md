```
{
	"info": {
		"_postman_id": "8abfc9e4-4fba-4179-81b2-9addae7f18b4",
		"name": "Streaming Ingestion Collection",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
	},
	"item": [
		{
			"name": "Step 1 : Create a data inlet",
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"type": "text",
						"value": "Bearer {{ACCESS_TOKEN}}"
					},
					{
						"key": "Cache-Control",
						"type": "text",
						"value": "no-cache"
					},
					{
						"key": "x-api-key",
						"type": "text",
						"value": "{{API_KEY}}"
					},
					{
						"key": "x-gw-ims-org-id",
						"type": "text",
						"value": "{{IMS_ORG}}"
					},
					{
						"key": "x-sandbox-name",
						"type": "text",
						"value": "prod"
					},
					{
						"key": "Content-Type",
						"type": "text",
						"value": "application/json"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"name\": \"API Stitching Data Inlet\",\r\n    \"description\": \"Merging EmailID and CRMID\",\r\n    \"sourceId\": \"postmanAPI\",\r\n    \"dataType\": \"xdm\"\r\n}"
				},
				"url": {
					"raw": "{{PLATFORM_GATEWAY}}/data/core/edge/inlet",
					"host": [
						"{{PLATFORM_GATEWAY}}"
					],
					"path": [
						"data",
						"core",
						"edge",
						"inlet"
					]
				}
			},
			"response": []
		},
		{
			"name": "Step 2: Listing of tenant Schemas",
			"request": {
				"method": "GET",
				"header": [
					{
						"key": "x-api-key",
						"value": "{{API_KEY}}"
					},
					{
						"key": "x-gw-ims-org-id",
						"value": "{{IMS_ORG}}"
					},
					{
						"key": "Authorization",
						"type": "text",
						"value": "Bearer {{ACCESS_TOKEN}}"
					},
					{
						"key": "Accept",
						"value": "application/vnd.adobe.xed-id+json",
						"disabled": true
					},
					{
						"key": "Accept",
						"type": "text",
						"value": "application/vnd.adobe.xed-full+json"
					},
					{
						"key": "Accept",
						"type": "text",
						"value": "application/vnd.adobe.xed-notext+json; version=1",
						"disabled": true
					},
					{
						"key": "Accept",
						"type": "text",
						"value": "application/vnd.adobe.xed-full-notext+json; version=1",
						"disabled": true
					},
					{
						"key": "Accept",
						"type": "text",
						"value": "application/vnd.adobe.xed-full-desc+json; version=1",
						"disabled": true
					}
				],
				"url": {
					"raw": "{{PLATFORM_GATEWAY}}/data/foundation/schemaregistry/tenant/schemas?properties=id,title,description,meta:altId,meta:extends,meta:class,meta:tenantNamespace,meta:immutableTags",
					"host": [
						"{{PLATFORM_GATEWAY}}"
					],
					"path": [
						"data",
						"foundation",
						"schemaregistry",
						"tenant",
						"schemas"
					],
					"query": [
						{
							"key": "properties",
							"value": "id,title,description,meta:altId,meta:extends,meta:class,meta:tenantNamespace,meta:immutableTags"
						}
					]
				},
				"description": "/data/foundation/schemaregistry/{containerId}/{classes|datatypes|schemas|mixins}/\n\ncontainerId = <global> or <tenant>\n\nFilter options:\nproperty=meta:extends==https://ns.adobe.com/xdm/context/record"
			},
			"response": []
		},
		{
			"name": "Step 3 : Create a dataset",
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"type": "text",
						"value": "Bearer {{ACCESS_TOKEN}}"
					},
					{
						"key": "Cache-Control",
						"type": "text",
						"value": "no-cache"
					},
					{
						"key": "x-api-key",
						"type": "text",
						"value": "{{API_KEY}}"
					},
					{
						"key": "x-gw-ims-org-id",
						"type": "text",
						"value": "{{IMS_ORG}}"
					},
					{
						"key": "x-sandbox-name",
						"type": "text",
						"value": "prod"
					},
					{
						"key": "Content-Type",
						"type": "text",
						"value": "application/json"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"name\": \"Streaming Ingestion CRM Dataset\",\r\n    \"description\": \"Streaming Ingestion CRM Dataset\",\r\n    \"schemaRef\": {\r\n        \"id\": \"https://ns.adobe.com/adobeamericaspot1/schemas/e4a8337b7948d0b1963d19702ffcdade\",\r\n        \"contentType\": \"application/vnd.adobe.xed-full+json;version=1\"\r\n    },\r\n    \"fileDescription\": {\r\n        \"persisted\": true,\r\n        \"containerFormat\": \"parquet\",\r\n        \"format\": \"parquet\"\r\n    },\r\n    \"streamingIngestionEnabled\": \"true\",\r\n    \"tags\": {\r\n        \"unifiedIdentity\": [\"enabled:true\"],\r\n        \"unifiedProfile\": [\"enabled:true\"]\r\n    }\r\n}"
				},
				"url": {
					"raw": "{{PLATFORM_GATEWAY}}/data/foundation/catalog/dataSets",
					"host": [
						"{{PLATFORM_GATEWAY}}"
					],
					"path": [
						"data",
						"foundation",
						"catalog",
						"dataSets"
					]
				}
			},
			"response": []
		},
		{
			"name": "UPS - GET Profile by Entity ID & NS Before",
			"request": {
				"method": "GET",
				"header": [
					{
						"key": "x-api-key",
						"value": "{{API_KEY}}"
					},
					{
						"key": "x-gw-ims-org-id",
						"value": "{{IMS_ORG}}"
					},
					{
						"key": "Authorization",
						"value": "Bearer {{ACCESS_TOKEN}}"
					}
				],
				"url": {
					"raw": "https://platform.adobe.io/data/core/ups/access/entities?entityId=crmid:9692348216&entityIdNS=crmid&schema.name=_xdm.context.profile",
					"protocol": "https",
					"host": [
						"platform",
						"adobe",
						"io"
					],
					"path": [
						"data",
						"core",
						"ups",
						"access",
						"entities"
					],
					"query": [
						{
							"key": "entityId",
							"value": "crmid:9692348216"
						},
						{
							"key": "entityIdNS",
							"value": "crmid"
						},
						{
							"key": "schema.name",
							"value": "_xdm.context.profile"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Step 4 : Call Data inlet",
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Cache-Control",
						"type": "text",
						"value": "no-cache"
					},
					{
						"key": "x-sandbox-name",
						"type": "text",
						"value": "prod"
					},
					{
						"key": "Content-Type",
						"type": "text",
						"value": "application/json"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"header\": {\r\n        \"schemaRef\": {\r\n            \"id\": \"https://ns.adobe.com/adobeamericaspot2/schemas/87724b969149fa2a1d128cfbb2c6aa8c\",\r\n            \"contentType\": \"application/vnd.adobe.xed-full+json;version=1\"\r\n        },\r\n        \"imsOrgId\": \"{{IMS_ORG}}\",\r\n        \"source\": {\r\n            \"name\": \"GettingStarted\"\r\n        },\r\n        \"datasetId\": \"5e1c5e604facb018a83c6004\"\r\n    },\r\n    \"body\": {\r\n        \"xdmMeta\": {\r\n            \"schemaRef\": {\r\n                \"id\": \"https://ns.adobe.com/adobeamericaspot2/schemas/87724b969149fa2a1d128cfbb2c6aa8c\",\r\n                \"contentType\": \"application/vnd.adobe.xed-full+json;version=1\"\r\n            }\r\n        },\r\n        \"xdmEntity\": {\r\n        \t\"_adobeamericaspot2\":{\r\n        \t\t\"crmId\":\"crmid:9692348216\",\r\n        \t\t\"emailId\":\"spestridge2@mac.com\"\r\n        \t}\r\n        }\r\n    }\r\n}"
				},
				"url": {
					"raw": "https://dcs.adobedc.net/collection/d5ad5d2cb2fd4e18c23ea510ce2841d5d2c1a43fab8e9110075dea7e444f4154?synchronousValidation=true",
					"protocol": "https",
					"host": [
						"dcs",
						"adobedc",
						"net"
					],
					"path": [
						"collection",
						"d5ad5d2cb2fd4e18c23ea510ce2841d5d2c1a43fab8e9110075dea7e444f4154"
					],
					"query": [
						{
							"key": "synchronousValidation",
							"value": "true"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "UPS - GET Profile by Entity ID & NS After",
			"request": {
				"method": "GET",
				"header": [
					{
						"key": "x-api-key",
						"value": "{{API_KEY}}"
					},
					{
						"key": "x-gw-ims-org-id",
						"value": "{{IMS_ORG}}"
					},
					{
						"key": "Authorization",
						"value": "Bearer {{ACCESS_TOKEN}}"
					}
				],
				"url": {
					"raw": "https://platform.adobe.io/data/core/ups/access/entities?entityId=crmid:5322492008&entityIdNS=crmid&schema.name=_xdm.context.profile",
					"protocol": "https",
					"host": [
						"platform",
						"adobe",
						"io"
					],
					"path": [
						"data",
						"core",
						"ups",
						"access",
						"entities"
					],
					"query": [
						{
							"key": "entityId",
							"value": "crmid:5322492008"
						},
						{
							"key": "entityIdNS",
							"value": "crmid"
						},
						{
							"key": "schema.name",
							"value": "_xdm.context.profile"
						}
					]
				}
			},
			"response": []
		}
	],
	"protocolProfileBehavior": {}
}
```
