A list of things to work on to enhance JAMon's benefit:

## Graphite Support

One of the major benefits of DropWizard Metrics over JAMon is the ability to publish metrics to Graphite.
http://graphite.readthedocs.org/
https://github.com/hopsoft/docker-graphite-statsd

Adding a Graphite Publisher would be very helpful.


## Gradle Build

Just because Gradle is much more agile these days.


## Spring Boot JAMon Starter

Creating this would allow Spring Boot apps to add JAMon with a simple dependency declaration
Might want one starter just for monitoring and a second to pull in the GUI
Ideally this would also support conditional discovery and registration of JAMon components
such as the JDBC, HTTP, and other monitoring like via JamonPerformanceMonitorInterceptor

http://stackoverflow.com/questions/28056736/annotation-based-usage-of-jamon-in-spring
```
@Component
public class MonitoringAdvisor extends AbstractPointcutAdvisor {

    private final StaticMethodMatcherPointcut pointcut = new StaticMethodMatcherPointcut() {
            @Override
            public boolean matches(Method method, Class<?> targetClass) {
                return targetClass.isAnnotationPresent(RestController.class);
            }
        };

    @Override
    public Pointcut getPointcut() {
        return this.pointcut;
    }

    @Override
    public Advice getAdvice() {
        return new JamonPerformanceMonitorInterceptor(true, true);
    }
}
```


## Percentiles Reporting

It would get great if there were at least the option to capture either a static or even better configurable
list of percentiles to capture with each monitor.


## JSON Export

Ideally JAMon stats should be able to be exported as JSON for consumption by APIs


## Logback support similar to Log4J

Since logback is the natural successor to Log4J



## Coherent Microservices and Cloud Configuration

Need to provide a blueprint for how to use JAMon in a cloud/microservice type environment.



## Dockerize JAMon GUI

Especially given the ability to pull data from multiple remote services, it would be great
if it were easy to spin up the JAMon GUI without necessarily having to embed it in each
monitored application.


## Automatic monitors for time intervals

In general, JAMon is extremely powerful for answering questions about what is happening
now and what has ever happened.  However, it is lacking the the ability to answer
what was happening between a given time interval in the past.  To sort of bridge that
gap, I've used various monitors like this at high level monitors in my applications.

byMin5
byHour
byDay

The result is that you can easily spot "spikes" at any point during the day.

Automatic reset of stats on a periodic basis





