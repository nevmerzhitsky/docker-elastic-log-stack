## Configuration

Firstly you need to create `logstash_internal` user to connect from logstash to elasticsearch else it cannot save parsed logs in elasticseatch. Next guide based on steps from article https://www.elastic.co/guide/en/x-pack/current/logstash.html

1. Run only kibana service: `docker-compose up -d kibana` (elasticsearch service will start automatically).
1. Go to http://localhost:5601/ (or IP of your Docker Machine) and auth by `elastic` with password `changeme`.
1. Create a `logstash_writer` role and a `logstash_internal` user as mentioned in the article. For the user use the password from file `logstash/pipeline/velvica-pipeline.conf` of this repo (section `output.elasticsearch`).

All required actions has been done, move to Running section.

## Running

Put some logs to local `logs` directory or make bind mount to `/var/beats_logs/` in `test-filebeat` container. Then just type `docker-compose up -d` to start all services and go to Discover section of Kibana: http://localhost:5601/ (or IP of your Docker Machine).
