# MultiCRM API 

Integration of multicrm saas api with crm or any other software. This small documentation shows what API methods should be implemented to integrate SAAS Frontend with custom applications. 

How this api works. Api is only invoked by Saas front-end application to CRM/Other software. Api should always send api_secret that is know by other application.
 
# API Methods

Method below must be implemented in software that is integrated with Saas API

  - /register
  - /deactivate-account
  - /resume-account
  - /update-plan
  - /validate
  - /save-or-update-user
  - /delete-user
  

## Register method
---
Type: POST  
Api Parmas:  
```
company_name - Company Name  
user_first_name - First name or Full name  
user_email - Email  
user_password - Plain password, should be hashed on software side  
user_limit - Optional  
storage_limit - Optional  
api_plan - Optional
api_secret - API secret should be checked on software side  
```
expected result if API will return valid values:
```
{
    "status": "success",
    "message": "Company Registered",
    "data": {
        "company": {
            "name": "John Doe Plumber",
            "is_enabled": true,
            "updated_at": "2018-10-24 10:00:00",
            "created_at": "2018-10-24 10:00:00",
            "id": 349
        },
        "user": {
            "first_name": "John",
            "email": "john@example.com",
            "company_id": 349,
            "name": "Mikekpokpok ",
            "updated_at": "2018-10-24 10:00:00",
            "created_at": "2018-10-24 10:00:00",
            "id": 6878,
            "company": {
                "name": "Creed",
                "is_enabled": true,
                "updated_at": "2018-10-24 10:00:00",
                "created_at": "2018-10-24 10:00:00",
                "id": 349
            }
        }
    }
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Company Name Is Taken",
    "data": []
}
or
{
    "message": "The given data was invalid.",
    "errors": {
        "company_name": [
            "The company name field is required."
        ],
        "user_email": [
            "The user email field is required."
        ]
    }
}
```

## Deactivate method
---
Type: POST  
Api Parmas: 

```
company_id - Company ID  
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "Account Deactivated",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "Company not found",
    "data": []
}
```



## Resum account
---
Type: POST  
Api params:
```
company_id - Company ID  
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "Account Activated",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "Whoops! Something went terrible wrong! Please contact Us",
    "data": []
}
```


## Update plan
---
Type: POST  
Api params:  
```
company_id - Company ID  
users_limit - Users limit  
storage_limit - Storage limit  
api_plan - Optional
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "Account Updated",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "Whoops! Something went terrible wrong! Please contact Us",
    "data": []
}
```

## Validate Account
---
Type: POST  
Api params: 
```
company_name - Company Name  
user_email - User Email
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "valid",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "This e-mail is already registered",
    "data": []
}
```

## Validate Account
---
Type: POST  
Api params: 
```
company_name - Company Name  
user_email - User Email
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "valid",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "This e-mail is already registered",
    "data": []
}
```

## Save or Update User / Employee
---
Type: POST  
Api params:
```
email - User Email
first_name - First Name
is_active - Is User Active
id - User id
password - User Password
company_id - Company Id
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "valid",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "success",
    "message": "User saved"
}
or
{
    "status": "error",
    "message": "Cant save user",
    "data": []
}
```

## Delete User
---
Type: POST  
Api params:  
```
id - User id  
company_id - Company Id
api_secret - API secret should be checked on software side.
```

expected result if API will return valid values:
```
{
    "status": "success",
    "message": "User deleted",
    "data": []
}
```
Expected result if API will result invalid values:
```
{
    "status": "error",
    "message": "Invalid secret"
}
or
{
    "status": "error",
    "message": "Cant delete user",
    "data": []
}
```
