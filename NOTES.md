# Middle Ware

    * middleware is a function
    * middle ware can execute any code
    * middleware can send response to clint

## Sample middleware ( which is executed for every request )

    const middleware1=(request,response,next)=>{
        console.log("this is middle ware one ");
        next()
    }

    app.use(middleware1)

this code makes use every request use middleware1

## middleware for a specific request

here middleware is executed and after that app.http-method is executed

    app.http-method('path', middleware-name , (req,res)=>{

        })

## middleware for specific path

    const middleware=()=>{}
    app.use('path',middleware)

## Handling Invalid Path

At last of all middlwares write this and above Error Handling middleWare

    app.use((req,res,next)=>{
        res.send({message:`Invalid path ${req.url}`})
    })

## Error Handling Middlwares

Write this middlware after the Invalid Path Middleware

    app.use((error,req,res,next)=>{
        res.send({message:`error occured ${error.message}`})
    })

# Creating seperate APIs Based On Path

## Step 1:

    create seperate files for seperate APIS
    add Extra path to differentiate each API

## Step 2:

    create router in reach API
    const express=require('express')
    const userApp=express.Router() or const productApp=express.Router()

## Step 3:

Export These Routers to Main Server

    module.exports=userApp;
    module.exports=productApp;

## Step 4:

    Import these routers in Server.js

    const userApp=require('./Apis/userApi.js')
