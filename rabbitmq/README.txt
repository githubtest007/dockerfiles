Examples:

# Run without TLS
docker run -d \
  --name rabbitmq \
  -p 5672:5672 \
  -p 15672:15672 \
  gonkulatorlabs/rabbitmq
# Run with TLS enabled
docker run -it \
  --name rabbitmq \
  -p 5671:5671 \
  -p 15671:15671 \
  -e SSL_CERT_FILE=/ssl/cert/cert.pem \
  -e SSL_KEY_FILE=/ssl/cert/key.pem \
  -e SSL_CA_FILE=/ssl/CA/cacert.pem \
  gonkulatorlabs/rabbitmq
# Run with autoclustering enabled
#   These options will register the RMQ
#   node as living on 192.168.99.101.
#   Nodes that join will attempt to cluster
#   on that address.
docker run -d \
  --name rabbitmq \
  -e AUTOCLUSTER_TYPE=consul \
  -e CONSUL_HOST=192.168.99.101 \
  -p 5672:5672 \
  -p 15672:15672 \
  gonkulatorlabs/rabbitmq