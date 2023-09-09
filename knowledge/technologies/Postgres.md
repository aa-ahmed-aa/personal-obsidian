Materialised views (more details https://www.postgresql.org/docs/current/rules-materializedviews.html)
are just like views with some small differences: 
- materialised views are like tables but much more faster and like views in how you create them but also much faster than views
- need to be refreshed from time to time or should be scheduled as a job somewhere 

see also
- [[pgbench]]
- [[check if identity is set to full on postgress table]]
- [[stats of index usage]]
- [[stats of actions of tables]]
- [[List table indeces postgress]]