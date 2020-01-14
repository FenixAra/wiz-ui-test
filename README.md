# wiz-ui-test

## Get Schedules

URL: https://staging-api.wizfreight.com/v1/schedules/list

Method: PORT

### Request
```
{
	"type": "FCL",
	"origin": "{port-uuid}",
	"destination": "{port-uuid}",
	"date": "{date in rfc3339 format}",
	"container_no": 10
}
```

### Response
Status Code: 200
```
{
    "schedules": [
        {
            "id": "51fc6253-ca4b-4fad-8f26-c1ac1c883f2f",
            "waypoints": [
                {
                    "port": {
                        "id": "3f068cf7-727b-4bac-bc76-7ba6cd17af7c",
                        "name": "Chennai"
                    },
                    "date": "18th Aug"
                },
                {
                    "port": {
                        "id": "64df1168-bacf-4d25-a3ea-ceb30a3ccfed",
                        "name": "Dubai"
                    },
                    "date": "28th Aug"
                }
            ],
            "transit_days": 10,
            "liner": {
                "id": "08451516-ad32-48f1-8f91-0542365a0133",
                "name": "Maersk"
            },
            "price": {
                "total": 1800,
                "currency": "USD"
            }
        },
        {
            "id": "51fc6253-ca4b-4fad-8f26-c1ac1c883f2f",
            "waypoints": [
                {
                    "port": {
                        "id": "3f068cf7-727b-4bac-bc76-7ba6cd17af7c",
                        "name": "Chennai"
                    },
                    "date": "12th Oct"
                },
                {
                    "port": {
                        "id": "64df1168-bacf-4d25-a3ea-ceb30a3ccfed",
                        "name": "Dubai"
                    },
                    "date": "28th Oct"
                }
            ],
            "transit_days": 16,
            "liner": {
                "id": "08451516-ad32-48f1-8f91-0542365a0133",
                "name": "MSC Liners"
            },
            "price": {
                "total": 2800,
                "currency": "USD"
            }
        },
        {
            "id": "51fc6253-ca4b-4fad-8f26-c1ac1c883f2f",
            "waypoints": [
                {
                    "port": {
                        "id": "3f068cf7-727b-4bac-bc76-7ba6cd17af7c",
                        "name": "Chennai"
                    },
                    "date": "11th Jan"
                },
                {
                    "port": {
                        "id": "64df1168-bacf-4d25-a3ea-ceb30a3ccfed",
                        "name": "Dubai"
                    },
                    "date": "15th Jan"
                }
            ],
            "transit_days": 4,
            "liner": {
                "id": "08451516-ad32-48f1-8f91-0542365a0133",
                "name": "Maersk"
            },
            "price": {
                "total": 8800,
                "currency": "USD"
            }
        }
    ]
}
```

## Get Fare estimates

URL: https://staging-api.wizfreight.com/v1/estimate

Method: POST

### Request
```
{
	"schedule_id": "{schedule uuid selected}",
	"container_type": "{container_type}",
	"number_of_containers": 10,
	"incoterm": "{incoterm}",
	"packages":[{
			"hs_code": "{hscode}",
			"cargo_name": "{cargo_name}",
			"packaging_type": "{package_type}",
			"quantity": 10,
			"dimension": {
				"length": 1.1,
				"width": 1.2,
				"height": 1.1,
				"weight": 12
			}
		}]
}
```

### Response
Status Code: 200
```
{
    "freigt_charges": 2400,
    "bill_of_lading": 2600,
    "terminal_handling_charges": 2400,
    "insurance": 200,
    "tax": 4000,
    "total": 11600
}
```

## Create a new booking
URL: https://staging-api.wizfreight.com/v1/bookings

Method: POST

### Request
```
{
	"schedule_id": "{schedule uuid selected}",
	"container_type": "{container_type}",
	"number_of_containers": 10,
	"incoterm": "{incoterm}",
	"packages":[{
			"hs_code": "{hscode}",
			"cargo_name": "{cargo_name}",
			"packaging_type": "{package_type}",
			"quantity": 10,
			"dimension": {
				"length": 1.1,
				"width": 1.2,
				"height": 1.1,
				"weight": 12
			}
		}]
}
```

### Response
Status Code: 200
```
{
    "status": true
}
```

## Get container types

URL: https://staging-api.wizfreight.com/v1/assets/containers/types

Method: GET

