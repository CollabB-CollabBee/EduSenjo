# Important Files
* www - defining server port number
* config.json - holds the global configuration settings for the application. Subsetings go in to the microservice specific settings
* example.txt - a file that holds all the NER information that can't be edited outside in a module or separate file

### Imortant direcotories
* config - holds the configuration files to adjust settings
* docs_and_development_notes - Is an attempt to create an understandable code base

# TO DO
* working on firstFile.txt
* etc.


# Steps done
* made the template for the repository

# TO DO
Create this structure in the type-definitions section
Sure, here is an example of a types directory and its content for a typical social platform web application:

src
├── api                   // API definitions and interfaces
│   ├── auth.d.ts
│   ├── post.d.ts
│   └── user.d.ts
├── components             // React components and interfaces
│   ├── feed.d.ts
│   ├── profile.d.ts
│   └── sidebar.d.ts
├── models                // Data models and interfaces
│   ├── messageModel.d.ts
│   ├── postModel.d.ts
│   └── userModel.d.ts
├── services                // Business logic and service implementations
│   ├── authService.ts
│   ├── postService.ts
│   └── userService.ts
└── types                    // Type definitions and interfaces
    ├── authData.d.ts
    ├── messageData.d.ts
    ├── postData.d.ts
    └── userData.d.ts