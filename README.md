`yarn install`

# Setup Heroku

Create a postgres DB

# Setup Prisma

`yarn run db:init`

- Edit `prisma/.env` with the heroku db Url
- Edit `schema.prisma to create a `house` table

````model House {
  id        Int      @id @default(autoincrement())
  userId    String   @map(name: "user_id")
  image     String
  latitude  Float
  longitude Float
  address   String
  bedrooms  Int
  createdAt DateTime @default(now()) @map(name: "created_at")
  updatedAt DateTime @default(now()) @map(name: "updated_at")

  @@index([userId], name: "houses.userId")
  @@map(name: "houses")
}```

- `yarn run db:new` (make sure there is no `prisma/.env` `DATABASE_URL` set here - Only in `/.env`)
  Give it a name, eg: createHouses
- `yarn run db:migrate:up` to confirm the migration
- `yarn run db:generate` creates a kind of local node_modules with types generated based on the models



Next steps:
1. Set the DATABASE_URL in the .env file to point to your existing database. If your database has no tables yet, read https://pris.ly/d/getting-started.
2. Set the provider of the datasource block in schema.prisma to match your database: postgresql, mysql or sqlite.
3. Run yarn prisma introspect to turn your database schema into a Prisma data model.
4. Run yarn prisma generate to install Prisma Client. You can then start querying your database.
