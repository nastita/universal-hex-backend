

# Universal HEX API

![Universal Hex Swagger](/docs/assets/swagger.png)

## Description

Universal HEX API is a backend service for the Hybrid Exchange for Universal Assets. It provides a robust API infrastructure to manage and track cross-chain assets, their relationships, and associated metadata.

### Current Features
- Get indexed Universal Assets data from [The Graph Aerodrome Base Subgraph](https://thegraph.com/explorer/subgraphs/GENunSHWLBXm59mBSgPzQ8metBEp9YDfdqwFr91Av1UM)
- Process the data and return it in a structured format to be consumed by the [Universal Hex Frontend](https://github.com/nastita/universal-hex-frontend) 

### To dos & Improvements
- Deploy API to a cloud provider (maybe render free tier or something similar) to make it easier check out
- Add quotes feature
- Add chain info to the assets, its currently on db but not propagated to through the services
- The subgraph we are using seems not to be tracking all the assets. Switching the indexing solution or perhaps implementing a custom indexing solution would be good.
- Implement a caching layer to reduce the number of requests to the subgraph
- Stop relying on coingecko images, upload token images somewhere

## Docker compose

To run the project using Docker Compose, follow these steps:

1. Clone the repository
2. Navigate to the project directory
3. Run the following command:
```bash
$ docker-compose up -d
```

This will start the PostgreSQL database, run the migrations, seed the database, and start the backend and frontend services.

- Visit ``http://localhost:8000/api`` to access the API.
- Visit ``http://localhost:3000`` to access the frontend.

## Project setup

1. Clone the repository

2. Install dependencies:
```bash
$ pnpm install
```

3. Set up environment variables:
   - Copy `.env.example` to `.env`
   - Update the variables according to your environment:
     ```
     NODE_ENV=development
     PORT=3000
     DATABASE_URL=postgresql://postgres:postgres@localhost:5433/universal-hex
     THE_GRAPH_API_KEY=your_api_key
     ```

4. Start the database:
```bash
$ docker-compose up postgres -d
```

## Database Management

- Generate Prisma client:
```bash
$ pnpm prisma generate
```

- Run database migrations:
```bash
$ pnpm prisma migrate dev
```

- Seed the database:
```bash
$ pnpm run seed
```

## Compile and run the project

```bash
# development
$ pnpm run start

# watch mode
$ pnpm run start:dev

# production mode
$ pnpm run start:prod
```

## API Documentation

Once the application is running, you can access the Swagger API documentation at:
```
http://localhost:8000/api
```
