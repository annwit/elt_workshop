# Data platform workshop
Materials for the "Building a modern data platform with Python and open-source tools" workshop.

## Pre-workshop set up
We'll be using Prefect Cloud, GitHub, and Docker during the workshop. To save everyone's time, please make sure you have at minimum Git + Docker with Airbyte images set up before we begin (as it needs to download quite a lot of data).

### 1. Install Git
[LINK](https://git-scm.com/downloads)

### 2. Set up GitHub
- create a Personal Access Token: [LINK](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- make GitHub remember the credentials: `git config --global credential.helper store`
- pull the [ELT workshop](https://github.com/dyvenia/elt_workshop) repo and provide the generated token as password: `git clone https://github.com/dyvenia/elt_workshop.git`

### 3. Install Docker
- Windows/Mac: [LINK](https://docs.docker.com/get-docker/)
- Linux: [LINK](https://docs.docker.com/engine/install/#server)

### 4. Install docker-compose
> **NOTE** Only required on Linux
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

### 5. Set up Airbyte
Run the following commands:
```
git clone https://github.com/airbytehq/airbyte.git
cd airbyte
docker-compose up
```

Once you see an Airbyte banner, the UI is ready at `localhost:8000`.

This concludes the set up. Execute `docker-compose down` to spin down Airbyte.

## Workshop set up
### 1. Set up Prefect Cloud
- go to https://cloud.prefect.io
- register for the "Starter" plan
- **Note: you will need to provide your credit card details** (they have 20,000 task runs/month free tier, which for personal and educational use is basically infinite. It's also very easy to delete the account after the workshop.)
- create an API key:
    - click on the face logo in top right corner, then Account Settings -> API Keys
    - click "CREATE AN API KEY"
    - choose a name, eg "dyvenia_elt_workshop"
    - choose an expiration date (for us a month is enough)
    - click "CREATE"
    - provide the token as the value of `auth_token` in .prefect/config.toml.EXAMPLE and rename the file to config.toml
