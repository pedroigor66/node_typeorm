# Table of contents
- [About](#-about)
- [Main libs and techs used](#-main-libs-and-techs-used)
- [Downloading and setting up the project](#-downloading-and-setting-up-the-project)
- [Expected routes](#-expected-routes)
- [License & copyright](#license--copyright)

## 📄 About

This project was done during Rocketseat's GoStack bootcamp challenge. It is a NodeJS server that stores transactions in a postgreSQL server.

---

## 👨‍💻 Main libs and techs used

The project was developed using the following techs:

- [NodeJS](https://nodejs.org/en/)
- [uuidv4](https://www.npmjs.com/package/uuidv4)
- [insomnia](https://insomnia.rest/)
- [Docker](https://www.docker.com/)
- [postgreSQL](https://www.postgresql.org/)
- [DBeaver](https://dbeaver.io/)
- [TypeORM](https://typeorm.io/#/)

---

## 🔧 Downloading and setting up the project

Simply clone this template or download it to your device and run the command **yarn** on your terminal to install all required dependencies.
To make sure erything is running properly, run **yarn test**.
To run the server, run the command **yarn dev:server**.
To test the routes, I recommend using the [insomnia](https://insomnia.rest/) app.

---

## ↔ Expected routes

- `POST /transactions`: This route should receive a `title`, `value`, `type` and `category` inside the requistion body, note that `type` is the transaction type. The transaction type `income` should be used for deposits and `outcome` for withdraws. When storing a new transaction, it is also interesting to log in the databank informations like `created_at` and `updated_at`. The file submitted in the request body should submitted in the following format bellow:

```json
{
  "id": "uuid",
  "title": "Salary",
  "value": 9001,
  "type": "income",
  "category": "Salary"
}
```

- `GET /transactions`: This route must return a list of all the transactions that were registered while the server is running, along with another object `"balance"` that shows the `"total"` value remaining after all the incomes and outcomes are accounted. See an example bellow:


```json
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salary",
      "value": 9001,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Salary",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    },
    {
      "id": "uuid",
      "title": "Freelance",
      "value": 2000,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Others",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    },
  ],
  "balance": {
    "income": 6000,
    "outcome": 0,
    "total": 11001
  }
}
```

- `DELETE /transactions/:id`: This route must delete a transaction that matches the `id` specified in the route parameters.

- `POST /transactions/import`: This route must allow an import of a `.csv` file containing the informations that are required to create a transaction. The imported `.csv` file should contain `title`, `value`, `type` and `category` data separated by `,`.

## License & copyright

Developed by Pedro Igor C. de Oliveira.

Licensed under the [MIT License](LICENSE).
