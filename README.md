# nightingale-workbench

This repository includes a docker-compose configuration that allows you to quickly spin up a copy of [Nightingale](https://github.com/nightingaleproject/nightingale) and the [SMART on FHIR Death Certification app](https://github.com/nightingaleproject/fhir-death-refactor) using Docker + Docker Compose for **experimental purposes**.

On startup:

Nightingale is accessable at `http://localhost:80` (or `http://docker-container-ip:80`, if using Docker Toolbox). This address includes the FHIR endpoint (`http://localhost:80/fhir/v1/death_records.json`), for GETing and POSTing FHIR death records.

The SMART on FHIR Death Certification app is accessable at `http://localhost:81` (or `http://docker-container-ip:81`, if using Docker Toolbox).

## Deployment Instructions

Start by cloning this repository (if on Windows, I'd suggest using Git BASH from Git for Windows):

```
git clone https://github.com/nightingaleproject/nightingale-workbench.git
```

Change into the newly cloned repository:

```
cd nightingale-workbench
```

Start up the Docker configuration:

```
docker-compose up
```

In another console window (**but in the same directory!**):

```
docker-compose run nightingale bundle exec rake db:create db:migrate
```

And then:

```
docker-compose run nightingale bundle exec rake nightingale:demo:setup
```

That's it!
