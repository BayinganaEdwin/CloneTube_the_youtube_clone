# CloneTube - a YouTube clone


# Deploying the website

1. Build the app using this command ( npm run build) → This will generate a dist or build folder that will contain the files we can send on our server
2. Ssh into your web-01 and web-02
3. Git clone your project on both your web-01 and web-02
4. Create a new directory on your web-0/web-021 that will contain your distributable or build files ( mkdir -p /var/www/appname )
5. Copy all the files from your github repo to the new directory (sudo cp * /var/www/appname)
6. Set the right permissions for the new directory ( sudo chown -R www-data:www-data /var/www/appname then sudo chmod -R 755 /var/www/appname
7. Make sure you have nginx on 01 and 02
8. Configure Nginx to serve the new folder - sudo nano /etc/nginx/sites-available/default

```jsx
server {
    listen 80;
    server_name your_domain_or_ip;  # Replace with your domain name or server IP address

    root /var/www/appname;  # Root directory for your website
    index index.html;  # Default file to serve

    location / {
        try_files $uri $uri/ =404;  # Serve files or return 404 if not found
    }
}
```

1. sudo ln -s /etc/nginx/sites-available/ /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
2. Test if your app is properly served, by curling localhostgated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.


## Deployed Demo

- Visit [CloneTube 🔗](https://www.edwinbayingana.tech/)

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).
This is a React web-app designed as a YouTube prototype/clone, having its API data source as RapidAPI and built for education purposes

## Get Started

- Clone the repo `git clone [link]`
- Run `npm i` to get all the dependencies
- Run `npm start` to start the development server

## Project Gear

- React JS
- Material UI
- HTML
- CSS

## Scripts to Run

After tapping into this project's directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to open it up in your browser.

The page will reload when you make changes.\
Lint errors are displayed in the console and client side (browser) as well.

### `npm test`

Launches the test runner in the interactive watch mode.\
Check out the documentation on [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more details.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

Check out the documentation on [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more details.
