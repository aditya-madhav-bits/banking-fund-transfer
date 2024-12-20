# Banking Fund Transfer Service

![Build](https://img.shields.io/badge/Build-Passing-brightgreen.svg) ![License](https://img.shields.io/github/license/aditya-madhav-bits/banking-fund-transfer)  

The **Banking Fund Transfer** service is designed to facilitate secure and efficient fund transfers between accounts. Built using Spring Boot, it provides a RESTful API for managing fund transfer requests, querying transactions, and retrieving details by reference or account ID.  

## Features ✨
- **Initiate Fund Transfers**: Request transfers with account details and amounts.  
- **Query by Reference ID**: Retrieve specific transfer details using a unique reference ID.  
- **Account-Based History**: Fetch all transfers related to a particular account.  
- **Extensible Architecture**: Designed for easy scaling and additional functionality.  

## Tech Stack 🛠️
- **Framework**: Spring Boot  
- **Language**: Java  
- **Database**: MongoDB (or configurable)  
- **Logging**: SLF4J with Lombok  

## API Endpoints 📡

### Base URL: `/fund-transfers`

#### 1. Initiate a Fund Transfer  
- **Endpoint**: `POST /fund-transfers`  
- **Request Body**:  
  ```json
  {
    "fromAccountId": "12345",
    "toAccountId": "67890",
    "amount": 500,
    "description": "Payment for services"
  }
  ```  
- **Response**:  
  ```json
  {
    "referenceId": "ref_001",
    "status": "SUCCESS",
    "message": "Transfer initiated successfully."
  }
  ```  

#### 2. Get Transfer Details by Reference ID  
- **Endpoint**: `GET /fund-transfers/{referenceId}`  
- **Path Variable**: `{referenceId}` = `ref_001`  
- **Response**:  
  ```json
  {
    "referenceId": "ref_001",
    "fromAccountId": "12345",
    "toAccountId": "67890",
    "amount": 500,
    "status": "COMPLETED",
    "timestamp": "2024-11-19T12:00:00Z"
  }
  ```  

#### 3. Get All Transfers by Account ID  
- **Endpoint**: `GET /fund-transfers`  
- **Query Parameter**: `accountId=12345`  
- **Response**:  
  ```json
  [
    {
      "referenceId": "ref_001",
      "toAccountId": "67890",
      "amount": 500,
      "status": "COMPLETED",
      "timestamp": "2024-11-19T12:00:00Z"
    },
    {
      "referenceId": "ref_002",
      "toAccountId": "78901",
      "amount": 250,
      "status": "PENDING",
      "timestamp": "2024-11-18T15:30:00Z"
    }
  ]
  ```  

## Installation 🚀

1. Clone the repository:  
   ```bash
   git clone https://github.com/aditya-madhav-bits/banking-fund-transfer.git
   cd banking-fund-transfer
   ```  

2. Configure your application:  
   Update the `application.properties` file:  
   ```properties
   server.port=8081
   spring.data.mongodb.uri=mongodb://localhost:27017/fund-transfer-db
   ```  

3. Build and run the application:  
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```  

4. Access the API:  
   Navigate to `http://localhost:8081/fund-transfers`.  

## Testing 🧪
Run unit tests:  
```bash
mvn test
```  

## Contribution Guidelines 🤝  
Contributions are welcome! Fork the repository, create a feature branch, and submit a pull request.  
