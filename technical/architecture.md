## AWS Regions, Availability Zones and Edge Locations explained

Link: https://www.experts-exchange.com/articles/18666/AWS-Regions-Availability-Zones-and-Edge-Locations-explained.html

#### Keyworks:
- Geographical components:
    - Regions
    - Availability Zones
    - Edge Locations
- Region: a geographic location that Amazon has selected to run and operate its Cloud services from.
- Availability Zone:           
    - Different Data Centres located within a Region.
    - Each AZ is completely independent of others which enable them to reside in different areas within the same Region providing a level of Business Continuity in the event of a disaster.
    - All AZ's within the same region are linked by extremely low latency connections.
- Edge locations: 
    - Used in conjunction with the AWS CloudFront service (a global CDN) to reduce latency for traffic served over CloudFront.
    - Independent of Regions and AZs.


## Scaling to 11 Million + Users

Link: http://highscalability.com/blog/2016/1/11/a-beginners-guide-to-scaling-to-11-million-users-on-amazons.html

#### Keywords:
- Knowledge:
    - Start with SQL and only move NoSQL when necessary.
    - A consistent theme is take components and separate them out. This allow those components to scale and fail independently
    - Scalability and redundancy are not two separate concepts, you can often do both at the same time.
- Database:
    - SQL is enough to serve first 10 million users. Scale with master-slave architecture (one write, many read).
    - NoSQL is needed for:
        - > 5 TB of data in year
        - incredibly data intensive workload, low-latency required
        - high throughput, tweak the IOs both on the reads and the writes
        - don't have any relational data
    - Apply Cache in front of database.
    - A issue with one write, many read is it could only send so much write traffic to one server. 
        - Federation:
            - Splitting into multiple DBs based on function.
            - **Downsides**: can't do cross database queries.
        - Sharding:
            - Splitting one dataset accross multiple hosts by id.
        - Moving some functionality to other type of DBs:
            - Data that doesn't require complex joins.
- Decouple Infrastructure:
    - Use SOA/microservices that are independent with of each other. So they can be scaled or fail independently of each other.