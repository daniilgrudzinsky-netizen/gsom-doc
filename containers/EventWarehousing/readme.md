### Code location:
`reportetl:src/services/EventWarehouse`

### Components
 
![image info](./Components.png)

#### DB

![image info](./ERD_EventWarehousing.jpg)


Tables `BetEvents` and `CurrencyOperations` are columnar tables. They are sharded (per gambling organizer - to control over performance) and particioned (by month - to drop the data once it's no longer required for compliance purposes).