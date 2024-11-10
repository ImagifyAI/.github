# ImagifyAI - AI-Powered Image Upload, Tagging, Search and Management

## Table of Contents
- [Introduction](#introduction)
- Technologies Used
  - [Frontend](#frontend)
  - [Backend](#backend)
- Core Features
  - [UI](#ui)
  - [User registration and authentication](#user-registration-and-authentication)
  - [AI based image processing, tagging & search](#image-processing)
- [How It Works](#how-it-works)
- Repositories
  - [Frontend](#frontend-repository)
  - [Backend](#backend-repository)


## Introduction
ImagifyAI is a web application that provides image processing services to users. The frontend is a React-based web application running on Cloudflare Pages. The frontend provides a user-friendly interface for users to upload images, select processing options, view and search the processed images. The frontend communicates with the backend API to process the images and display the results to the user. The backend is running on Cloudflare Workers in conjunction with Cloudflare D1, Cloudflare R2, Cloudflare Workers AI for handling user registration, authentication, session handling, processing and storage of images, tagging the images using ***resnet50*** model, searching images based on tags, and allowing users to view and download the processed images.

## Technologies Used
### Frontend
- **Framework**: React (v18.2.0)
- **Styling**: Styled-Components
- **Routing**: React Router DOM (v6.4.0)
- **HTTP Client**: Axios (v1.7.7)

### Backend
- **Cloudflare Workers**: Serverless execution environment for handling API requests and backend logic.
- **Cloudflare Workers AI**: Used for advanced image processing tasks, like auto-tagging or analysis.
- **Cloudflare R2 (Object Storage)**: Stores and serves uploaded images.
- **Cloudflare D1 (SQL Database)**: A structured relational database for storing image metadata and user information.
- **Node.js**: JavaScript runtime environment for backend logic.
- **Vitest**: Testing framework for verifying functionality.
- **JSON Web Tokens (JWT)**: For secure user authentication and session management.
- **Wrangler**: CLI tool for deploying and managing Cloudflare Workers.

## Core Features
### UI
- **Image Upload**: Users can upload images to the platform for processing.
- **Image Processing**: Users can select processing options and view the processed images.
- **Tagging**: Images are tagged using the ***resnet50*** model for easy search and retrieval.
- **Search**: Users can search for images based on tags.
- **Download**: Users can download the processed images.

### User registration and authentication
- **User Registration**: New users can create an account on the platform.
- **User Authentication**: Registered users can log in securely using JWT tokens.

### Image processing
- **Image Tagging**: Images are tagged using the ***resnet50*** model for easy search and retrieval.

### AI-based image processing, tagging & search
- **Image Processing**: Users can upload images for processing, select processing options, and view the processed images and tags detected by the ***resnet50*** model.
- **Auto-Tagging**: Images are automatically tagged using the ***resnet50*** model.
- **Search**: Users can search for images based on tags in the gallery.
- **Download**: Users can download the processed images.

## How It Works
#### The user interacts with the frontend web application based on React and hosted on Cloudflare Pages.
The frontend requires a user to register or log in to access the image processing services. Upon login, the user can upload images, select processing options, and once upload has been completed, they will receive the tags detected by the ***resnet50*** model. These tags can then be used to search for images in the gallery by the user.

***Cloudflare Pages***: I've used Cloudflare Pages to host the frontend application, serving static assets (HTML, CSS, JavaScript) with global distribution across Cloudflare’s edge network. Why? Because Cloudflare Pages automatically deploys the static assets to Cloudflare's global edge network, ensuring that users can load the application quickly from the nearest server. It also integrates with GitHub for seamless continuous deployment, scales with demand, automatically handles traffic spikes, and provides minified assets for faster load times. Additionally, it offers DDoS protection, automatic HTTPS, content security policies, preview deployments for testing, rollback capabilities, and more.

#### The frontend communicates with the backend API running on Cloudflare Workers in conjunction with Cloudflare D1, Cloudflare R2, Cloudflare Workers AI.
The backend API is running on Cloudflare Workers and is responsible for handling user registration, authentication, session handling and processing and storage of images. Once a user registers, their information is stored in Cloudflare D1. The user can then log in securely using JWT tokens. Once the images are uploaded, they are tagged using the ***resnet50*** model using Cloudflare Workers AI. The tagged images are stored in Cloudflare R2 and the image metadata is stored in Cloudflare D1. The backend API also provides search functionality based on tags and serves the processed images to the frontend, allowing users to view and download them.

***Cloudflare Workers***: I've used Cloudflare Workers to execute serverless functions that process incoming API requests, manage routing, handle authentication, and serve the processed images. Why? Because Cloudflare Workers provides a secure, performant, and resilient backend infrastructure. It manages user authentication, routes requests to various endpoints for user actions, and can bind to other Cloudflare services like D1 and R2 for storage and retrieval of image data. It also leverages Workers AI for advanced image processing tasks like auto-tagging, recognition, or analysis.

***Cloudflare D1***: I've used Cloudflare D1 to store image metadata, user information, and search indexing. Why? Because Cloudflare D1 provides structured data storage for relational data, enabling SQL-based searches on tags and other metadata fields. It stores and retrieves user details, image metadata, and enables search functionality based on tags.

***Cloudflare R2***: I've used Cloudflare R2 to store and serve uploaded images. Why? Because Cloudflare R2 provides cost-effective, scalable object storage for image files, enabling secure and reliable access to image data. It handles storing uploaded image files and provides access to image files for the frontend, served securely via R2.

***Cloudflare Workers AI***: I've used Cloudflare Workers AI for advanced image processing tasks like auto-tagging, recognition, or analysis. Why? Because Workers AI enables AI-driven image processing tasks, enhancing the functionality of the platform. It automatically adds tags or labels to images on upload, supporting keyword-based search and potentially other AI-driven analyses on image data.

## Repositories
### [Frontend Repository](https://github.com/ImagifyAI/frontend)
The ImagifyAI Frontend is a React-based web application designed to provide a seamless user experience for interacting with ImagifyAI's image processing services. This frontend is hosted on Cloudflare Pages for fast, reliable, and globally distributed delivery, ensuring optimal performance and scalability. Note that this repository is a part of the ImagifyAI project and is intended to be used in conjunction with the ImagifyAI backend and other related services.

### [Backend Repository](https://github.com/ImagifyAI/backend)
The ImagifyAI Backend is a JavaScript-based backend application designed to provide image processing services to users. This backend is hosted on Cloudflare Workers for serverless execution, scalability, and global reach. It leverages Cloudflare R2 for image storage, Cloudflare D1 to store image metadata and user information, and Cloudflare Workers AI for image tagging. Note that this repository is a part of the ImagifyAI project and is intended to be used in conjunction with the ImagifyAI frontend and other related services.

### To Do
- **Use Cloudflare Turnstile to enhance security & privacy by detecting and blocking bot traffic**
- **Use Cloudflare Images to implement image processing feature, allowing users to select multiple images for conversion to different formats**
- **Use Cloudflare Durable Objects for storing image processing session data, enabling users to resume processing sessions across devices**