Flask Script Executor

The Flask Script Executor is a web service that securely executes Python scripts and functions. It provides two routes to handle script execution and function invocation.

Routes
------

/scripts

This route accepts a POST request with a JSON payload containing the Python script code to execute. The script is executed securely by parsing the code using the `ast` module and checking for any dangerous operations. The result of the script execution is returned as a JSON response.

Example Request:

POST /scripts
Content-Type: application/json

{
  "script_code": "print('Hello, World!')"
}

Example Response:

HTTP/1.1 200 OK
Content-Type: application/json

{
  "result": "Script executed successfully"
}

/params

This route accepts a POST request with a JSON payload containing the Python script code and parameters to execute a specific function within the script. The script code is parsed using the `ast` module, and the specified function is executed with the provided parameters. The result of the function execution is returned as a JSON response.

Example Request:

POST /params
Content-Type: application/json

{
  "script_code": "def custom(name): return 'Hello, ' + name",
  "script_params": ["Alice"]
}

Example Response:

HTTP/1.1 200 OK
Content-Type: application/json

{
  "result": "Hello, Alice"
}

Requirements
------------

- Python 3.9+
- Flask
- RestrictedPython

Installation
------------

1. Clone the repository: git clone <repository_url>


2. Install the dependencies: pip install -r requirements.txt


Usage
-----

1. Run the Flask app: flask run


2. Send HTTP requests to the appropriate endpoints as described above.

Security Considerations
-----------------------

The script execution is performed in a restricted environment using the `ast` module to parse the code and check for dangerous operations. Dangerous functions and module imports are explicitly disallowed. However, it's important to thoroughly review and validate any code executed in this service to ensure security.

License
-------

This project is licensed under the MIT License. See the LICENSE file for details.

Feel free to customize and expand this README to provide more information about your specific use case and any additional functionality or features of your Flask app.
