## https://prometheus.io/docs/guides/node-exporter/

## Download Node Exporter

```bash
wget https://github.com/prometheus/node_exporter/releases/download/v1.7.0/node_exporter-1.7.0.linux-amd64.tar.gz
```

## Extract the Contents
```bash
tar xvf node_exporter-1.7.0.linux-amd64.tar.gz
```

## Move the Node Exporter Binary
```bash
cd node_exporter-1.7.0.linux-amd64
sudo cp node_exporter /usr/local/bin
rm -rf ./node_exporter-1.7.0.linux-amd64
```

## Create a Node Exporter User
```bash
sudo useradd --no-create-home --shell /bin/false node_exporter
sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter
```

## Configure the Service
```bash
sudo mv ./node_exporter.service /etc/systemd/system/
```

## Enable and Start the Service
```bash
sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter.service
```

# Add Private EC2 to Prometheus

## Move Node Exporter to Private EC2
```bash
scp -i <path-keypair> node_exporter-1.7.0.linux-amd64.tar.gz ubuntu@<private-ip>:/home/ubuntu/
```

## How to install and configure Node Exporter on AWS EC2: https://youtu.be/n4wTONEVz-A?si=8yP1-uEBkYIwLH8W
