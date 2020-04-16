# Monica Jupyter Notebooks connected to a GOST database
<!-- Short description of the project. -->

This is a docker compose which allows to connect Jupyter Notebooks to a gost Database filled with Monica's demonstation content.

You can read with it: Sound Heat Maps, Density Heat Maps and Trackind ID. 

In this example, the dump files was already created from Woodstower Festival data with the help of gost-db-dump-dummy. 
That app is a version of gost-db-dump adapted for when the observation table is really huge and you want only a part.

0. Show how this version of Jupyter Container and its dependencies was built. IT happens that the new version of Jupyter Client failed for some reasons 
so we downgraded it with the command: RUN conda install -c anaconda jupyter_client=5.3.1

```bash
docker-compose build
```

1. Create a Network. It is necessary to control the gateway.

```bash
docker network create --gateway 192.168.0.1 --subnet 192.168.0.0/24 reseau
```

2. Create the Gost Database Container. You need to authorize docker to write in our local disk ( settings/shared drives)

```bash
docker-compose up -d gost-db
```

3. Run Jupyter Notebooks and Copy the link with the TOKEN

```bash
docker-compose up notebook
```

4. In the notebook, run everything with the Cell tab 
## Contributing
Contributions are welcome. 

Please fork, make your changes, and submit a pull request. For major changes, please open an issue first and discuss it with the other authors.

## Affiliation
![MONICA](https://github.com/MONICA-Project/template/raw/master/monica.png)  
This work is supported by the European Commission through the [MONICA H2020 PROJECT](https://www.monica-project.eu) under grant agreement No 732350.
