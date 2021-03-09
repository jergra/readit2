start pgadmin from windows
    password: !Virgil43
go to pgadmin12
    password: password

from readit prompt, this runs database:
    npm run dev

from readit prompt, to get database prompt:
    psql -d readit -U postgres
        password is: password
    (this username and password are set in: ormconfig.json)



destroy all tables in the database and remake:
    1. delete all migration files in the migration folder
    2. run the following
        npm run typeorm schema:drop
        npm run typeorm migration:run

adding new table to the database:
    create a migration file in the migration folder:
        npm run typeorm migration:generate -- --name migration-file-name-mentioning-new-table
    run the migration file that you have just createdwoo:
        npm run typeorm migration:run