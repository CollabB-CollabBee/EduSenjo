# Application development process

## Structure of workflow

### First steps
Main example structure:

root/
├── api-gateway/
│   ├── Dockerfile
│   ├── README.md
│   └── src/
│       ├── index.js
│       └── routes/
│           ├── users.js
│           └── posts.js
├── auth-service/
│   ├── Dockerfile
│   ├── README.md
│   └── src/
│       ├── index.js
│       ├── models/
│       │   └── user.js
│       └── routes/
│           └── auth.js
├── post-service/
│   ├── Dockerfile
│   ├── README.md
│   └── src/
│       ├── index.js
│       ├── models/
│       │   └── post.js
│       └── routes/
│           └── posts.js
└── user-service/
    ├── Dockerfile
    ├── README.md
    └── src/
        ├── index.js
        ├── models/
        │   └── user.js
        └── routes/
            └── users.js

### Steps taken
* Install Express Generator: If you haven't already, install Express Generator globally using npm
- npm install -g express-generator
* Create a New Project: Create a new directory for your project and navigate to it using your terminal. Then, run the following command to generate a new project using Express Generator:
- express my-microservice
* Start the Development Server: Navigate into the newly created project directory:
- cd my-microservice
- npm start

### Next
This will start the Express.js development server and run your microservice on port 3000.

Develop Your Microservice: You can now start developing your microservice using Express.js. Create routes, controllers, models, and other application logic within the src directory of your project.

Test Your Microservice: Write unit and integration tests for your microservice code in the tests directory. You can use Mocha and chai as popular testing frameworks for Node.js applications.

Deploy Your Microservice: Once your microservice is developed and tested, you can deploy it to a production environment using a containerization platform like Docker or Kubernetes.

### Suggested workflow
The first important scope of the user microservice to develop is user registration and authentication. This functionality provides the foundation for managing user accounts and enabling secure access to the application. A prioritized development list for the user microservice would be as follows:

1. **User Registration:** Implement user registration functionality to allow new users to create accounts. This involves capturing user information, validating input, and securely storing user credentials.

2. **User Authentication:** Develop user authentication mechanisms to verify user identities and enable secure access to application resources. This includes implementing login and logout functionalities, handling password management, and utilizing appropriate authentication protocols.

3. **User Profile Management:** Create user profile management features to allow users to edit their personal information, manage their preferences, and view their account details.

4. **Access Control and Authorization:** Implement access control and authorization mechanisms to restrict access to sensitive data and functionalities based on user roles and permissions. This ensures that users can only access resources they are authorized to use.

5. **User Notifications and Alerts:** Develop user notification and alert systems to inform users about important events, such as password resets, account updates, or security warnings.

6. **User Activity Tracking:** Implement user activity tracking to monitor user behavior, identify patterns, and gain insights into user interactions with the application.

7. **User Preferences and Personalization:** Create user preference and personalization features to allow users to customize their experience based on their individual preferences and settings.

8. **Social Integration and Third-Party Authentication:** Integrate social login functionalities and third-party authentication mechanisms to provide users with alternative login options and enhance user experience.

9. **User Data Management and Privacy:** Implement robust data management practices to ensure the security, privacy, and compliance of user data. This includes data encryption, access controls, and data deletion policies.

10. **User Feedback and Support:** Develop user feedback mechanisms and support channels to collect user feedback, address concerns, and provide assistance when needed.

By prioritizing these features, you can establish a solid foundation for user management and authentication within your microservice architecture. As the user microservice evolves, you can expand its scope to include additional functionalities that enhance user experience and support your overall application requirements.

### Files needed to be created:
To develop the user registration functionality for your microservice, you'll need to create several files to handle user registration requests, validate input data, interact with a database to store user information, and send confirmation emails or notifications.

Here's a breakdown of the files you'll need:

1. **User Registration Controller:** Create a controller file, such as `userRegistrationController.js`, to handle incoming user registration requests. This controller will receive user registration data, process it, and interact with the database to create new user accounts.

2. **User Registration Request Model:** Create a model file, such as `userRegistrationRequestModel.js`, to define the structure of user registration data. This model will ensure that the incoming data conforms to the expected format and contains all the necessary information.

3. **User Registration Service:** Create a service file, such as `userRegistrationService.js`, to encapsulate the business logic related to user registration. This service will handle tasks like validating user input, generating secure passwords, and interacting with the database to persist user information.

