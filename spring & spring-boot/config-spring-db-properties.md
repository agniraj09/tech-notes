**KEY
DATA TYPE
POSSIBLE VALUE
DEFAULT VALUE
DEFINITION**
-
**spring.jpa.show-sql**\
Type : boolean\
Values : true/false\
Default : false

>Determines whether to log SQL queries in console or not. Logs the queries if set to true.
---
**spring.jpa.open-in-view**\
Type : boolean\
Values : true/false\
Default : true
> Creates session for each request and keeps the session active till request is fulfilled/processed. If this option is enabled, any update in entity could be saved without even using @Transactional. This might cause some unexpected issues which are difficult to be traced. It's always better to keep it false and handle the transaction manually.\
> https://medium.com/@rafaelralf90/open-session-in-view-is-evil-fd9a21645f8e
---
**spring.data.jpa.repositories.bootstrap-mode**\
Type : string/enum\
Values : default, lazy, deferred\
Default : default
> 1. default  : Registers and initializes repositories eagerly. Before application is started.\
> 2. lazy  : Registers repositories eagerly but does not initialize them. Initialization happens at first use(after application started)\
> 3. deferred  : Registers and initializes repositories after application is started.\
> https://www.baeldung.com/jpa-bootstrap-mode
---
**spring.datasource.hikari.auto-commit**\
Type : boolean\
Values : true/false\
Default : true
 > If enabled, without the need of @Transaction or manual commit, spring commits each and every transaction/update happens to an entity object. This makes developer life easy to not bother about commit but will be problematic if we have more than one dependent DB calls. It's always better to keep it false and handle the transaction manually.\
> https://www.baeldung.com/java-jdbc-auto-commit
---
**spring.jpa.hibernate.ddl-auto**\
Type : string/enum\
Values : create, create-drop, update, validate, none\
Default : If no schema manager provided -> create-drop, else none
> 1. create -> Hibernate drops existing tables and creates new tables\
> 2. create-drop -> Creates tables and drops them when processing is completed. Used in test cases.\
> 3. update -> Updates existing tables but does not delete the existing tables or columns.\
> 4. validate -> Just validates if all tables exist or not.\
> 5. none -> Does nothing
---
**spring.jpa.properties.hibernate.generate_statistics**\
Type : booleanv
Values : true/false\
Default : false
> Collects statistics for each entity manager and also adds loggers for each SQL execution. Could be time and resource consuming hence advised to turn it off in PROD.
---
**spring.jpa.properties.hibernate.jdbc.batch_size**\
Type : integer\
Values : Any positive value\
Default : No default value. Batching is ignored if value is not set.
 > This property represents the number of statements that hibernate will group together before asking driver to execute them. For example, if 100 entities are saved and if batch size is 20, only 5 calls/queries will be made to save them all. If no value is mentioned, 100 queries would have executed.
---
**spring.jpa.properties.hibernate.order_inserts**\
Type : boolean\
Values : true/false\
Default : false
 > If this value is set, and when a large number complex/hierarchical entities are saved in single session, hibernate sorts the entities by type and primary key and then saves them in order. This improves performance as it does not have to validate the entities with primary key when it saves in normal mode.
---
**spring.jpa.properties.hibernate.order_updates**\
Type : boolean\
Values : true/false\
Default : false
>If this value is set, and when a large number complex/hierarchical entities are updated in single session, hibernate sorts the entities by type and primary key and then updated them in order. This improves performance as it does not have to validate the entities with primary key when it updates in normal mode.
---
**spring.jpa.properties.hibernate.query.fail_on_pagination_over_collection_fetch**\
Type : boolean\
Values : true/false\
Default : false
>In Hibernate when we use pagination, it fetches large dataset calls collection and then tries to paginate the results. This would consume lot of in-memory as entire collection is fetched. If the flag is set to true, it would throw an exception when hibernate tries to do the same. Either we need to fetch less data or tweak fetching logic to avoid this exception.
---
**spring.jpa.properties.hibernate.query.in_clause_parameter_padding**\
Type : boolean\
Values : true/false\
Default : false
>This is used for IN clause parameter padding. When we have an IN clause that actually will have 3 values, if this config is set to true, hibernate will add extra placeholder in power of 2. The additional placeholders will be filled with last value of input. Hibernate does this so that DB can use same execution plans for similar queries. This results in better performance. Also this does not work with native queries. It works only when Hibernate generates the query
---
**spring.jpa.properties.hibernate.query.plan_cache_max_size**\
Type : integer\
Values : Any positive value\
Default : 2048
>Whenever a query is executed, it has to be first compiled and a query plan needs to be prepared before executing it. This is a time consuming process. So if we can store the compiled version in cache, if same query is executed again, it will reduce the time and increase performance. This config is used to tell how many number of unique compiled queries need to be stored in cache. 
---
**spring.jpa.properties.hibernate.connection.provider_disables_autocommit**\
Type : boolean\
Values : true/false\
Default : false 
>Normally, the auto commit value/behavior of a connection is set in 2 places. First one where the connection is created in pool. This is at JDBC level. Second one is when Hibernate acquires the connection from pool. This is at Hibernate level. If connection is created with auto commit as true but this config is set as true, it basically disables the auto commit behavior a connection. To make sure auto commit is disabled in both levels, this and hikari auto commit should be set to proper values.
---
**spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation**\
Type : boolean\
Values : true/false\
Default : false
 > This tells hibernate to create large objects outside of transactional context to improve performance and avoid errors.
 ---
