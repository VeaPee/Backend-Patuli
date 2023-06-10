# Description

- We use Express.js to create this API endpoints as backend
- For deployment we are using App Engine service by Google Cloud Platform
- For database we are using MongoDB Atlas
- For storing images we use Google Cloud Storage
- For auto deployment we use Cloud Build by Google Cloud Platform, and setup cloudbuild.yaml before doing that

# Endpoints

## Register

- Method: POST
- Path URL: /api/v1/auth/register
- Header: -
- Body:
    - name: string
    - email: string(email)
    - password: string(min 8 max 20 digit)
    - passwordConfirmation: string(must be the same as password)
- Authorization: -
- Response (example):

```json
{
    "error": false,
    "message": "Akun berhasil dibuat",
    "data": {
        "name": "string",
        "email": "string",
        "password": "string",
        "accountLevel": "integer",
        "accountExp": "integer",
	"completedSubQuiz": "integer",
        "completedQuiz": "integer",
        "createdAt": "date",
        "_id": "ObjectID",
        "imageUrl": "string",
        "__v": "integer"
    }
}
```

## Login
- Method: POST
- Path URL: /api/v1/auth/login
- Header: -
- Body:
    - email: string(email)
    - password: string(min 8 max 20 digit)
- Authorization: -
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": {
        "id": "ObjectID",
        "name": "string",
        "token": "string"
    }
}
```

## Get Profile

- Method: GET
- Path URL: /api/v1/account/profile
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": {
        "_id": "ObjectID",
        "name": "string",
        "email": "string",
        "password": "string",
        "accountLevel": "integer",
        "accountExp": "integer",
        "completedQuiz": "integer",
        "createdAt": "date",
        "imageUrl": "string",
        "__v": "integer"
	"completedSubQuiz": "integer",
    }
}
```

## Edit Password Account

- Method: PUT
- Path URL: /api/v1/account/edit-password
- Header: -
- Body:
    - oldPassword: string(min 8 max 20 digit)
    - newPassword: string(min 8 max 20 digit, can’t be the same as old password)
    - passwordConfirmation: string(min 8 max 20 digit, must be the same as new password)
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Password berhasil diubah"
}
```

## Edit Profile Picture Account

- Method: PUT
- Path URL: /api/v1/account/edit-image
- Header (Content-Type): multipart/form-data
- Body:
    - file: image(JPG, JPEG, PNG)
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Foto profil berhasil diubah"
}
```

## Get All Lessons

- Method: GET
- Path URL: /api/v1/lessons
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        },
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        },
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        },
	...
    ]
}
```

## Get Lesson by Lesson Type

- Method: GET
- Path URL: /api/v1/lessons/:lessonType
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        },
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        },
	...
    ]
}
```

## Get Lesson by Lesson Number

- Method: GET
- Path URL: /api/v1/lessons/:lessonType/:lessonNumber
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectID",
            "lessonName": "string",
            "imageUrl": "string",
            "lessonNumber": "integer",
            "lessonType": "string"
        }
    ]
}
```

## Get All Quizzes

- Method: GET
- Path URL: /api/v1/quizzes/
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer",
            "languageType": "string",
	    "subQuiz": "integer"
        },
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
	...
    ]
}
```

## Get Quiz by Quiz Difficulty

- Method: GET
- Path URL: /api/v1/quizzes/:quizDifficulty
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
	...
    ]
}
```

## Get Quiz by Sub Quiz

- Method: GET
- Path URL: /api/v1/quizzes/:quizDifficulty/:subQuiz
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        },
	...
    ]
}
```

## Get Quiz by Quiz Number

- Method: GET
- Path URL: /api/v1/quizzes/:quizDifficulty/:subQuiz/:quizNumber
- Header: -
- Body: -
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "success",
    "data": [
        {
            "createdAt": "date",
            "_id": "ObjectId",
            "answer": "string",
            "quiz": "string",
            "quizDifficulty": "string",
            "quizNumber": "integer"
	    "languageType": "string",
	    "subQuiz": "integer"
        }
    ]
}
```

## Edit Exp Account

- Method: PUT
- Path URL: /api/v1/level/edit-exp
- Header: -
- Body:
    - newExp: number(increment)
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Exp berhasil diperbarui"
}
```

## Edit Level Account

- Method: PUT
- Path URL: /api/v1/level/edit-level
- Header: -
- Body:
    - newLvl: number(increment)
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Level berhasil diperbarui"
}
```

## Edit Completed Sub Quiz

- Method: PUT
- Path URL: /api/v1/level/edit-completed-sub-quiz
- Header: -
- Body:
    - newQuestComplete: number
    - subQuiz: number
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Completed quiz berhasil diperbarui"
}
```

## Edit Completed Quiz Beginner Account

- Method: PUT
- Path URL: /api/v1/level/edit-completed-quiz-beginner
- Header: -
- Body:
    - newQuestComplete: number
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Completed quiz berhasil diperbarui"
}
```

## Edit Completed Quiz Intermediate Account

- Method: PUT
- Path URL: /api/v1/level/edit-completed-quiz-intermediate
- Header: -
- Body:
    - newQuestComplete: number
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Completed quiz berhasil diperbarui"
}
```

## Edit Completed Quiz Expert Account

- Method: PUT
- Path URL: /api/v1/level/edit-completed-quiz-expert
- Header: -
- Body:
    - newQuestComplete: number
- Authorization: Bearer Token
- Response (example):

```json
{
    "error": false,
    "message": "Completed quiz berhasil diperbarui"
}
```

## Get Hash

- Method: GET
- Path URL: /api/v1/hash/
- Header: -
- Body: -
- Authorization : -
- Response (example):

```json
{
    "data": [
        {
            "abjad": "string"
        },
        {
            "abjad_lite": "string"
        },
        {
            "angka": "string"
        },
        {
            "angka_lite": "string"
        },
        {
            "kata": "string"
        },
        {
            "kata_lite": "string"
        }
    ]
}
```
