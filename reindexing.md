```

GET _tasks?detailed=true&actions=*reindex

POST _tasks/_cancel?nodes=node_id&actions=*reindex

POST _reindex?slices=5
{
  "max_docs": 1744993,
  "source": {
    "index": "xxxxx",
    "size": 1000, 
    "query": {
      "match_all": {}
    }
  },
  "dest": {
    "index": "xxx"
  }
}

PUT /XXXXXXXXX/_settings
{
  "index" : {
    "refresh_interval" : "1s"
  }
}


PUT  messages
{
   "settings":{
      "number_of_shards":20,
      "number_of_replicas":1
   },
  
   "mappings" : {
      "properties" : {
        "outreach_time" : {
          "type" : "date",
          "format" : "yyyy-M-dd HH:mm:ss"
        }
      }
    }
}

GET abcd/_search
{
   "_source":"timestamp",
   "query":{
      "bool":{
         "filter":[
            {
               "range":{
                  "timestamp":{
                     "gte":"now-180d"
                  }
               }
            }
         ]
      }
   }
}

```
