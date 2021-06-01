## Tradesman API endpoints


### Case 1 
Wrong schedule url_key or tradesman_key provided
Type: **GET**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/111
```

Response:
Status: **404**
```
{
  "error": "Schedule or Tradesman not found."
}

```

### Case 2
Unassigned scheduled visited by tradesman that schedule was NOT sent to
Type: **GET**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/789
```

Response:
Status: **404**
```
{
  "error": "Schedule not sent to 'tradesman company name'"
}

```

### Case 3
Unassigned scheduled visited by tradesman that schedule was sent to
Type: **GET**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/111
```

Response: as  per **Case 4** except "assigned_tradesman" = 0


### Case 4
Assigned scheduled visited by approved tradesman
Type: **GET**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/123
```
Response will contain:
- schedule general data
- tradesman info - "tradesman"
- all schedule content - "contents"
- all drawings related to the schedule - "drawings"
- only quotes submitted by tradesman - "quotes":
- only invoices submitted by the tradesman - "invoices":
- only questions submitted by tradesman and related answers - "tradesman_questions" => "answers"

Response:
Status: **200**
```
{
  "id": 1,
  "ref_no": "TR_001",
  "proj_ref": "V2C9024",
  "name": "Sample",
  "content": "sample note",
  "status": "Approved",
  "status_note": "",
  "type": "Joinery",
  "sent_for_quote": "Yes",
  "approved_quote": "60",
  "approved_date": 1620999227,
  "sent_date": "2021/05/11",
  "sent_by": "Pawel",
  "sent_by_id": 0,
  "approved_by_id": 47,
  "approved_by": "Sebastian Woyno",
  "designer_id": 0,
  "designer_email": "pawel@ventura.ie",
  "completion_date": "",
  "total_cost": "",
  "url_key": "6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz",
  "assigned_tradesman": 1,
  "updated_by_id": 40,
  "updated_at": "1620887694",
  "created_at": "",
  "update_unix": 0,
  "tradesman": {
    "id": 1,
    "company": "Piu Alto",
    "name": "Brian Lenehan",
    "email": "lorraine@piualto.com",
    "phone": "",
    "url_key": "123",
    "note": "",
    "type": "Joinery"
  },
  "contents": [
    {
      "id": 2,
      "trade_order_id": 1,
      "name": "576576",
      "qty": "1",
      "text": "khjhkjhkjhkjh",
      "image": "",
      "updated_by_id": 0,
      "updated_at": 0,
      "created_at": 0,
      "image_id": 0
    },
    {
      "id": 4,
      "trade_order_id": 1,
      "name": "iuy",
      "qty": "12",
      "text": "yiuyiuy",
      "image": "",
      "updated_by_id": 47,
      "updated_at": 1620211799,
      "created_at": 1620211702,
      "image_id": 0
    },
    {
      "id": 5,
      "trade_order_id": 1,
      "name": "sample tesr",
      "qty": "1",
      "text": "dkfj\ndfgkadfjg;lkfdjghs",
      "image": "http://localhost/VERP_Light/api/public/uploads/u_1620212691_f.jpg",
      "updated_by_id": 47,
      "updated_at": 1620212774,
      "created_at": 1620212266,
      "image_id": 65
    },
    {
      "id": 11,
      "trade_order_id": 1,
      "name": "sample text",
      "qty": "1",
      "text": "",
      "image": "",
      "updated_by_id": 47,
      "updated_at": 1621061361,
      "created_at": 1621061349,
      "image_id": 0
    }
  ],
  "main_image": "http://localhost/VERP_Light/api/public/uploads/u_1620212691_f.jpg",
  "drawings": {
    "9": {
      "id": 54,
      "name": "1.png",
      "parent_id": 1,
      "unix": 1620199078,
      "path": "http://localhost/VERP_Light/api/public/uploads/u_1620199078_f.png",
      "type": "image/png",
      "fileable_id": 1,
      "fileable_type": "App\\TradeOrder",
      "document_type": "drawing",
      "document_from": "",
      "document_value": ""
    },
    "11": {
      "id": 51,
      "name": "2.png",
      "parent_id": 1,
      "unix": 1620197874,
      "path": "http://localhost/VERP_Light/api/public/uploads/u_1620197874_f.png",
      "type": "image/png",
      "fileable_id": 1,
      "fileable_type": "App\\TradeOrder",
      "document_type": "drawing",
      "document_from": "",
      "document_value": ""
    }
  },
  "quotes": {
    "3": {
      "id": 60,
      "name": "3.png",
      "parent_id": 1,
      "unix": 1620200428,
      "path": "http://localhost/VERP_Light/api/public/uploads/u_1620200428_f.png",
      "type": "image/png",
      "fileable_id": 1,
      "fileable_type": "App\\TradeOrder",
      "document_type": "quote",
      "document_from": "1",
      "document_value": ""
    },
    "4": {
      "id": 59,
      "name": "3.png",
      "parent_id": 1,
      "unix": 1620200417,
      "path": "http://localhost/VERP_Light/api/public/uploads/u_1620200417_f.png",
      "type": "image/png",
      "fileable_id": 1,
      "fileable_type": "App\\TradeOrder",
      "document_type": "quote",
      "document_from": "1",
      "document_value": ""
    }
  },
  "invoices": {
    "6": {
      "id": 57,
      "name": "3.png",
      "parent_id": 1,
      "unix": 1620199393,
      "path": "http://localhost/VERP_Light/api/public/uploads/u_1620199393_f.png",
      "type": "image/png",
      "fileable_id": 1,
      "fileable_type": "App\\TradeOrder",
      "document_type": "invoice",
      "document_from": "1",
      "document_value": ""
    }
  },
  "tradesman_questions": {
    "2": {
      "id": 3,
      "text": "",
      "file": "",
      "questionable_id": 1,
      "questionable_type": "App\\TradeOrder",
      "author_id": 47,
      "updated_at": 0,
      "created_at": 1620550086,
      "tradesman_id": 1,
      "question_author": "Piu Alto",
      "date": "2021/05/09 09:48",
      "answers": [
        {
          "id": 6,
          "text": "sample answer to pioalto",
          "file": "",
          "question_id": 3,
          "author_id": 47,
          "updated_at": 0,
          "created_at": 1621151218,
          "tradesman_id": 0,
          "class": "text_inactive",
          "author_name": "Sebastian Woyno",
          "date": "2021/05/16 08:46",
          "tradesman": null
        }
      ],
      "tradesman": {
        "id": 1,
        "company": "Piu Alto",
        "name": "Brian Lenehan",
        "email": "lorraine@piualto.com",
        "phone": "",
        "url_key": "123",
        "note": "",
        "type": "Joinery"
      }
    },
    "3": {
      "id": 2,
      "text": "sample question 2",
      "file": "",
      "questionable_id": 1,
      "questionable_type": "App\\TradeOrder",
      "author_id": 40,
      "updated_at": 0,
      "created_at": 0,
      "tradesman_id": 1,
      "question_author": "Piu Alto",
      "date": "1970/01/01 01:00",
      "answers": [
        
      ],
      "tradesman": {
        "id": 1,
        "company": "Piu Alto",
        "name": "Brian Lenehan",
        "email": "lorraine@piualto.com",
        "phone": "",
        "url_key": "123",
        "note": "",
        "type": "Joinery"
      }
    }
  }
}

```