4. **User Data Access Object (DAO):** Create a DAO file, such as `userDao.js`, to handle interactions with the database for user data management. This DAO will provide methods for creating, reading, updating, and deleting user data in the database.

5. **User Registration Email Notification:** If your application requires email notifications for user registration, create a file, such as `userRegistrationEmailNotification.js`, to handle sending confirmation emails to new users. This file will use email libraries or APIs to send personalized emails with registration details and activation links.

6. **User Registration Error Handling:** Implement error handling mechanisms in your controller, service, and DAO to capture and handle errors that may occur during the user registration process. This will ensure that users receive appropriate error messages or notifications if registration fails.

7. **User Registration Unit Tests:** Create unit tests for your controller, service, and DAO to verify the correctness and functionality of the user registration process. These tests will ensure that the code behaves as expected and handles various input scenarios correctly.

8. **User Registration Integration Tests:** If your application involves multiple microservices, create integration tests to ensure that the user registration process works seamlessly across different microservices. These tests will simulate real-world interactions between microservices to validate the overall user registration flow.

By creating and organizing these files, you can effectively implement user registration functionality for your microservice, ensuring that new users can create accounts and securely access your application.

### Chosen structure for the user-microservice:
user-microservice
├── controllers
│   └── userRegistrationController.js
├── models
│   └── userRegistrationRequestModel.js
├── services
│   └── userRegistrationService.js
├── dao
│   └── userDao.js
├── emailNotifications
│   └── userRegistrationEmailNotification.js
├── utils
│   └── errorHandler.js
├── tests
│   ├── unitTests
│   │   ├── userRegistrationController.test.js
│   │   └── userRegistrationService.test.js
│   └── integrationTests
│       └── userRegistrationIntegrationTests.js
└── index.js

### Business Logic for User Registration:
Yes, the business logic for user registration is closely related to the type of information that will be collected from users. The specific business logic will vary depending on the application and its requirements, but it typically involves the following steps:

1. **Data Validation:** Validate the user-provided information to ensure it is complete, accurate, and meets the application's requirements. This may include checking for valid email addresses, strong passwords, and adherence to data formatting guidelines.

2. **Input Sanitization:** Sanitize the user-provided input to prevent malicious code or data injection attacks. This involves removing or escaping any potentially harmful characters or data that could compromise the application's security.

3. **User Uniqueness Check:** Verify that the provided username or email address is unique within the system. This ensures that no two users can have the same identifier, preventing conflicts and maintaining data integrity.

4. **Password Hashing:** Securely hash the user's password using a strong hashing algorithm. This prevents the storage of plain-text passwords, significantly enhancing security and protecting user credentials.

5. **User Account Creation:** Create a new user account in the database, storing the hashed password, user information, and any other relevant data. This establishes the user's identity and access privileges within the application.

6. **Account Activation or Confirmation:** Depending on the application's workflow, either activate the user's account immediately or send a confirmation email or notification. This ensures that the user has a valid account and can access the application's features.

7. **User Role Assignment:** Assign the newly created user an appropriate role or set of permissions based on the application's authorization model. This controls the user's access to specific functionalities and resources within the system.

8. **Error Handling:** Implement robust error handling mechanisms to capture and handle any errors that may occur during the user registration process. This provides appropriate feedback to users and ensures system stability.

9. **Logging and Auditing:** Log user registration events for auditing and tracking purposes. This provides a record of user activity and can be used for troubleshooting and security analysis.

By carefully considering the business logic associated with user registration, you can ensure that your application collects the necessary information securely, validates it appropriately, and creates user accounts in a consistent and secure manner.

### Setting up database connection for user-microservice testing

A dedicated configuration directory typically sits at the root level of your application, alongside the microservice directories and other top-level components. This structure provides a consistent and organized approach to managing configuration files across the application.

Here's an example of a directory structure with a dedicated configuration directory:

application-root/
├── config/                       # Dedicated configuration directory
│   ├── config.json              # Application-wide configuration
│   ├── user-microservice.json  # Configuration for user microservice
│   └── product-microservice.json # Configuration for product microservice
├── microservices/              # Microservice directories
│   ├── user-microservice/      # User microservice code and resources
│   │   ├── index.js             # Microservice entry point
│   │   └── routes.js            # Microservice routing logic
│   └── product-microservice/   # Product microservice code and resources
│       ├── index.js             # Microservice entry point
│       └── routes.js            # Microservice routing logic
└── other-components/           # Other application components
    ├── database.js              # Database connection and access logic
    └── logger.js               # Logging functionality

