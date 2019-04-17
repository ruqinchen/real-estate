---
name: Event Types


---
# Event Types

### NOTE

Events are wrapped by a Notification object:

```json
{
  "type": "Notification",
  "id": "https://you.example.com/inbox/12345",
  "timestamp": 1550503972767,
  "agent": "https://user.example.com/profile/card#me",
  "instrument": "https://application.example.com/profile/card#me",
  "object": {
    "type": "Action",
    "topic": [ "profile:read" ]
    }
  }
```



## OfferAction

an offer to buy/bid on a property is made


```json
{
  "type": "OfferAction",
  "agent": {
    "type": "Person",
    "name": "Bob",
    "email": "bob@example.com"
  },
  "object": {
    "type": "RealEstateListing",
    "id": "http://example.com/12345"
  },
  "additionalProperty": {
    "@context": "https://application.example.com/context#",
    "customProp": "custom-prop-value"
  },
  "identifier": {
    "@context": "http://example.com/context#",
    "ID": "value"
  },
  "recipient": {
    "id": "http://user.example.com/profile/card#me"
  },
  "offerPrice": {
    "type": "PriceSpecification",
    "minPrice": 0,
    "maxPrice": 0,
    "price": 0,
    "priceCurrency": "USD"
  }
}
```

#### OfferAction properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | OfferAction  |
| agent | object | the agent making the offer <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | reference to the item on which the offer is being made <br/>RANGE: [string](/schemas#string),[Thing](/schemas#thing) |
| additionalProperty | object | Property names and values are only valid in the provided `@context`.  For example if `@context http://example.com/context#`. the property with key `ID` should be represented locally as `http;//example.com/context#ID`  |
| identifier | object | a key value map of **namespaced** unique identifiers.  |
| recipient | object | the offer recipient <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization) |
| offerPrice | object | describes the price offered <br/>RANGE: [PriceSpecification](/schemas#pricespecification) |

## MarketingProgramCreate

a MarketingProgram was created


```json
{
  "type": "CreateAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "MarketingProgram",
    "id": "https://example.com/collection/1",
    "name": "Market Report 1008 Mountain Gate Road",
    "description": "Dolor accusamus rerum nemo non omnis. Nam labore pariatur eius omnis sit.",
    "creator": "http://user.example.com/profile/card",
    "dateCreated": "2019-04-14T10:08:56Z",
    "dateModified": "2019-04-14T10:08:56Z",
    "member": [
      "https://user.example.com/profile/card"
    ]
  }
}
```

#### MarketingProgramCreate properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | CreateAction  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |

## EmailAction

an EmailMessage was sent


```json
{
  "type": "EmailAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "EmailMessage",
    "id": "https://example.com/collection/1",
    "name": "Market Report 1008 Mountain Gate Road",
    "description": "Dolor accusamus rerum nemo non omnis. Nam labore pariatur eius omnis sit.",
    "creator": "http://user.example.com/profile/card",
    "dateCreated": "2019-04-14T10:08:56Z",
    "dateModified": "2019-04-14T10:08:56Z",
    "toRecipient": [
      "user@example.com"
    ],
    "ccRecipient": [
      "user@example.com"
    ],
    "bccRecipient": [
      "user@example.com"
    ],
    "dateSent": "2019-04-14T10:08:56Z",
    "dateRead": "2019-04-14T10:08:56Z",
    "sender": "http://user.example.com/profile/card",
    "messageAttachment": [
      {
        "type": "DigitalDocument",
        "id": "http://user.example.com/public/logo/fileName.zip",
        "name": "fileName.zip",
        "encodingFormat": "application/zip",
        "identifier": {},
        "about": "http://user.example.com/profile/card#me"
      }
    ]
  }
}
```

#### EmailAction properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | EmailAction  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |

## MarketingProgramMemberAdd

a program member was added by the agent (Work In Progress)


```json
{
  "type": "MarketingProgramMemberAdd",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "Person",
    "id": "https://example.com/collection/1",
    "name": "string",
    "givenName": "Bruce",
    "familyName": "Wayne",
    "jobTitle": "Jefe",
    "email": "user@example.com",
    "faxNumber": "(498) 625-6456",
    "telephone": "1-339-041-0306 x2866",
    "contactPoint": [
      {
        "type": "ContactPoint",
        "name": "Work",
        "telephone": "1-364-127-9618 x20418",
        "faxNumber": "834.320.1602",
        "email": "user@example.com",
        "url": "https://www.facebook.com/hallandoates"
      }
    ],
    "address": [
      {
        "type": "PostalAddress",
        "streetAddress": "1007 Mountain Gate Rd",
        "postOfficeBoxNumber": "Box 1234",
        "addressRegion": "New Jersey",
        "addressLocality": "Gotham City",
        "postalCode": "10010"
      }
    ],
    "birthDate": "2019-04-14"
  },
  "topic": [
    "marketing"
  ],
  "targetCollection": "http://example.com"
}
```

#### MarketingProgramMemberAdd properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | MarketingProgramMemberAdd  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | * |   |
| targetCollection | string&lt;uri&gt; | ref to the marketing program receiving the new member <br/>RANGE: [ProgramMembership](/schemas#programmembership) |

## MarketingProgramMemberRemove

a member was removed by the agent (Work In Progress)


```json
{
  "type": "MarketingProgramMemberRemove",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "Person",
    "id": "https://example.com/collection/1",
    "name": "string",
    "givenName": "Bruce",
    "familyName": "Wayne",
    "jobTitle": "Jefe",
    "email": "user@example.com",
    "faxNumber": "(498) 625-6456",
    "telephone": "1-339-041-0306 x2866",
    "contactPoint": [
      {
        "type": "ContactPoint",
        "name": "Work",
        "telephone": "1-364-127-9618 x20418",
        "faxNumber": "834.320.1602",
        "email": "user@example.com",
        "url": "https://www.facebook.com/hallandoates"
      }
    ],
    "address": [
      {
        "type": "PostalAddress",
        "streetAddress": "1007 Mountain Gate Rd",
        "postOfficeBoxNumber": "Box 1234",
        "addressRegion": "New Jersey",
        "addressLocality": "Gotham City",
        "postalCode": "10010"
      }
    ],
    "birthDate": "2019-04-14"
  },
  "topic": [
    "marketing"
  ],
  "targetCollection": "http://example.com"
}
```

#### MarketingProgramMemberRemove properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | MarketingProgramMemberRemove  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | * |   |
| targetCollection | string&lt;uri&gt; | ref to the marketing program receiving the new member <br/>RANGE: [ProgramMembership](/schemas#programmembership) |

## profile_added

a profile (agent, affiliate or office) was created


```json
{
  "topic": [
    "profile:read"
  ],
  "type": "AddAction",
  "object": {
    "id": "https://user.example.com/profile/card#me",
    "type": "RealEstateAgent"
  }
}
```
#### profile_added properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | [Profile](/schemas#profile) | the profile object <br/>RANGE: [RealEstateAgent](/schemas#realestateagent),[RealEstateOffice](/schemas#realestateoffice),[RealEstateOrganization](/schemas#realestateorganization) |

## profile_updated

a profile (agent, affiliate or office) was updated


```json
{
  "topic": [
    "profile:read"
  ],
  "type": "UpdateAction",
  "object": {
    "id": "https://user.example.com/profile/card#me",
    "type": "RealEstateAgent"
  }
}
```
#### profile_updated properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | UpdateAction  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | [Profile](/schemas#profile) | the updated profile object <br/>RANGE: [RealEstateAgent](/schemas#realestateagent),[RealEstateOffice](/schemas#realestateoffice),[RealEstateOrganization](/schemas#realestateorganization) |

## contact_added

a contact was created


```json
{
  "type": "AddAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "Person",
    "id": "https://example.com/collection/1",
    "name": "string",
    "givenName": "Bruce",
    "familyName": "Wayne",
    "jobTitle": "Jefe",
    "email": "user@example.com",
    "faxNumber": "(498) 625-6456",
    "telephone": "1-339-041-0306 x2866",
    "contactPoint": [
      {
        "type": "ContactPoint",
        "name": "Work",
        "telephone": "1-364-127-9618 x20418",
        "faxNumber": "834.320.1602",
        "email": "user@example.com",
        "url": "https://www.facebook.com/hallandoates"
      }
    ],
    "address": [
      {
        "type": "PostalAddress",
        "streetAddress": "1007 Mountain Gate Rd",
        "postOfficeBoxNumber": "Box 1234",
        "addressRegion": "New Jersey",
        "addressLocality": "Gotham City",
        "postalCode": "10010"
      }
    ],
    "birthDate": "2019-04-14",
    "leadSource": {
      "type": "Organization",
      "id": "https://example.com/collection/1",
      "name": "string",
      "telephone": "079.706.7065 x6341",
      "faxNumber": "(873) 271-4802",
      "email": "user@example.com",
      "url": "http://example.com",
      "availableLanguage": [
        {
          "type": "Language",
          "name": "English",
          "additionalName": "en"
        }
      ],
      "branchCode": "CA301-001",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "logo": [
        {
          "type": "DigitalDocument",
          "id": "http://user.example.com/public/logo/fileName.zip",
          "name": "fileName.zip",
          "encodingFormat": "application/zip",
          "identifier": {},
          "about": "http://user.example.com/profile/card#me"
        }
      ],
      "image": [
        {
          "type": "ImageObject",
          "id": "http://user.example.com/public/logo/image.jpg",
          "name": "image.jpg",
          "encodingFormat": "image/jpeg",
          "content": "string",
          "about": "http://user.example.com/profile/card#me",
          "url": "http://user.example.com/public/profile/image.jpg"
        }
      ],
      "parentOrganization": [
        "http://example.com"
      ]
    }
  },
  "topic": [
    "contact"
  ]
}
```

#### contact_added properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a contact  |
| topic | * |   |

## contact_updated

a crm contact was updated


```json
{
  "type": "UpdateAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "Person",
    "id": "https://example.com/collection/1",
    "name": "string",
    "givenName": "Bruce",
    "familyName": "Wayne",
    "jobTitle": "Jefe",
    "email": "user@example.com",
    "faxNumber": "(498) 625-6456",
    "telephone": "1-339-041-0306 x2866",
    "contactPoint": [
      {
        "type": "ContactPoint",
        "name": "Work",
        "telephone": "1-364-127-9618 x20418",
        "faxNumber": "834.320.1602",
        "email": "user@example.com",
        "url": "https://www.facebook.com/hallandoates"
      }
    ],
    "address": [
      {
        "type": "PostalAddress",
        "streetAddress": "1007 Mountain Gate Rd",
        "postOfficeBoxNumber": "Box 1234",
        "addressRegion": "New Jersey",
        "addressLocality": "Gotham City",
        "postalCode": "10010"
      }
    ],
    "birthDate": "2019-04-14",
    "leadSource": {
      "type": "Organization",
      "id": "https://example.com/collection/1",
      "name": "string",
      "telephone": "079.706.7065 x6341",
      "faxNumber": "(873) 271-4802",
      "email": "user@example.com",
      "url": "http://example.com",
      "availableLanguage": [
        {
          "type": "Language",
          "name": "English",
          "additionalName": "en"
        }
      ],
      "branchCode": "CA301-001",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "logo": [
        {
          "type": "DigitalDocument",
          "id": "http://user.example.com/public/logo/fileName.zip",
          "name": "fileName.zip",
          "encodingFormat": "application/zip",
          "identifier": {},
          "about": "http://user.example.com/profile/card#me"
        }
      ],
      "image": [
        {
          "type": "ImageObject",
          "id": "http://user.example.com/public/logo/image.jpg",
          "name": "image.jpg",
          "encodingFormat": "image/jpeg",
          "content": "string",
          "about": "http://user.example.com/profile/card#me",
          "url": "http://user.example.com/public/profile/image.jpg"
        }
      ],
      "parentOrganization": [
        "http://example.com"
      ]
    }
  },
  "topic": "contact"
}
```

#### contact_updated properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | UpdateAction  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a contact  |
| topic | * |   |

## contact_removed

a crm contact was removed


```json
{
  "type": "RemoveAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "Person",
    "id": "https://example.com/collection/1",
    "name": "string",
    "givenName": "Bruce",
    "familyName": "Wayne",
    "jobTitle": "Jefe",
    "email": "user@example.com",
    "faxNumber": "(498) 625-6456",
    "telephone": "1-339-041-0306 x2866",
    "contactPoint": [
      {
        "type": "ContactPoint",
        "name": "Work",
        "telephone": "1-364-127-9618 x20418",
        "faxNumber": "834.320.1602",
        "email": "user@example.com",
        "url": "https://www.facebook.com/hallandoates"
      }
    ],
    "address": [
      {
        "type": "PostalAddress",
        "streetAddress": "1007 Mountain Gate Rd",
        "postOfficeBoxNumber": "Box 1234",
        "addressRegion": "New Jersey",
        "addressLocality": "Gotham City",
        "postalCode": "10010"
      }
    ],
    "birthDate": "2019-04-14",
    "leadSource": {
      "type": "Organization",
      "id": "https://example.com/collection/1",
      "name": "string",
      "telephone": "079.706.7065 x6341",
      "faxNumber": "(873) 271-4802",
      "email": "user@example.com",
      "url": "http://example.com",
      "availableLanguage": [
        {
          "type": "Language",
          "name": "English",
          "additionalName": "en"
        }
      ],
      "branchCode": "CA301-001",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "logo": [
        {
          "type": "DigitalDocument",
          "id": "http://user.example.com/public/logo/fileName.zip",
          "name": "fileName.zip",
          "encodingFormat": "application/zip",
          "identifier": {},
          "about": "http://user.example.com/profile/card#me"
        }
      ],
      "image": [
        {
          "type": "ImageObject",
          "id": "http://user.example.com/public/logo/image.jpg",
          "name": "image.jpg",
          "encodingFormat": "image/jpeg",
          "content": "string",
          "about": "http://user.example.com/profile/card#me",
          "url": "http://user.example.com/public/profile/image.jpg"
        }
      ],
      "parentOrganization": [
        "http://example.com"
      ]
    }
  },
  "topic": "contact"
}
```

#### contact_removed properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a contact  |
| topic | string |   |

## CommentAction

a comment was created by the agent about a subject &#x60;about&#x60;


```json
{
  "type": "CommentAction",
  "agent": {
    "type": "Person",
    "name": "Charlie Commentor"
  },
  "object": {
    "type": "Comment",
    "id": "https://example.com/collection/1",
    "about": "http://user.example.com/profile/card#me",
    "text": "Commodi ratione vel qui ullam ea ut."
  },
  "topic": [
    "contact"
  ]
}
```

#### CommentAction properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | CommentAction  |
| agent | object | the commentor <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | A comment on an item.  |
| topic | * |   |

## lead_added

a crm lead was created


```json
{
  "type": "AddAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_added properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## lead_updated

a crm lead was updated


```json
{
  "type": "UpdateAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_updated properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! | UpdateAction  |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## lead_removed

a lead was removed


```json
{
  "type": "RemoveAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_removed properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## lead_assigned

a lead was assigned


```json
{
  "type": "AssignAction",
  "agent": "http://user.example.com/profile/card",
  "object": {},
  "topic": "lead"
}
```

#### lead_assigned properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | string |   |

## lead_accepted

a crm lead was accepted


```json
{
  "type": "AcceptAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_accepted properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## lead_rejected

a crm lead was rejected


```json
{
  "type": "RejectAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_rejected properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## lead_returned

a crm lead was returned


```json
{
  "type": "ReturnAction",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "AssignAction",
    "id": "http://example.com",
    "agent": "http://organization.example.com/profile/card#me",
    "recipient": "http://user.example.com/profile/card#me",
    "object": {
      "type": "Person",
      "id": "https://example.com/collection/1",
      "name": "string",
      "givenName": "Bruce",
      "familyName": "Wayne",
      "jobTitle": "Jefe",
      "email": "user@example.com",
      "faxNumber": "(498) 625-6456",
      "telephone": "1-339-041-0306 x2866",
      "contactPoint": [
        {
          "type": "ContactPoint",
          "name": "Work",
          "telephone": "1-364-127-9618 x20418",
          "faxNumber": "834.320.1602",
          "email": "user@example.com",
          "url": "https://www.facebook.com/hallandoates"
        }
      ],
      "address": [
        {
          "type": "PostalAddress",
          "streetAddress": "1007 Mountain Gate Rd",
          "postOfficeBoxNumber": "Box 1234",
          "addressRegion": "New Jersey",
          "addressLocality": "Gotham City",
          "postalCode": "10010"
        }
      ],
      "birthDate": "2019-04-14",
      "leadSource": {
        "type": "Organization",
        "id": "https://example.com/collection/1",
        "name": "string",
        "telephone": "079.706.7065 x6341",
        "faxNumber": "(873) 271-4802",
        "email": "user@example.com",
        "url": "http://example.com",
        "availableLanguage": [
          {
            "type": "Language",
            "name": "English",
            "additionalName": "en"
          }
        ],
        "branchCode": "CA301-001",
        "contactPoint": [
          {
            "type": "ContactPoint",
            "name": "Work",
            "telephone": "1-364-127-9618 x20418",
            "faxNumber": "834.320.1602",
            "email": "user@example.com",
            "url": "https://www.facebook.com/hallandoates"
          }
        ],
        "logo": [
          {
            "type": "DigitalDocument",
            "id": "http://user.example.com/public/logo/fileName.zip",
            "name": "fileName.zip",
            "encodingFormat": "application/zip",
            "identifier": {},
            "about": "http://user.example.com/profile/card#me"
          }
        ],
        "image": [
          {
            "type": "ImageObject",
            "id": "http://user.example.com/public/logo/image.jpg",
            "name": "image.jpg",
            "encodingFormat": "image/jpeg",
            "content": "string",
            "about": "http://user.example.com/profile/card#me",
            "url": "http://user.example.com/public/profile/image.jpg"
          }
        ],
        "parentOrganization": [
          "http://example.com"
        ]
      }
    }
  },
  "topic": "lead"
}
```

#### lead_returned properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | a lead offered or assigned by the agent to one or more recipients  |
| topic | * |   |

## website_registration

a website vistor has registered


```json
{
  "type": "Notification",
  "id": "https://you.example.com/inbox/12345",
  "topic": "website",
  "timestamp": 1550503972767,
  "agent": "https://user.example.com/profile/card#me",
  "instrument": "https://application.example.com/profile/card#me",
  "object": {
    "type": "string",
    "agent": "http://user.example.com/profile/card",
    "object": {}
  }
}
```

#### website_registration properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string |   |
| id | string&lt;uri&gt; | the notification uri  |
| topic | [string] | subscription scopes that will recieve the notification  |
| timestamp | string | the time the notification was created  |
| agent | string&lt;uri&gt; | the user/source that generated the notification  |
| instrument | string&lt;uri&gt; | application or service that delivereted the notification  |
| object | object | the event payload <br/>RANGE: [Action](/schemas#action) |

## website_appointment_requested

a website vistor has requested an appointment


```json
{
  "type": "string",
  "agent": "http://user.example.com/profile/card",
  "object": {
    "type": "string",
    "agent": "http://user.example.com/profile/card",
    "object": {}
  },
  "topic": "website"
}
```

#### website_appointment_requested properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | * |   |

## website_showing_requested

a website visitor has requested a showing appointment


```json
{
  "type": "string",
  "agent": "http://user.example.com/profile/card",
  "object": {},
  "topic": "website"
}
```

#### website_showing_requested properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | * |   |

## website_question

a website visitor has asked a question


```json
{
  "type": "string",
  "agent": "http://user.example.com/profile/card",
  "object": {},
  "topic": "website"
}
```

#### website_question properties

| Name/Type | Type | Description |
|:--------- | :--- | :---------- |
| type | string! |   |
| agent | string&lt;uri&gt;&#124;object | the direct performer or driver of the action. <br/>RANGE: [Person](/schemas#person),[Organization](/schemas#organization),[URI](/schemas#uri) |
| object | object | The object upon the action is carried out, whose state is kept intact or changed.  |
| topic | * |   |
