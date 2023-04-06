# UofM Find Course API
This API is designed to support enrollment at UofM. This set of APIs would provide a list of information related to the courses they are interested in. Students could specify relevant parameters such as Year, Term and CourseID to retrieve course information.
## API description
Our API is a simple REST API, where user can do GET requests to the endpoint.

## Endpoints and Parameters
#### Endpoint
There is only one endpoint.  
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseID}```
#### Patameters
There are three parameters:
| Parameter  | Type   | Description  | Required  |
|------------|--------|--------------|-----------|
| Year       | int    | the academic year in which the course is being offered. Ex:2023|  Yes |
| Term       | string | the specific part of the academic year. Ex:Fall, Winter        |  Optional  |
| CourseID   | string | the ID of a specific course. Ex:COMP3040                       |  Optional  |

## Description of Resources
| **Parameters**  | **Type**  | **Description** |
|---|---|---|
| CourseID  | string  |  The subject and crouse number of a course. |
| CourseName  | string  |  The course title. |
| Prerequisites | string  | The prerequisites of the course.  |
| Description  | string  |  The description of the course. |
| Credits | int  | Credits hours of the course. |
| Attribute  | string  | The attribute of the course.  |
| Term | string | The term the course is being offered in. |
| Year | int | The year the course is being offered in. |
| Status code | int | The code indicating if the request was a success/fail. |

### Response JSON Description
```json
  {
     "Courses": [
    {
     "CourseID": "<string>",
    "CourseName": "<string>",
    "Prerequisites": "<string>",
    "Description": "<string>",
    "Credits": "<int>",
    "Attribute": "<string>",
    "Term": "<string>",
    "Year": "<int>"
    },
    ...
    ],
    "Status code": "<int>"
  }
```
## Sample Requests
Here are the three sample requests for getting course information from our API:

### 1.List all Computer Science courses in a specific academic year.
```https://UofMCSEnrollment.ca/api/courses?{Year}```

####  GET Request
 ```
    https://UofMCSEnrollment.ca/api/courses?{2023}
  ```

#### Response
```json
  {
  "Courses": [
    {
      "CourseID": "COMP3040",
      "CourseName": "Technical Communication in Computer Science",
      "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610",
      "Description": "This course is designed to help students become more effective and confident writers in the context of the computing profession.",
      "Credits": 3,
      "Attribute": "Science Requirement for BA, Science",
      "Term": "Fall/Winter",
      "Year": 2023
    },
    {
      "CourseID": "COMP3430",
      "CourseName": "Operating Systems",
      "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610",
      "Description": "This course is designed to help students get a better understanding of Operating systems, their design, implementation, and usage.",
      "Credits": 3,
      "Attribute": "Science Requirement for BA, Science",
      "Term": "Summer/Fall",
      "Year": 2023
    }
  ],
  "Status code": 200
}
```
### 2. List all Computer Science courses in a specific academic year and term.
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}```

#### GET Request
```
https://UofMCSEnrollment.ca/api/courses?{2023}&{Winter}
```
  
#### Response
```json
  {
  "Courses": [
    {
      "CourseID": "COMP3040",
      "CourseName": "Technical Communication in Computer Science",
      "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610",
      "Description": "This course is designed to help students become more effective and confident writers in the context of the computing profession.",
      "Credits": 3,
      "Attribute": "Science Requirement for BA, Science",
      "Term": "Fall/Winter",
      "Year": 2023
    },
    {
      "CourseID": "COMP3430",
      "CourseName": "Operating Systems",
      "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610",
      "Description": "This course is designed to help students get a better understanding of Operating systems, their design, implementation, and usage.",
      "Credits": 3,
      "Attribute": "Science Requirement for BA, Science",
      "Term": "Summer/Fall/Winter",
      "Year": 2023
    }
  ],
  "Status code": 200
}
```

### 3. List a specific Computer Science course in a specific academic year and term.
```https://UofMCSEnrollment.ca/api/courses?{Year}&{Term}&{CourseID}```

 #### GET Request

  ```
  https://UofMCSEnrollment.ca/api/courses?{2023}&{Winter}&{COMP3430}
  ```

### Response 
```json
  {
  "Courses": [
    {
      "CourseID": "COMP3430",
      "CourseName": "Operating Systems",
      "Prerequisites": "one of COMP 2140 or COMP 2061; and COMP 2280 or ECE 3610",
      "Description": "This course is designed to help students get a better understanding of Operating systems, their design, implementation, and usage.",
      "Credits": 3,
      "Attribute": "Science Requirement for BA, Science",
      "Term": "Winter/Fall",
      "Year": 2023
    }
  ],
      "Status code": 200
}
