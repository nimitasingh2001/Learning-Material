# Scalability

As an application grows, the load on it grows too: more users, more data, more requests per second. A design that worked for a thousand users may not work for a million, and a database that served a hundred queries per second may not serve ten thousand.

This is where **scalability** becomes critical.

> Scalability is the ability of a system to handle increased load by adding resources. The key word here is "ability", a scalable system can grow to meet demand without requiring a complete architectural overhaul.

## Measuring Scalability

Before scaling, you need to understand how to measure it. You cannot improve what you do not measure, and vague statements like "we need to scale" are useless without concrete numbers.

Scalability is typically evaluated along these dimensions:

### Load Metrics

| Metric | Description | Example |
|:--------|:------:|------:|
Requests per second (RPS) |	Number of API calls the system handles |	10,000 RPS |
Concurrent users | Users active at the same time |	50,000 concurrent |
Data volume |	Amount of data stored or processed |	10 TB storage |
Throughput |	Data transferred per unit time |	1 GB/s |
Query rate |	Database queries per second |	50,000 QPS |
Message rate |	Messages processed through queues |	100,000 msg/s |

### Performance Under Load
A system scales well if it maintains acceptable performance as load increases. Here is what good and bad scaling looks like:

| Load Increase|	Response Time	Behavior |	What It Means |
|:--------|:------:|------:|
1x | (baseline)	50ms |	Baseline	|	Normal operation |
2x	| 55ms	|	Excellent |	Sublinear growth, caching working well |
5x	|	70ms	|	Good	|	System handling load efficiently |
10x	|	150ms	|	Acceptable	|	Linear degradation, predictable |
10x	|	500ms	|	Concerning	|	Superlinear degradation, bottleneck forming |
10x	|	Timeout	|	Critical	|	System at breaking point |

> The goal is to keep performance relatively stable as load increases. Ideally, you want linear or sublinear degradation, where doubling load does not double response time. When response times spike or the system starts timing out, you have hit a scalability wall.
