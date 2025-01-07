# BoilerPlateCode_NodeJS

Boiler Plate Code - Node JS

1. Terminal -> npm init.
2. Create index.js file.
3. Create .gitignore file.
4. Create .env file.
5. Create .env.sample file.
6. Create vercel.json file.
7. Create public folder.
8. Create src folder.
9. Create src folder -> controllers folder.
10. Create src folder -> db folder.
11. Create src folder -> db folder -> index.js file.
12. Create src folder -> middleware folder.
13. Create src folder -> models folder.
14. Create src folder -> routes folder.
15. Create src folder -> utils folder.
16. Create src folder -> app.js file.
17. Create src folder -> constant.js file.
18. Package.json file -> scripts -> "start": "nodemon index.js"
19. Terminal -> npm i bcrypt cookie-parser cors dotenv express jsonwebtoken mongoose @sendgrid/mail
20. Terminal -> npm i nodemon -D
21. Package.json file -> "type": "module",
22. Terminal -> npm run start
23. .env file -> MONGODB_URI = mongodb://127.0.0.1:27017/ReactFirst / Cluster
24. db folder -> Create new index.js file -> import mongoose from "mongoose";
    1. import { DB_NAME } from "../constant.”js;
    2. const connetDb = async () => {
    3. try {
    4. const connectionInstance = await mongoose.connect(`${process.env.MONGODB_URI}/${DB_NAME}`);
    5. console.log(`\n MongoDB Connected at ${connectionInstance.connection.host}`);
    6. } catch (error) {
    7. console.log(`MongoDB connection error`, error);
    8. process.exit(1);
    9. }
    10. }
    11. export default connetDb;
25. Src Folder -> app.js file -> import express from "express";
    1. import cors from "cors";
    2. const app = express();
    3. app.use(cors());
    4. app.use(express.json({limit : '16kb'}));
    5. app.use(express.urlencoded({extended : true, limit : '16kb'}));
    6. app.use("/", (req, res, next) => {
    7. res.status(200).json({message : "Prac Connected"})
    8. })
    9. export {app};
26. Root Folder -> index.js file -> import connetDb from "./src/db/“index.js;
    1. import { app } from "./src/app.js”;
    2. import dotenv from "dotenv";
    3. dotenv.config({
    4. path : './.env'
    5. });
    6. connetDb()
    7. .then(() => 
    8. app.listen(process.env.PORT || 8001, () => {
    9. console.log(`Server started at ${process.env.PORT}`);
    10. }))
    11. .catch(error => {
    12. console.log("MongoDB Connection Failed", error);
    13. })
27. Terminal -> npm run start
28. 
