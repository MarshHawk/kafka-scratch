```
helm repo add strimzi https://strimzi.io/charts/

helm upgrade --install kafka strimzi/strimzi-kafka-operator -n kafka

kubectl apply -f ./k.yaml

kubectl run -n kafka kafka-producer -ti --image=quay.io/strimzi/kafka:latest-kafka-3.4.0 --rm=true --restart=Never -- bin/kafka-console-producer.sh --bootstrap-server kafka-cluster-kafka-bootstrap:9092 --topic my-topic

kubectl run -n kafka kafka-consumer -ti --image=quay.io/strimzi/kafka:latest-kafka-3.4.0 --rm=true --restart=Never -- bin/kafka-console-consumer.sh --bootstrap-server kafka-cluster-kafka-bootstrap:9092 --topic my-topic --from-beginning
```