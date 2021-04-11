# Project Title

modularbank (Software engineer test assignment)

## Getting Started

Import in IDE as maven project.

### Prerequisites

What things you need to install the software and how to install them

```
* JDK 11
* STS
* Postgres 13.2
* Maven 3.5
* RabbitMQ 3.8


```
SQL Script :

```

CREATE TABLE account (
   id integer primary key  default  nextval('id_sequence'::regclass),
   accountNumber VARCHAR ( 12 ) NOT null unique,
   balance numeric(19, 2) NOT NULL,
   currency smallint NOT NULL,
   country  VARCHAR ( 50 ) NOT NULL,
   customerId VARCHAR ( 12 ) NOT null,
   createdDate timestamp with time zone NOT NULL DEFAULT timezone('UTC'::text, now()),
   constraint balance check (balance >= 0)
);


CREATE TABLE transaction (
   id integer primary key  default  nextval('id_sequence'::regclass),
   accountNumber VARCHAR ( 12 ) NOT NULL,
   amount  numeric(19, 2) NOT NULL,
   curr_balance numeric(19, 2) NOT null,
   currency smallint NOT NULL,
   description text ,
   direction  VARCHAR ( 50 ) NOT NULL,
   createdDate timestamp with time zone NOT NULL DEFAULT timezone('UTC'::text, now()),
   constraint amount check (amount >= 0)

);
ALTER TABLE transaction ADD FOREIGN KEY (accountNumber)
REFERENCES account(accountNumber) ON DELETE CASCADE;

```

Ports:
```
tomcat : 8080
RabbitMQ : 5672

```

Important links:


POST: http://localhost:8080/account/create

![image](https://user-images.githubusercontent.com/43113212/114313246-65d3df00-9b13-11eb-8601-eb149cdd24ec.png)

GET: http://localhost:8080/account/{accountId}

![image](https://user-images.githubusercontent.com/43113212/114313280-9451ba00-9b13-11eb-9e01-b694179b4e28.png)


POST: http://localhost:8080/account/transaction

Request:        
![image](https://user-images.githubusercontent.com/43113212/114313313-b51a0f80-9b13-11eb-9a2d-bca32b902107.png)

Response:
![image](https://user-images.githubusercontent.com/43113212/114313342-c8c57600-9b13-11eb-8f06-373f40c5e316.png)





## Authors

* **Ishu Maurya** - *Assignment* - [modularbank](https://github.com/ishumaurya1992/modular-bank)

