1 - install vagrant
2- run  vagrant init ubuntu/trusty64
3 - vagrant up
4 - vagrant ssh
5 - sign up for datadog
6 - download MongoDB Community v3.6 via apt (https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)
7 - INstall DD Ubuntu agent (DD_API_KEY=4aff808b0967a016d2d255add8640996 bash -c "$(curl -L https://raw.githubusercontent.com/DataDog/datadog-agent/master/cmd/agent/install_script.sh)")
8 - make data directory for MongoDB - sudo mkdir /data/db
9 - create conf.yaml file in /etc/datadog-agent/conf.d/mongo.d/
10 - restart agent - sudo service datadog-agent restart
11- Custom Check:
	in ...datadog-agent/conf.d/my_metric.conf
  CODE:   init_config:

          instances:
               [{}]
  in...datadog-agent/checks.d/mymetric.py
        from checks import AgentCheck
        from random import randint
        class HelloCheck(AgentCheck):
           def check(self, instance):
           self.gauge('my_metric', randint(0,1000))
  
