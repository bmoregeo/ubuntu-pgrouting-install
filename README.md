ubuntu-pgrouting-install
========================
    # Install pgrouting
    sudo sudo add-apt-repository ppa:georepublic/pgrouting-unstable
    sudo apt-get update
    sudo apt-get install
    sudo apt-get install postgresql-9.3
    sudo apt-get install postgresql-9.3-postgis-2.1
    sudo apt-get install postgresql-9.3-pgrouting

    echo -e "host\tall\tall\t\t\t\t\t\ttrust" | sudo tee -a /etc/postgresql/9.3/main/pg_hba.conf
    sudo service posgresql restart

    # Setup osm
    sudo apt-get install python-pip
    