### Adaptation: decoupling the database dependency by using Typescript
* changing userDao.js into userDao.ts
### Proposed changes in structure visualized
Sure, here's the suggested directory structure for your project, incorporating TypeScript support while maintaining the existing structure:


project-root/
├── config  # Configuration files
├── docs_and_development_notes  # Documentation and development notes
├── node_modules  # Installed Node.js packages
├── package.json  # Project package manifest
├── package-lock.json  # Node.js dependencies lock file
├── tsconfig.json  # TypeScript compiler configuration
└── user-microservice  # User microservice directory
    ├── app.ts  # Application entry point
    ├── bin  # Executable scripts
    │   └── www  # Startup script for the application
    ├── controllers  # Controllers for handling HTTP requests
    │   ├── controllers.txt  # Controller documentation
    │   └── userRegistrationController.ts  # User registration controller
    ├── dao  # Data access objects for interacting with the database
    │   ├── dao.txt  # DAO documentation
    │   ├── userDao.js  # Legacy JavaScript DAO implementation (for compatibility)
    │   └── userDao.ts  # TypeScript DAO implementation
    ├── emailNotifications  # Email notification logic
    │   ├── emailNotifications.txt  # Email notification documentation
    │   └── userRegistrationEmailNotification.ts  # User registration email notification logic
    ├── models  # Data models representing entities
    │   ├── models.txt  # Model documentation
    │   └── userRegistrationRequestModel.ts  # User registration request model
    ├── package.json  # Microservice package manifest
    ├── public  # Static assets for the application
    │   ├── images  # Application images
    │   ├── javascripts  # Application JavaScript scripts
    │   └── stylesheets  # Application stylesheets
    ├── routes  # Route definitions for routing requests to controllers
    │   ├── index.ts  # Main route configuration
    │   └── users.ts  # User-related routes
    ├── services  # Business logic services
    │   ├── services.txt  # Service documentation
    │   └── userRegistrationService.ts  # User registration service logic
    ├── tests  # Unit and integration tests
    │   ├── integrationTests  # Integration tests for microservice interactions
    │   └── unitTests  # Unit tests for individual components
    ├── utils  # Utility functions and helper classes
    │   ├── errorHandler.ts  # Error handling logic
    │   └── utils.txt  # Utility documentation
    └── views  # Jade templates for rendering HTML pages
        ├── error.jade  # Error page template
        ├── index.jade  # Main application page template
        └── layout.jade  # Common layout template for all pages


This structure preserves the original organization while incorporating TypeScript support. The existing JavaScript files (e.g., `userDao.js`) can be converted to TypeScript gradually, allowing you to transition to TypeScript without disrupting the overall project structure.

Remember to update the `tsconfig.json` file to include the relevant TypeScript compiler options and ensure that the project is configured to compile TypeScript files. With this structure in place, you can effectively manage your user microservice using TypeScript while maintaining the existing directory organization.

## tsconfig
To create a custom `tsconfig.json` file, you'll need to consider the following factors:

1. **Target ECMAScript Version:** Determine the ECMAScript version your project targets. This will affect the features and syntax supported in the generated JavaScript code.

2. **Module System:** Identify the module system used in your project. Common options include CommonJS and ES6 modules. This setting ensures compatibility with the module system used in your project and its dependencies.

3. **Strictness Level:** Decide on the desired strictness level for type checking. A stricter level enforces stricter type rules and prevents potential type errors, but it may require more explicit type annotations.

4. **ES6 Module Interoperability:** Choose whether to enable ES6 module interoperability. This option allows your TypeScript code to interact with ES6 modules in CommonJS environments.

5. **Allow JavaScript Files:** Decide whether to allow the compiler to process plain JavaScript files. This is useful for gradually transitioning from JavaScript to TypeScript.

6. **Implicit `any` Type Checking:** Determine whether to prevent implicit `any` type assignments. Enabling this option promotes explicit type annotations and improves type safety.

7. **Declaration File Checking:** Decide whether to skip checking for declaration files (.d.ts) in libraries. This can improve compilation speed, especially for large projects with numerous libraries.

8. **Include/Exclude Patterns:** Specify the patterns of files to be included or excluded from the compilation process. This allows you to selectively compile specific files or directories.

9. **Additional Compiler Options:** Explore other available compiler options that may be relevant to your project, such as source map generation, emitting JavaScript files with inline type annotations, or setting the module resolution strategy.

By carefully considering these factors and tailoring the `tsconfig.json` file to your project's specific needs, you can effectively configure the TypeScript compiler and ensure that your code is compiled correctly, adheres to the desired standards, and benefits from TypeScript's type system.

