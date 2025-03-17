# synechron_15th

```

Welcome to OpenDev Etherpad!

my name is raman khanna..


https://github.com/ramannkhanna2/synechron_15th.git


bigdata : vs :  
    volume , velocity , variety
    
    
    compute :
    
    collection /ingestion stage  :
        kinesis stream ,firehose 
        
        storage stage :
        s3 , ebs 
        
        data processing services
        
        raw >>> some meaningful format : data cleaning  / data transformations  
        
        emr , glue 
        
        
        
    data warehousing services like redshift : analyze the data 
    


cloud itself , aws , ec2 , autoscaling , cli




cloud : rent the services :
    
    
    
    application as a business owner : 10000 users 
        
        requirement : 
            platform/machine of deployment : servers , storage , maintennace , routers , swtches  : cant purchase
            code 

costly  cost by seconds : cant purchase 



2004 /2006 : aws cloud 

renting their infra components as web services 



public/private :
    
    hybrid cloud :
    
    busines owner : private datacentre >>>>>>>>>>>>>>>>>> cloud migration to aws   :  netwrkin , compute 
    
    storage : s3 advantage on public cloud ( unlimited storage by aws ) 
    
    
    
    
    
    
    
    
    
    
    
    deployment platform >>> ec2 as the compute
    
    devloped code >> build the code and create the atefact >> deployong on a server
    
    
    
    ram , processing power( CPU )
    
    load testing ......
    
    -- what tyupe of application it is
    -- how big my application  is 
    -- user trafiic 
    
    
    
    
    machine : ip 
    
    server : serves something / adds a functionality to the machine  : 1 gb ram , 1 cpu 
    
    
    machine >> add a data base applictaion : db server 
    
    machine >> linux applicayion >> linux server
    
    us-east-1
    
    ec2 service : manage virtual servers in aws cloud 
    
    
    
    
    machine >> empty node >> install software configuration : (  operating system +added fucntionalty ) : ami
    
    ubuntu 24 : ami
    
    t2.micro : inst type
    
    security group / firewall :  raman-sg
    
    =======================================
    
    
    - auth to to my account
             gui /management console 
             aws cli 
             cdk/sdk
             
  
    
    
    
    -----------------------------------
    server create :
    
    connect to my instanc :
    -- web connect
    -- ssh client    ( cmd , powershell , custom terminal like moba xterm , gitbash )

    
    ============================================
    
    advantage : 
    

    predictable and unpredictable bursting : aws cloyud : auto scaling group 
    makes my application scalable to a very large extent
    multiple data centres

-- upper cap
-- stop and start intance


============================================

-- go to auto scaling group under ec2 :
    
    -- create a launch template
    
    
        --- ami : ubuntu24
        keypair : reuse ur previous one
        security group : existing
        
        -- click on create launch template
        
        
    groupsize : 1
    limit : 1 to 10 
        

------------------------------
  -- launch template :
      -- modifu=y laucnch template
         -- resource tags :
             Name: raman-synechron-servers
             
-- 

=============================================

manual scaling up and down :
    
   
    
    autimated scaling : thrershold such as cpu load 
    
     scaled ur inst down to 1 ...
    
    asg >> automatic scaling >>> dynamic policy >> set the threshold as 60 % avergae load 
    
    
    
    
    --- now i will mimic the load increse ....and wil continouskky increase the load 

-- go to the ec2 instance >>> monitoring >>> cpu utlization metrics >> view in metrics 

--n connect to the main instance >> stress the cpu ...
  
   apt update -y
   apt install stress -y
   
   
   --- now see instances scale up and down automatically


real time / near real  time 
collection   >> stirage s3 , ebs >>   processing : data transformation     >> warehouse  


=======================
-- kinesis stream 
  -- created a stream
  
  -- opened cloudshell
  
  
   aws help
    8  aws ec2 help
    9  aws ec2 describe-instances --region us-east-1
   10  clear
   11  aws ec2 describe-instances     --region us-east-1     --query 'Reservations[*].Instances[*].InstanceId'     --output table
   12  aws ec2 describe-instances     --region us-east-1     --query 'Reservations[*].Instances[*].[InstanceId, PublicIpAddress, InstanceType]'     --output table
   13  aws ec2 describe-instances     --region us-east-1     --filters "Name=instance-state-name,Values=running"     --query 'Reservations[*].Instances[*].[InstanceId, InstanceType, PublicIpAddress]'     --output table
   14  history
[root@ip-10-132-52-126 ~]# 


-----------------------------------------------------

5 shards in total :

3 records :
    
aws kinesis put-record --stream-name raman-kinesis-stream --partition-key user1 --data "user signup" --cli-binary-format raw-in-base64-out

aws kinesis describe-stream --stream-name raman-kinesis-stream



aws kinesis put-record --stream-name raman-kinesis-stream --partition-key user1 --data "user login" --cli-binary-format raw-in-base64-out

aws kinesis get-shard-iterator --stream-name raman-kinesis-stream --shard-id shardId-000000000000 --shard-iterator-type TRIM_HORIZON


aws kinesis get-records --shard-iterator "AAAAAAAAAAGl6cvZBj8RaXoY9Tsz4n9raJizxiIyQge1JWa126v1mvSDnMVi1mhD3Y3qrnk8woD0fJQizLi4WOK3N9tInC2OOkxobUUDEL4pGnXPuh+SVSi+5ap9M60tCf1mu/1V673VYsbPvP6QvrJ4EhWwaU1JCmWa3AeiH10fq7R2ikKRdZtQgGsuV2efCEScuxTNeyZILleZSQA7pPGEIEh2qMtaSVxz2SzxYrhmI1Huq1DX22HIa0EYn4dfUSWgcCiinz8="

aws kinesis put-record --stream-name raman-kinesis-stream --partition-key user1 --data "user activity" --cli-binary-format raw-in-base64-out


aws kinesis get-records --shard-iterator "AAAAAAAAAAGl6cvZBj8RaXoY9Tsz4n9raJizxiIyQge1JWa126v1mvSDnMVi1mhD3Y3qrnk8woD0fJQizLi4WOK3N9tInC2OOkxobUUDEL4pGnXPuh+SVSi+5ap9M60tCf1mu/1V673VYsbPvP6QvrJ4EhWwaU1JCmWa3AeiH10fq7R2ikKRdZtQgGsuV2efCEScuxTNeyZILleZSQA7pPGEIEh2qMtaSVxz2SzxYrhmI1Huq1DX22HIa0EYn4dfUSWgcCiinz8="


decode that base 64 data at the end ....

===============================================================


kinesis streams >>>>> kinesis firehose ( batches) near time  >>> s3 ( data lake) , redhsift , spliunk  >>> processing service

=======================================================


Firehose ---- s3 demo (collecion)near real time

- create a firehose deliver stream (direct_put) : PurchaseLogs

- create an s3 bucket : orderlogss

while creatig my firhse stream :
    
s3 bucket prefix :
year=!{timestamp:yyyy}/month=!{timestamp:MM}/day=!{timestamp:dd}/hour=!{timestamp:HH}/

s3 bucket error output prefix:
fherroroutputbase/!{firehose:random-string}/!{firehose:error-output-type}/!{timestamp:yyyy/MM/dd}/

- enable delievery stream

===

- create an ec2 instance , amazon linux..
yum install aws-kinesis-agent -y
sudo service aws-kinesis-agent start
sudo service aws-kinesis-agent status


wget http://media.sundog-soft.com/AWSBigData/LogGenerator.zip

unzip LogGenerator.zip

chmod a+x LogGenerator.py

mkdir /var/log/cadabra (as per the py script)



---- modify below conf file as below :

[root@ip-172-31-30-73 aws-kinesis]# cat /etc/aws-kinesis/agent.json
{
  "cloudwatch.emitMetrics": true,
  "kinesis.endpoint": "",
  "firehose.endpoint": "firehose.us-east-1.amazonaws.com",

  "flows": [
    {
      "filePattern": "/var/log/cadabra/*.log",
      "deliveryStream": "PurchaseLogs"
    }
  ]
}


--- run the agent :

systemctl start aws-kinesis-agent
OR 
service aws-kinesis-agent start


chkconfig aws-kinesis-agent on


---- give your ece instance a role to access other services :

assign the role to instance


---- run the script to generate logs on server  : 500000 orders

tail -f /var/log/aws-kinesis-agent/aws-kinesis-agent.log
tail -f  /var/logs/cadabra/
sent the logs to s3

============================================================



```
