# Gh-Data Api Docs Guide

_[The GH-Data ](https://ghdata.herokuapp.com)_ an opensource project REST api build to fetch all data in the public institutions in Ghana with respective and up to date endpoints.

## Table of Contents

- [Gh-Data REST API](#Api-data-rest-api)

  - [API overview](#api-overview)
  - [Regions](#regions)
  - [Districts](#districts)
  - [Contributing](#contrinbuting)
  - [Contributors](#contributors)
  - [License](#license)

  ## APi Overview

  When you route to the index page of the api, you will find that there are two main endpoints .i.e the regions and their respective cities and thier respective endpoints like so:

  ## Regions

  The regions endpoint fetch all the data related to the regions. We have the following endpoints associated to the regions

  ### All Regions

  <code>https://ghdata.herokuapp.com/regions</code>
  E.g

  ```

  {
  "success": true,
  "code": 200,
  "message": "Request successful",
  "data": [
    {
      "code": "AH",
      "name": "Ahafo Region",
      "capital": "Goaso"
    }
  ]
  }

  ```

  ### One Region

  <code> https://ghdata.herokuapp.com/regions/{regionCode}</code>
  This endpoints fetches a region by supplying the region code

  E.g. Supplying `BE` to the to the regionCode returns the following data.

  ```
  {
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": {
        "code": "BE",
        "name": "Bono East Region",
        "capital": "Techiman"
    }
  }
  ```

  ### One Region with Districts

  <code>https://ghdata.herokuapp.com/regions/{regionCode}/districts</code>
  This endpoint accepts a regionCode to and returns a one region with the available districts.

  E.g.
  The regionCode `BE` returns the data with the available districts

  ```
  {
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": {
        "code": "BE",
        "name": "Bono East Region",
        "capital": "Techiman",
        "districts": [
            {
                "name": "Atebubu Amantin Municipal",
                "capital": "Atebubu",
                "level": "municipal"
            }...etc

        ]
    }
  }

  ```

  ### Search Regions

  <code>https://ghdata.herokuapp.com/search/regions/{query}</code>
  Search through the regions by a search term.

  E.g.
  Searching for `Bono` in the search paramater returns the following JSON response like so:
  <code>https://ghdata.herokuapp.com/search/regions/Bono</code>

  ```
  {
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": [
        {
            "code": "BE",
            "name": "Bono East Region",
            "capital": "Techiman"
        },
        {
            "code": "BO",
            "name": "Bono Region",
            "capital": "Sunyani"
        }
    ]
  }

  ```

## Districts

This api endpoint fetches all the data associated with districts.

### All Districts

<code>https://ghdata.herokuapp.com/districts</code>

```
{
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": [
        {
            "name": "Asunafo North Municipal",
            "capital": "Goaso",
            "level": "municipal",
            "regionCode": "AH"
        }...etc
        ]

}

```

### Filter a district by regionCode

<code>https://ghdata.herokuapp.com/districts{?region=regionCode1,regionCode2,...,regionCodeN}{&level=metropolitan,district,municipal}</code>

Filter a district by supplying one or more regionCodes to the url to fetch all the data related to that district(s) like so:

E.g.
<code>https://ghdata.herokuapp.com/districts?region=BE,AH,AS&level=metropolitan,district,municipal</code>

```

{
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": [
        {
            "name": "Asunafo North Municipal",
            "capital": "Goaso",
            "level": "municipal",
            "regionCode": "AH"
        },
        {
            "name": "Atebubu Amantin Municipal",
            "capital": "Atebubu",
            "level": "municipal",
            "regionCode": "BE"
        },
       {
          "name": "Adansi North District",
          "capital": "Fomena",
          "level": "district",
          "regionCode": "AS"
        }
        ]

}
```

### Get all the regions with their respective districts

<code>https://ghdata.herokuapp.com/regions/{regionCode}/districts</code>
This `url` fetches all data containing regions and thier respective districts

### Search a district by passing a query parameter

<code>https://ghdata.herokuapp.com/search/districts/{query}</code>

E.g.
<code>https://ghdata.herokuapp.com/search/districts/Nkoranza</code>
This endpoint gets all the data for that specific district like so:

```
{
    "success": true,
    "code": 200,
    "message": "Request successful",
    "data": [
        {
            "name": "Nkoranza  North District",
            "capital": "Busunya",
            "level": "district",
            "regionCode": "BE"
        },
        {
            "name": "Nkoranza South Municipal ",
            "capital": "Nkoranza",
            "level": "municipal",
            "regionCode": "BE"
        }
    ]
}


```

###

## Contributing

Contributions are welcome. Feel free to open a pull request with changes.

## Contributors

- [Yeboah Nana Osei](https://twitter.com/yeboahnanaosei)

### Running it Locally

After forking or cloning the repository, perform the following steps to generate the site and preview it:

- Make sure you have node.js installed on your computer. See https://nodejs.org/en/download/
- `npm install` or `yarn` to install all the dependencies
- `npm start` to start the webserver on your local machine
- Point your browser at http://localhost:5000/

## License

The content of this project itself is licensed under the, and the underlying source code used to format and display that content is licensed under the [MIT license](License.txt).