### example tsconfig all options
```{
  "compilerOptions": {
    "target": "es2022", // ECMAScript version target
    "module": "commonjs", // Module system (CommonJS or ES6)
    "strict": true, // Strict mode for type checking
    "esModuleInterop": true, // Interoperability with ES6 modules
    "allowJs": true, // Allow processing of JavaScript files
    "noImplicitAny": true, // Prevent implicit `any` type assignments
    "skipLibCheck": true, // Skip checking declaration files (.d.ts)
    "outDir": "./dist", // Output directory for compiled JavaScript files
    "declaration": true // Generate declaration files (.d.ts)
  },
  "include": ["**/*.ts", "**/*.tsx"] // Include patterns for TypeScript files
}```
``````
### Config directory
* made the map database-configurations

### Changes to be maked as list
To address the errors of modules and types not found in `userRegistrationController.ts`, you'll need to make changes to the following files, converting them from JavaScript to TypeScript:

1. **utils/password-hasher.js:** This file contains the `hashPassword` function used for hashing passwords. Convert this file to `utils/password-hasher.ts` and add TypeScript type annotations to the function parameters and return value. This will ensure type safety and prevent type errors related to the `hashPassword` function.

2. **email-notifications/user-registration-email-notification.js:** This file contains the `sendConfirmationEmail` function used for sending confirmation emails. Convert this file to `email-notifications/user-registration-email-notification.ts` and add TypeScript type annotations to the function parameters. This will ensure type safety and prevent type errors related to the `sendConfirmationEmail` function.

3. **models/userRegistrationRequestModel.js:** This file (if it exists) contains the model for the user registration request data. Convert this file to `models/userRegistrationRequestModel.ts` and add TypeScript type annotations to the model properties. This will ensure type safety and prevent type errors related to the user registration request data.

4. **dao/userDao.js:** This file (if it exists) contains the data access object (DAO) for interacting with the user data in the database. Convert this file to `dao/userDao.ts` and add TypeScript type annotations to the function parameters and return values. This will ensure type safety and prevent type errors related to the user data access.

5. **services/userRegistrationService.js:** This file (if it exists) contains the service logic for handling user registration. Convert this file to `services/userRegistrationService.ts` and add TypeScript type annotations to the function parameters and return values. This will ensure type safety and prevent type errors related to the user registration service.

By converting these files to TypeScript and adding appropriate type annotations, you'll resolve the errors related to modules and types not found, ensuring compatibility with the TypeScript code in `userRegistrationController.ts`.


# GAP 20 nov 2023

Sure, here is a list of files that must be made in order to make the user microservices work:

**Controllers**

* AuthenticationController.ts
* AuthorizationController.ts
* UserController.ts

**Services**

* AuthService.ts
* AuthorizationService.ts
* UserService.ts

**Other Files**

* userRegistrationRequestModel.d.ts (Already completed)
* passwordhasher.d.ts (Optional, but recommended)

In addition to the above files, you may also need to create additional files depending on the specific implementation of your user microservices. For example, you may need to create configuration files, middleware files, or error handling files.

Here is a more detailed explanation of each file:

* **AuthenticationController.ts:** This file will handle all of the authentication-related routes for your user microservices. This includes routes for logging in, registering new users, and resetting passwords.
* **AuthorizationController.ts:** This file will handle all of the authorization-related routes for your user microservices. This includes routes for checking user permissions, granting and revoking permissions, and managing roles.
* **UserController.ts:** This file will handle all of the user-related routes for your user microservices. This includes routes for getting user information, updating user information, and deleting user accounts.
* **AuthService.ts:** This file will provide the business logic for authentication-related tasks. This includes tasks such as verifying user credentials, creating new user accounts, and generating authentication tokens.
* **AuthorizationService.ts:** This file will provide the business logic for authorization-related tasks. This includes tasks such as checking user permissions, granting and revoking permissions, and managing roles.
* **UserService.ts:** This file will provide the business logic for user-related tasks. This includes tasks such as getting user information, updating user information, and deleting user accounts.
* **userRegistrationRequestModel.d.ts:** This file will define the data structure for a user registration request. This file is optional, but it is recommended to use it to ensure type safety in your application.
* **passwordhasher.d.ts:** This file will define the interface for a password hasher. This file is optional, but it is recommended to use it to ensure type safety in your application.

I hope this list is helpful. Please let me know if you have any other questions.