### Response
Status Code: 200
```
[
    {
        "id": "f32f769d-0bf4-4b6e-b5f3-588646dae67a",
        "name": "20 ft, Flat Rack"
    },
    {
        "id": "f185b5db-5bb6-4ae8-b811-f12a24462c7b",
        "name": "20 ft, ISO Tank"
    },
    {
        "id": "8c387826-c7f9-48c8-b25c-516364040b6c",
        "name": "20 ft, Open Top"
    },
    {
        "id": "3f9a0373-925b-4b5d-a68f-7e6c3c576c23",
        "name": "20 ft, Reefer"
    },
    {
        "id": "ec4b331f-553e-49ef-9a1d-8aa743e4dec6",
        "name": "20 ft, Standard"
    },
    {
        "id": "35a89c76-3488-45cd-9ad1-ae17a5dc8bac",
        "name": "40 ft, Flat Rack"
    },
    {
        "id": "dd207c1e-d684-428e-b0c8-3e1b42291531",
        "name": "40 ft, ISO Tank"
    },
    {
        "id": "8568622a-01ee-42dd-a22e-95f340f5c509",
        "name": "40 ft, Open Top"
    },
    {
        "id": "f7e817c9-3406-4b8a-b603-cd1f0a002c87",
        "name": "40 ft, Reefer"
    },
    {
        "id": "d5f4a993-c583-4946-843d-5bcbbda8cd22",
        "name": "40 ft, Standard"
    },
    {
        "id": "afc1042d-b626-4c99-9b60-07c4ec582749",
        "name": "40 HC, Flat Rack"
    },
    {
        "id": "34d7b345-e6b4-4ea2-8414-8581c1db41f0",
        "name": "40 HC, ISO Tank"
    },
    {
        "id": "ce069f78-d4da-4996-a80f-4024f3709f5e",
        "name": "40 HC, Open Top"
    },
    {
        "id": "2cc28577-a9fb-40e0-92a4-b41550f49075",
        "name": "40 HC, Reefer"
    },
    {
        "id": "eb961f12-fdb8-4d2f-a2e3-3195f0673e0e",
        "name": "40 HC, Standard"
    },
    {
        "id": "e6dc05b1-4f61-49a9-b34e-b1c74a7641c1",
        "name": "45 HC, Flat Rack"
    },
    {
        "id": "c7d938c9-0c9d-4575-9ee9-200f74a7cde2",
        "name": "45 HC, ISO Tank"
    },
    {
        "id": "aa52b023-8a2a-4570-86cd-23d167f6acc8",
        "name": "45 HC, Open Top"
    },
    {
        "id": "b6eb22d8-13ad-4e72-87db-38d382754776",
        "name": "45 HC, Reefer"
    },
    {
        "id": "52835aea-45ba-46b5-8b70-b8d44cd35d02",
        "name": "45 HC, Standard"
    }
]
```

## Get incoterm list

URL: https://staging-api.wizfreight.com/v1/assets/incoterms/list

Method: GET

### Response
Status Code: 200
```
[
    {
        "id": "5e1b2885-85df-4150-bde7-6cada3f5f0d1",
        "name": "CIF"
    },
    {
        "id": "6e0249d2-a619-464f-a43d-07aa6623f68e",
        "name": "CFR"
    },
    {
        "id": "9535665c-afe2-4c32-a398-db7b99d12041",
        "name": "CPT"
    },
    {
        "id": "5ed52105-6a91-4ed6-ac43-30ba3910580a",
        "name": "CIP"
    },
    {
        "id": "39af7311-3bbd-411d-9120-2176b9a539db",
        "name": "DAT"
    },
    {
        "id": "730fe43c-9cf9-4ad9-b4d3-ccac52dfee70",
        "name": "DAP"
    },
    {
        "id": "8d8c94dd-8d75-4c18-b70e-d7edabc11319",
        "name": "DDP"
    },
    {
        "id": "874095b4-6957-4ee2-abf2-c1cb0109d511",
        "name": "EXW"
    },
    {
        "id": "09252ee9-5735-4419-b205-608492f6ef17",
        "name": "FCA"
    },
    {
        "id": "6753aade-a3c4-49e7-add9-763be3b6ce2c",
        "name": "FOB"
    },
    {
        "id": "19646522-56ba-4f5d-aae2-e871446ddca9",
        "name": "FAS"
    }
]
```
