# tanshuai notes

## Install Problems

### Error on MacOS "You need Python 3.7 or greater installed and mapped to the 'python' command"

ln -s -f /usr/bin/python3 /usr/local/bin/python

### Postgres is not ready ... FATAL:  database "vasp_backend_db" does not exist

Logs:
```
vasp-backend-web_1     | [2021-07-06 09:50:17,125] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:17.869 UTC [88] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:17,870] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:18.132 UTC [89] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:18,132] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:18.876 UTC [90] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:18,876] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:19.139 UTC [91] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:19,139] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:19.881 UTC [92] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:19,881] WARNING in __init__: Postgres is not ready, waiting...
db_1                   | 2021-07-06 09:50:20.144 UTC [93] FATAL:  database "vasp_backend_db" does not exist
vasp-backend-web_1     | [2021-07-06 09:50:20,144] WARNING in __init__: Postgres is not ready, waiting...
vasp-backend-web_1     | [2021-07-06 09:50:20,882] ERROR in __init__: Database failed to start, exiting...
vasp-backend-web_1     | [2021-07-06 09:50:21,146] ERROR in __init__: Database failed to start, exiting...
```

Solution: Open Terminal of this Docker to run `backend.sh`.


> **Note to readers:** On December 1, 2020, the Libra Association was renamed to Diem Association. The project repos are in the process of being migrated. All projects will remain available for use here until the migration to the new GitHub Organization is complete.

# Reference Merchant

Reference Merchant is an open-source project aimed at demonstrating integration of 
payments into an existing e-commerce solution. We tried to incorporate both technical and design
aspects not only to show how the different technical pieces fit together, but also demonstrate
thoughtful design, content, and best experience practices.


## Note to Developers

* Reference Merchant is a reference implementation, and not meant to be fully production grade.
* The project will continue to develop to include the different aspects of the evolving developer ecosystem.


## Project Organization

The project is separated into the following components:
* [Merchant](/merchant) - e-commerce website mock.
* [VASP](/vasp) - VASP fulfilling the merchant's payment requests.
* [Gateway](/gateway) - Nginx server routing requests to the various system components.
* [Liquidity](/liquidity) - Liquidity provider mock implementing simple liquidity functionality.
    This piece should be replaced by a service that provides your organization with needed
    liquidity functionality.


## Getting started

The project uses Docker containers to run its components. The containers are orchestrated using
docker-compose.

**System Requirements:**
* docker and docker-compose - Docker can be installed from the [web](https://www.docker.com/products/docker-desktop). If you are installing Docker for the first time on your system, be sure to run it at least once to have it configure itself and get `docker-compose` as a runnable command.
* python 3.7
* yarn
* react-scripts
* macOS: xcode cli tools  ```xcode-select --install```

Run the following commands in the repository root:
```shell script
scripts/lrm.sh setup_environment
scripts/lrm.sh build
scripts/lrm.sh develop
```

The merchant website will be available at http://localhost:8000

See `docker/docker-compose.yaml` for the setup details.
