
**Workflow**

N.B: Project explanation from this blog [https://prismaio.notion.site/Let-s-build-a-REST-API-with-NestJS-and-Prisma-94258f8a78d7460883d5b900f706e9ae]

Up and running postgres database
`docker-compose up --build`

If database port already running then stop this port and container then docker-compose up again

To do this task we need to run this command
```
sudo docker kill $(docker ps -q)
sudo netstat -nlpt |grep 3306
sudo kill <PID> ex: 33031
```

migrate prisma orm
`npx prisma migrate dev`

generate prisma module and service
```
npx nest generate module prisma
npx nest generate service prisma
```

push schema to postgres database
`npx prisma db push`

open prisma studio for data visualization and manipulation
`npx prisma studio`

generate resource ex: create CRUD module
`npx nest generate resource`

generate exception filter 
`npx nest generate filter prisma-client-exception`

install dotenv-cli for end-to-end testing
`npm i dotenv-cli --save-dev`

add this property to jest-e2e.json file
```
  "moduleDirectories": [
    "<rootDir>/../",
    "node_modules"
  ]
```

for running end-to-end testing we first need to migrate database
`npx prisma migrate dev`

then run this command for test
`npm run test:e2e`