# Difference between Block Storage and Object level storage
1. Block level is suitable for transactional database     1. Object storage store file as it is , it will
read and write operation, structured databse                 not devide your file.

2. It devide data into evenly sized block (chunks)        2. In object storage, object can be
for instance a file can be split into evenly size block      --the filr/data itself
befor it get stored.                                         -- Its metadata
                                                             -- the object global unique ID

3. Data block that stored in block storage would          3. Global unique id is unique identifier(          
not contain metadata.                                                           can be object name) and it must be unique                 
4. Block storage only keeps the address(index)            4. Object storage cannot mount as drive
where the data blocks are stored.                             where as block storage can be use as cdrive

5. we treat as block.                                     5. we treat as object
EX- EBS                                                      EX- AWS S3, Dropbox

# Elastic Block Store
Whenever we are creating EC2 machine, the volume we are getting with ec2 machine are called as root/boot volume also called as EBS volume.

EBS volume are persistent volume mean whenever you stop or reboot your Ec2 instance, your data will not delete. Your data will only delete in case of termination of EC2 instance.

Whenever we craete new volume and attached to EC2 instance then delete on termination will be off by default.

