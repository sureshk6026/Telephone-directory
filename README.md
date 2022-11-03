# Telephone-directory
CURD operation using the telephone directory document
#CURD operation using the python

import pymongo
from pymongo import MongoClient

client=pymongo.MongoClient('mongodb://localhost:27017/')
db=client["Telephone_directory"]
col=db["Document"]

#create operation

data= [{"name":"suresh","address":"no 158 india","phone":8939035008},
       {"name":"kumar","address":"no 159 india","phone":8939035009},
       {"name":"sureshkuamr","address":"no 160 india","phone":8929035008}
      ]

#create multiple document with separate obj_ids  
New_collecttion=col.insert_many(data)

#create one document and add it to collection
data_new={"name":"rabada","address":"no 10 south africa","phone":9034327398}
New_collection1=col.insert_one(data_new)

#read operation

for i in col.find():
    print(i)
myquery={}
for i in col.find(myquery):
    print(i)

#update operation

#it upddates all the occurrences
col.update_many({"name":"rabada"},{"$set":{"phone":8939035008}})
for i in col.find():
    print(i)

#it update the first occurrence
col.update_one({"name":"rabada"},{"$set":{"phone":9750667890}})    
for i in col.find():
    print(i)

#delete operation

#delete the first occurance
col.delete_one({"name":"rabada"})
for i in col.find():
    print(i)
    
#delete all the occurrances
col.delete_many({"name":"rabada"})
for i in col.find():
    print(i)