### Case 5
Assigned scheduled visited by unapproved tradesman
Type: **GET**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/111
```

Response:
Status: **403**
```
{
  "error": "Job not available any more. Please contact designer for details."
}

```


### Case 6
Tradesman post question
Type: **POST**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/question/{url_key}/{tradesman_key}
```
Sample:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/question/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/123
```
Send data
{
    "text": "This is my question"
}

Response:
Status: **201**
POst data:
```
{
  "text": "This is my question",
  "file": "",
  "id": 6,
  "question_author": "Piu Alto",
  "date": "1970/01/01 01:00"
}

```

### Case 7
Tradesman post question with empty text field
Type: **POST**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/question/{url_key}/{tradesman_key}
```
Sample:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/question/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/123
```

Post data:
```
{
    "text": ""
}
```

Response:
Status: **422**
```
{
  "text": [
    "Required"
  ]
}

```


### Case 8
Tradesman reply to answer
Type: **POST**
URL:
```
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/{question ID}/{url_key}/{tradesman_key}

Sample:
http://st9151.ispot.cc/verp_light_test/api/public/public_tradesman/single/question/8/6wEG1GloCEhElHn5RPXL0aMOWhUwYZTz/111
```
Post data:
```
{
    "text": "sample reply"
}
```

Response:
Status: **201**
```
{
  "text": "sample reply",
  "question_id": 8,
  "tradesman_id": 4,
  "created_at": 1621239152,
  "class": "text_inactive",
  "id": 8
}
```


