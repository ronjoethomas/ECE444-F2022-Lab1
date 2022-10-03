# Education_Pathways

This is a modified version of the previous Assignment1 template by Ron Thomas.


**Activity 2**
![image](https://user-images.githubusercontent.com/59146858/193521255-4661168f-6912-4551-95ba-b4b4fef357c6.png)

**Activity 3**
![image](https://user-images.githubusercontent.com/59146858/193521321-93f6c6ed-79cd-4d54-96dd-0987d6e908c2.png)

**Activity 4**
![image](https://user-images.githubusercontent.com/59146858/193521380-a8c6bddb-84c3-4ef8-88c9-a97833fe1ae0.png)
![image](https://user-images.githubusercontent.com/59146858/193521426-4d567ce8-190d-4933-b311-4307f67f5af5.png)


The deployed version can be found at https://lab3-docker.herokuapp.com.

## Changes

- Removed hardcodes of backend urls.
- Removed hardcodes of database, and replace the database with dummy static data.

## How to run it locally

- Enter the repo directory
- Create a virtual environment if you haven't done this before. Activate it.

```powershell
# Windows
py -3 -m venv venv
venv\Scripts\activate

# For Mac and Linux, please check the link: https://flask.palletsprojects.com/en/2.2.x/installation/
```

- Install dependencies (if you haven't done this before).

```powershell
pip install -r requirements.txt
```

- Enter the `Education_Pathways/` directory, run the backend

```powershell
flask --app index --debug run
```

- Enter the `Education_Pathways/frontend/` directory
- Make sure the `baseURL` is set as `localhost:5000`

```javascript
# Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "http://localhost:5000/"
});
```

- Make sure the proxy link in package.json is set as "http://localhost:5000/"

```json
// Part of Education_Pathways\frontend\package.json
"private": true,
"proxy": "http://localhost:5000/",
```

- Build and run the frontend:

```powershell
npm run build
npm start
```

- Then you will see the application at `localhost:3000`

## Build and run with Docker

For detailed instructions on Docker, please refer to the documents for Lab3 on Quercus.

- Change the proxy link in package. Remember to change it back to "http://localhost:5000/"

```json
// Part of Education_Pathways/frontend/package.json
"private": true,
"proxy": "http://host.docker.internal:5000/",
```

```powershell
# Under the root directory
docker compose up --build
```

## How to deploy (not required for lab3)

Please make sure everything works well before you run it with docker.

- Make sure the baseURL is set as [URL to your deployed project]

```javascript
// Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "[URL to your deployed project]" -- baseURL for deployment
});
```

- Re-build the frontend to update the baseURL

```powershell
# Under the frontend/ directory
npm run build
```

- Deploy your changes to heroku

```powershell
git push heroku main
```
