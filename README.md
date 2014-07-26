ubuntu-pgrouting-install
========================

    # Variables
    minx=-77.0604
    miny=38.9247
    maxx=-77.0413
    minx=38.9339
    
    # Install extra
    sudo apt-get install python-pip
    sudo apt-get install git
    
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
    mkdir $HOME/osmdata
    cd $HOME/osmdata
    wget -O mapdata.osm "http://api.openstreetmap.org/api/0.6/map?bbox=$minx,$miny,$maxx,$maxy"
    
    ./osm2pgrouting -file osmdata.osm \
                    -conf /usr/share/osm2pgrouting/mapconfig.xml \
                    -dbname routing \
                    -user gisi \
                    -clean
    
