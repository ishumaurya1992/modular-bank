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
Sql Script :

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

GET: http://localhost:8080/account/{accountId}


       

POST: http://localhost:8080/account/transaction

        





## Authors

* **Ishu Maurya** - *Assignment* - [modularbank](https://github.com/ishumaurya1992/modular-bank)

