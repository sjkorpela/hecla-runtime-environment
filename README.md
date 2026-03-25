# HE/CLA Runtime Environment #

Project description.

## How to run locally ##

Needs:
- Java 21+ to build
- npm/node to build
- Docker to build and run

### Setting up the backend ###

1. Clone the backend into this repository with command `git clone git@bitbucket.org:MikaJK/hecla-backend.git
` or similar methods.
2. Navigate into the `hecla-backend` directory.
3. Run command `./mvnw install` to install dependencies.
4. Run command `./mvnw clean package -DskipTests` to build a .jar file in the `hecla-backend/target` directory.

### Setting up the frontend ###

1. Clone the frontend into this repository with command `git clone git@bitbucket.org:MikaJK/hecla-frontend.git
` or similar methods.
2. Navigate into the `hecla-backend` directory.
3. Run command `npm install` to install dependencies.
4. Run command `npm run build` to build a standalone package in the `hecla-frontend/.next/standalone` directory.

### Building and running Docker images ###

Run the command `docker compose up --build` to build and run all relevant Docker images.

The Docker Compose environment builds images of the backend and the frontend through their individual Docker images,
defined in their repositories. These images need:
- `hecla-backend/target/hecla-backend-1.0.jar` to make the backend image.
- `hecla-frontend/.next/standalone`, `hecla-frontend/.next/static`, and `hecla-frontend/public` to make the frontend image.

### Setting up Keycloak ###

Once the Docker images have all started fully:
1. Open up the Keycloak admin panel at http://localhost:8080.
2. Log in with the temporary admin credentials, and then replace them with something secure.
   - Important: When creating a new admin account, be sure to enable relevant roles in the `Role mapping`, such as `admin`.
3. Create a new realm called `hecla` and set it as the current realm.
4. In the `Clients` section, create a client with:
   1. The client id as `public`
   2. PKCE method as `S256`
   3. The valid redirect URI as https://oauth.postman.io/v1/callback
5. In the `Users` section, add any users you may need.
   - Important: Add their password in the `Credentials` tab.




## Other ##

Run command `find -name .git -execdir git pull \;` to pull changes in both subdirectories.