
CLoud pub sub
- scalable(upto billions of msgs/day), fully managed, low cost, 
- topics, subscription
- publisher puts msg to topic using https request
- type Pull/push - push means send post request to an http endpoint which is consumer
- msg sent to all subcriptions - from subscription - clients take and process tasks - and acknowledge once done
- All are supported: One to one, One to many, many to one, many to many

can set:
- message retention days
- subscription expire due to inactivity for days
- time for acknowledgement (def: 10sec)
- filter for subscription
- message ordering
- dead letter queue
- retry policy

can take snapshot of a **subscription** - with current state


- zonal - lite pub sub - optimise cost

gcloud pubsub topics/subscriptions