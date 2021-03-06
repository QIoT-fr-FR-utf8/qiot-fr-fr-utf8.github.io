# QIoT Edge Service

* TOC
{:toc}

## How it works


### Class Diagram

[![](https://mermaid.ink/img/eyJjb2RlIjoiY2xhc3NEaWFncmFtXG4gICAgU2Vuc29yIDx8LS0gUG9sbHV0aW9uUmVzdWx0XG4gICAgU2Vuc29yIDx8LS0gR2FzUmVzdWx0XG4gICAgU2Vuc29yIDogK2ludCBzdGF0aW9uSWRcbiAgICBjbGFzcyBQb2xsdXRpb25SZXN1bHR7XG4gICAgICArU3RyaW5nIGluc3RhbnRcbiAgICAgICtJbnRlZ2VyIFBNMTBcbiAgICAgICtJbnRlZ2VyIFBNMTBfYXRtXG4gICAgICArSW50ZWdlciBQTTFfMFxuICAgICAgK0ludGVnZXIgUE0xXzBfYXRtXG4gICAgICArSW50ZWdlciBQTTJfNVxuICAgICAgK0ludGVnZXIgUE0yXzVfYXRtXG4gICAgICArSW50ZWdlciBndDBfM3VtXG4gICAgICArSW50ZWdlciBndDBfNXVtXG4gICAgICArSW50ZWdlciBndDEwdW1cbiAgICAgICtJbnRlZ2VyIGd0MV8wdW1cbiAgICAgICtJbnRlZ2VyIGd0Ml81dW1cbiAgICAgICtJbnRlZ2VyIGd0NV8wdW1cbiAgICAgICt0b1N0cmluZygpXG4gICAgfVxuICAgIGNsYXNzIEdhc1Jlc3VsdHtcbiAgICAgICtTdHJpbmcgaW5zdGFudFxuICAgICAgK0RvdWJsZSBhZGNcbiAgICAgICtEb3VibGUgbmgzXG4gICAgICArRG91YmxlIG94aWRpc2luZ1xuICAgICAgK0RvdWJsZSByZWR1Y2luZ1xuICAgICAgK3RvU3RyaW5nKClcbiAgICB9XG4gICAgY2xhc3MgUmVzdWx0e1xuICAgICAgK0hhc2hNYXA8U3RyaW5nLE9iamVjdD5cbiAgICAgICt0b1N0cmluZygpXG4gICAgfVxuICAgIGNsYXNzIFN0YXRpb257XG4gICAgK0ludGVnZXIgaWRcbiAgICArU3RyaW5nIHNlcmlhbFxuICAgICtTdHJpbmcgbmFtZVxuICAgICtEb3VibGUgbG9uZ2l0dWRlXG4gICAgK0RvdWJsZSBsYXRpdHVkZVxuICAgICtCb29sZWFuIGFjdGl2ZVxuICAgIH0iLCJtZXJtYWlkIjp7InRoZW1lIjoiZGVmYXVsdCIsInRoZW1lVmFyaWFibGVzIjp7ImJhY2tncm91bmQiOiJ3aGl0ZSIsInByaW1hcnlDb2xvciI6IiNFQ0VDRkYiLCJzZWNvbmRhcnlDb2xvciI6IiNmZmZmZGUiLCJ0ZXJ0aWFyeUNvbG9yIjoiaHNsKDgwLCAxMDAlLCA5Ni4yNzQ1MDk4MDM5JSkiLCJwcmltYXJ5Qm9yZGVyQ29sb3IiOiJoc2woMjQwLCA2MCUsIDg2LjI3NDUwOTgwMzklKSIsInNlY29uZGFyeUJvcmRlckNvbG9yIjoiaHNsKDYwLCA2MCUsIDgzLjUyOTQxMTc2NDclKSIsInRlcnRpYXJ5Qm9yZGVyQ29sb3IiOiJoc2woODAsIDYwJSwgODYuMjc0NTA5ODAzOSUpIiwicHJpbWFyeVRleHRDb2xvciI6IiMxMzEzMDAiLCJzZWNvbmRhcnlUZXh0Q29sb3IiOiIjMDAwMDIxIiwidGVydGlhcnlUZXh0Q29sb3IiOiJyZ2IoOS41MDAwMDAwMDAxLCA5LjUwMDAwMDAwMDEsIDkuNTAwMDAwMDAwMSkiLCJsaW5lQ29sb3IiOiIjMzMzMzMzIiwidGV4dENvbG9yIjoiIzMzMyIsIm1haW5Ca2ciOiIjRUNFQ0ZGIiwic2Vjb25kQmtnIjoiI2ZmZmZkZSIsImJvcmRlcjEiOiIjOTM3MERCIiwiYm9yZGVyMiI6IiNhYWFhMzMiLCJhcnJvd2hlYWRDb2xvciI6IiMzMzMzMzMiLCJmb250RmFtaWx5IjoiXCJ0cmVidWNoZXQgbXNcIiwgdmVyZGFuYSwgYXJpYWwiLCJmb250U2l6ZSI6IjE2cHgiLCJsYWJlbEJhY2tncm91bmQiOiIjZThlOGU4Iiwibm9kZUJrZyI6IiNFQ0VDRkYiLCJub2RlQm9yZGVyIjoiIzkzNzBEQiIsImNsdXN0ZXJCa2ciOiIjZmZmZmRlIiwiY2x1c3RlckJvcmRlciI6IiNhYWFhMzMiLCJkZWZhdWx0TGlua0NvbG9yIjoiIzMzMzMzMyIsInRpdGxlQ29sb3IiOiIjMzMzIiwiZWRnZUxhYmVsQmFja2dyb3VuZCI6IiNlOGU4ZTgiLCJhY3RvckJvcmRlciI6ImhzbCgyNTkuNjI2MTY4MjI0MywgNTkuNzc2NTM2MzEyOCUsIDg3LjkwMTk2MDc4NDMlKSIsImFjdG9yQmtnIjoiI0VDRUNGRiIsImFjdG9yVGV4dENvbG9yIjoiYmxhY2siLCJhY3RvckxpbmVDb2xvciI6ImdyZXkiLCJzaWduYWxDb2xvciI6IiMzMzMiLCJzaWduYWxUZXh0Q29sb3IiOiIjMzMzIiwibGFiZWxCb3hCa2dDb2xvciI6IiNFQ0VDRkYiLCJsYWJlbEJveEJvcmRlckNvbG9yIjoiaHNsKDI1OS42MjYxNjgyMjQzLCA1OS43NzY1MzYzMTI4JSwgODcuOTAxOTYwNzg0MyUpIiwibGFiZWxUZXh0Q29sb3IiOiJibGFjayIsImxvb3BUZXh0Q29sb3IiOiJibGFjayIsIm5vdGVCb3JkZXJDb2xvciI6IiNhYWFhMzMiLCJub3RlQmtnQ29sb3IiOiIjZmZmNWFkIiwibm90ZVRleHRDb2xvciI6ImJsYWNrIiwiYWN0aXZhdGlvbkJvcmRlckNvbG9yIjoiIzY2NiIsImFjdGl2YXRpb25Ca2dDb2xvciI6IiNmNGY0ZjQiLCJzZXF1ZW5jZU51bWJlckNvbG9yIjoid2hpdGUiLCJzZWN0aW9uQmtnQ29sb3IiOiJyZ2JhKDEwMiwgMTAyLCAyNTUsIDAuNDkpIiwiYWx0U2VjdGlvbkJrZ0NvbG9yIjoid2hpdGUiLCJzZWN0aW9uQmtnQ29sb3IyIjoiI2ZmZjQwMCIsInRhc2tCb3JkZXJDb2xvciI6IiM1MzRmYmMiLCJ0YXNrQmtnQ29sb3IiOiIjOGE5MGRkIiwidGFza1RleHRMaWdodENvbG9yIjoid2hpdGUiLCJ0YXNrVGV4dENvbG9yIjoid2hpdGUiLCJ0YXNrVGV4dERhcmtDb2xvciI6ImJsYWNrIiwidGFza1RleHRPdXRzaWRlQ29sb3IiOiJibGFjayIsInRhc2tUZXh0Q2xpY2thYmxlQ29sb3IiOiIjMDAzMTYzIiwiYWN0aXZlVGFza0JvcmRlckNvbG9yIjoiIzUzNGZiYyIsImFjdGl2ZVRhc2tCa2dDb2xvciI6IiNiZmM3ZmYiLCJncmlkQ29sb3IiOiJsaWdodGdyZXkiLCJkb25lVGFza0JrZ0NvbG9yIjoibGlnaHRncmV5IiwiZG9uZVRhc2tCb3JkZXJDb2xvciI6ImdyZXkiLCJjcml0Qm9yZGVyQ29sb3IiOiIjZmY4ODg4IiwiY3JpdEJrZ0NvbG9yIjoicmVkIiwidG9kYXlMaW5lQ29sb3IiOiJyZWQiLCJsYWJlbENvbG9yIjoiYmxhY2siLCJlcnJvckJrZ0NvbG9yIjoiIzU1MjIyMiIsImVycm9yVGV4dENvbG9yIjoiIzU1MjIyMiIsImNsYXNzVGV4dCI6IiMxMzEzMDAiLCJmaWxsVHlwZTAiOiIjRUNFQ0ZGIiwiZmlsbFR5cGUxIjoiI2ZmZmZkZSIsImZpbGxUeXBlMiI6ImhzbCgzMDQsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlMyI6ImhzbCgxMjQsIDEwMCUsIDkzLjUyOTQxMTc2NDclKSIsImZpbGxUeXBlNCI6ImhzbCgxNzYsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlNSI6ImhzbCgtNCwgMTAwJSwgOTMuNTI5NDExNzY0NyUpIiwiZmlsbFR5cGU2IjoiaHNsKDgsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlNyI6ImhzbCgxODgsIDEwMCUsIDkzLjUyOTQxMTc2NDclKSJ9fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiY2xhc3NEaWFncmFtXG4gICAgU2Vuc29yIDx8LS0gUG9sbHV0aW9uUmVzdWx0XG4gICAgU2Vuc29yIDx8LS0gR2FzUmVzdWx0XG4gICAgU2Vuc29yIDogK2ludCBzdGF0aW9uSWRcbiAgICBjbGFzcyBQb2xsdXRpb25SZXN1bHR7XG4gICAgICArU3RyaW5nIGluc3RhbnRcbiAgICAgICtJbnRlZ2VyIFBNMTBcbiAgICAgICtJbnRlZ2VyIFBNMTBfYXRtXG4gICAgICArSW50ZWdlciBQTTFfMFxuICAgICAgK0ludGVnZXIgUE0xXzBfYXRtXG4gICAgICArSW50ZWdlciBQTTJfNVxuICAgICAgK0ludGVnZXIgUE0yXzVfYXRtXG4gICAgICArSW50ZWdlciBndDBfM3VtXG4gICAgICArSW50ZWdlciBndDBfNXVtXG4gICAgICArSW50ZWdlciBndDEwdW1cbiAgICAgICtJbnRlZ2VyIGd0MV8wdW1cbiAgICAgICtJbnRlZ2VyIGd0Ml81dW1cbiAgICAgICtJbnRlZ2VyIGd0NV8wdW1cbiAgICAgICt0b1N0cmluZygpXG4gICAgfVxuICAgIGNsYXNzIEdhc1Jlc3VsdHtcbiAgICAgICtTdHJpbmcgaW5zdGFudFxuICAgICAgK0RvdWJsZSBhZGNcbiAgICAgICtEb3VibGUgbmgzXG4gICAgICArRG91YmxlIG94aWRpc2luZ1xuICAgICAgK0RvdWJsZSByZWR1Y2luZ1xuICAgICAgK3RvU3RyaW5nKClcbiAgICB9XG4gICAgY2xhc3MgUmVzdWx0e1xuICAgICAgK0hhc2hNYXA8U3RyaW5nLE9iamVjdD5cbiAgICAgICt0b1N0cmluZygpXG4gICAgfVxuICAgIGNsYXNzIFN0YXRpb257XG4gICAgK0ludGVnZXIgaWRcbiAgICArU3RyaW5nIHNlcmlhbFxuICAgICtTdHJpbmcgbmFtZVxuICAgICtEb3VibGUgbG9uZ2l0dWRlXG4gICAgK0RvdWJsZSBsYXRpdHVkZVxuICAgICtCb29sZWFuIGFjdGl2ZVxuICAgIH0iLCJtZXJtYWlkIjp7InRoZW1lIjoiZGVmYXVsdCIsInRoZW1lVmFyaWFibGVzIjp7ImJhY2tncm91bmQiOiJ3aGl0ZSIsInByaW1hcnlDb2xvciI6IiNFQ0VDRkYiLCJzZWNvbmRhcnlDb2xvciI6IiNmZmZmZGUiLCJ0ZXJ0aWFyeUNvbG9yIjoiaHNsKDgwLCAxMDAlLCA5Ni4yNzQ1MDk4MDM5JSkiLCJwcmltYXJ5Qm9yZGVyQ29sb3IiOiJoc2woMjQwLCA2MCUsIDg2LjI3NDUwOTgwMzklKSIsInNlY29uZGFyeUJvcmRlckNvbG9yIjoiaHNsKDYwLCA2MCUsIDgzLjUyOTQxMTc2NDclKSIsInRlcnRpYXJ5Qm9yZGVyQ29sb3IiOiJoc2woODAsIDYwJSwgODYuMjc0NTA5ODAzOSUpIiwicHJpbWFyeVRleHRDb2xvciI6IiMxMzEzMDAiLCJzZWNvbmRhcnlUZXh0Q29sb3IiOiIjMDAwMDIxIiwidGVydGlhcnlUZXh0Q29sb3IiOiJyZ2IoOS41MDAwMDAwMDAxLCA5LjUwMDAwMDAwMDEsIDkuNTAwMDAwMDAwMSkiLCJsaW5lQ29sb3IiOiIjMzMzMzMzIiwidGV4dENvbG9yIjoiIzMzMyIsIm1haW5Ca2ciOiIjRUNFQ0ZGIiwic2Vjb25kQmtnIjoiI2ZmZmZkZSIsImJvcmRlcjEiOiIjOTM3MERCIiwiYm9yZGVyMiI6IiNhYWFhMzMiLCJhcnJvd2hlYWRDb2xvciI6IiMzMzMzMzMiLCJmb250RmFtaWx5IjoiXCJ0cmVidWNoZXQgbXNcIiwgdmVyZGFuYSwgYXJpYWwiLCJmb250U2l6ZSI6IjE2cHgiLCJsYWJlbEJhY2tncm91bmQiOiIjZThlOGU4Iiwibm9kZUJrZyI6IiNFQ0VDRkYiLCJub2RlQm9yZGVyIjoiIzkzNzBEQiIsImNsdXN0ZXJCa2ciOiIjZmZmZmRlIiwiY2x1c3RlckJvcmRlciI6IiNhYWFhMzMiLCJkZWZhdWx0TGlua0NvbG9yIjoiIzMzMzMzMyIsInRpdGxlQ29sb3IiOiIjMzMzIiwiZWRnZUxhYmVsQmFja2dyb3VuZCI6IiNlOGU4ZTgiLCJhY3RvckJvcmRlciI6ImhzbCgyNTkuNjI2MTY4MjI0MywgNTkuNzc2NTM2MzEyOCUsIDg3LjkwMTk2MDc4NDMlKSIsImFjdG9yQmtnIjoiI0VDRUNGRiIsImFjdG9yVGV4dENvbG9yIjoiYmxhY2siLCJhY3RvckxpbmVDb2xvciI6ImdyZXkiLCJzaWduYWxDb2xvciI6IiMzMzMiLCJzaWduYWxUZXh0Q29sb3IiOiIjMzMzIiwibGFiZWxCb3hCa2dDb2xvciI6IiNFQ0VDRkYiLCJsYWJlbEJveEJvcmRlckNvbG9yIjoiaHNsKDI1OS42MjYxNjgyMjQzLCA1OS43NzY1MzYzMTI4JSwgODcuOTAxOTYwNzg0MyUpIiwibGFiZWxUZXh0Q29sb3IiOiJibGFjayIsImxvb3BUZXh0Q29sb3IiOiJibGFjayIsIm5vdGVCb3JkZXJDb2xvciI6IiNhYWFhMzMiLCJub3RlQmtnQ29sb3IiOiIjZmZmNWFkIiwibm90ZVRleHRDb2xvciI6ImJsYWNrIiwiYWN0aXZhdGlvbkJvcmRlckNvbG9yIjoiIzY2NiIsImFjdGl2YXRpb25Ca2dDb2xvciI6IiNmNGY0ZjQiLCJzZXF1ZW5jZU51bWJlckNvbG9yIjoid2hpdGUiLCJzZWN0aW9uQmtnQ29sb3IiOiJyZ2JhKDEwMiwgMTAyLCAyNTUsIDAuNDkpIiwiYWx0U2VjdGlvbkJrZ0NvbG9yIjoid2hpdGUiLCJzZWN0aW9uQmtnQ29sb3IyIjoiI2ZmZjQwMCIsInRhc2tCb3JkZXJDb2xvciI6IiM1MzRmYmMiLCJ0YXNrQmtnQ29sb3IiOiIjOGE5MGRkIiwidGFza1RleHRMaWdodENvbG9yIjoid2hpdGUiLCJ0YXNrVGV4dENvbG9yIjoid2hpdGUiLCJ0YXNrVGV4dERhcmtDb2xvciI6ImJsYWNrIiwidGFza1RleHRPdXRzaWRlQ29sb3IiOiJibGFjayIsInRhc2tUZXh0Q2xpY2thYmxlQ29sb3IiOiIjMDAzMTYzIiwiYWN0aXZlVGFza0JvcmRlckNvbG9yIjoiIzUzNGZiYyIsImFjdGl2ZVRhc2tCa2dDb2xvciI6IiNiZmM3ZmYiLCJncmlkQ29sb3IiOiJsaWdodGdyZXkiLCJkb25lVGFza0JrZ0NvbG9yIjoibGlnaHRncmV5IiwiZG9uZVRhc2tCb3JkZXJDb2xvciI6ImdyZXkiLCJjcml0Qm9yZGVyQ29sb3IiOiIjZmY4ODg4IiwiY3JpdEJrZ0NvbG9yIjoicmVkIiwidG9kYXlMaW5lQ29sb3IiOiJyZWQiLCJsYWJlbENvbG9yIjoiYmxhY2siLCJlcnJvckJrZ0NvbG9yIjoiIzU1MjIyMiIsImVycm9yVGV4dENvbG9yIjoiIzU1MjIyMiIsImNsYXNzVGV4dCI6IiMxMzEzMDAiLCJmaWxsVHlwZTAiOiIjRUNFQ0ZGIiwiZmlsbFR5cGUxIjoiI2ZmZmZkZSIsImZpbGxUeXBlMiI6ImhzbCgzMDQsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlMyI6ImhzbCgxMjQsIDEwMCUsIDkzLjUyOTQxMTc2NDclKSIsImZpbGxUeXBlNCI6ImhzbCgxNzYsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlNSI6ImhzbCgtNCwgMTAwJSwgOTMuNTI5NDExNzY0NyUpIiwiZmlsbFR5cGU2IjoiaHNsKDgsIDEwMCUsIDk2LjI3NDUwOTgwMzklKSIsImZpbGxUeXBlNyI6ImhzbCgxODgsIDEwMCUsIDkzLjUyOTQxMTc2NDclKSJ9fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)

### Pulling from qiot Sensor Service

We have implemented this interface to gather data from our python 
Rest API services. This interface will be call every 5s to send data to DataHub.

``` java
package fr.axians.qiot.edge_service.service.sensor;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import org.eclipse.microprofile.rest.client.inject.RegisterRestClient;

@Path("/sensors")
@RegisterRestClient
public interface SensorService {
    
    @GET
    @Path("/gas")
    @Produces("application/json")
    Result getGasResult();

    @GET
    @Path("/pollution")
    @Produces("application/json")
    Result getPollutionResult();
}
```
### Scheduling

The scheduling is done by **TelemetryService**. We get data from Sensor Service and put it on DataHub. We choose to use the Flowable object to create our stream between our qiot edge services and the DataHub. This object associated with our MQTT parameter set in our resource files allow us to send a String that contains our air quality information.

``` java
public class TelemetryService {
    
    private static final Logger LOGGER = Logger.getLogger("ListenerBean");
    @Inject
    SensorResource sr;

    
    /* Gas stream */
    @Outgoing("gas-stream")
    public Flowable <String> streamGasData() throws JsonProcessingException {
        
        /* Creating the ObjectMapper object */
        ObjectMapper mapper = new ObjectMapper();
        LOGGER.info(mapper.writeValueAsString(sr.getGas()));
        return Flowable.interval(5, TimeUnit.SECONDS).map(interval -> mapper.writeValueAsString(sr.getGas()));
    }


    /* Pollution stream */
    @Outgoing("pollution-stream")
    public Flowable <String> streamPollutionData() throws JsonProcessingException {
        /* Creating the ObjectMapper object */
        ObjectMapper mapper = new ObjectMapper();
        LOGGER.info(mapper.writeValueAsString(sr.getPollution()));
        /* Converting the Gas object to JSONString */
        return Flowable.interval(5, TimeUnit.SECONDS).map(interval ->  mapper.writeValueAsString(sr.getPollution()));
    }
}
```


### Shutdown

When we gracefully shutdown the QIoT Edge Service, we are calling a function (more information bellow) that sends a request to unsubscribe.

``` java
void onStop(@Observes ShutdownEvent ev) {
        LOGGER.info("Stop application begin uregistering process ...");               
        regService.unregStation(this.st.getId());
    }
```

### init overload

Here we have our initialization class that instantiated dynamically configuration parameters we need.

``` java
void init(){
        this.st = new Station();
        LOGGER.info(this.st.toString());
        
        //Defined the machine-id path to be able to regester
        java.nio.file.Path  path = Paths.get("/etc/machine-id");
        String content = null;

        //Get the id defined in the file
        try {
            content = Files.readString(path, StandardCharsets.UTF_8);
        } catch (IOException e) {
            LOGGER.error(e);
        };

        //Initialize the Station information
        this.st.setSerial(content);
        LOGGER.info("Device name : "+this.st.getName());

        /* Retrieve stationId and activate the station */
        Integer stationId =0;
        stationId = regService.regStation(this.st.getSerial(), this.st.getName(), this.st.getLongitude(), this.st.getLatitude());
        this.st.setId(stationId);
        this.st.setActive(true);
        LOGGER.info("Register ID : "+this.st.getId());
    }
```

1. Get the unique machine ID
1. Register the Device on DataHub

It's necessary to use the /etc/machine-id of Host machine and not ephemeral container. To do this, we share the host file with containers at the creation:

> podman **-v /etc/machine-id:/etc/machine-id:ro**  *[...]*

### (Un)Register

We have created an *Interface* to Register and UnRegister Device on DataHub:

``` java
public interface RegistrationService {

    /* Registration of the station */
    @PUT
    @Path("/register/serial/{serial}/name/{name}/longitude/{longitude}/latitude/{latitude}")
    @Produces(MediaType.TEXT_PLAIN)
    @Consumes(MediaType.TEXT_PLAIN)
    public Integer regStation(@PathParam("serial") String serial,
    @PathParam("name") String name,
    @PathParam("longitude") Double longitude,
    @PathParam("latitude") Double latitude);

    /* Unregistration of the station */
    @DELETE
    @Path("/register/id/{id}")
    public void unregStation(@PathParam("id") Integer id);

}
```

Name, longitude and latitude are set in application.properties and can be set by ENV variables from CRI. 

## Running the application in production mode

From Fedora IOT on Raspberry PI, execute the following commands

### Env Variables

```
SENSORHOST: FQDN or IP of Python Sensor Service ex: (sensor)
TEAMNAME: Name of Edge Device or Team (default: fr_FR.UTF8)
TEAMLONGITUDE: Longitude of Device (default: -3.65)
TEAMLATITUDE: Latitude of Device (default: 47.09)
``` 

### Production

```
podman run \
-v /etc/machine-id:/etc/machine-id:ro \
-e SENSORHOST=changeme \
-e TEAMNAME=QIoT.fr_FR.UTF8 \
quay.io/acb-fr/qiot-edge-service-jvm:1.1
```

### Debug Mod

```
podman run \
-it --rm
-v /etc/machine-id:/etc/machine-id:ro \
quay.io/acb-fr/qiot-edge-service-jvm:1.1
```

## Difficulties

### int into Double

We have two IOT runtime environments. Two Raspberries, two probes, two geographic sites. One is used for production, the other for development. We built a fully functional Edge Service image on the Pre-Production environment but with this same image we encountered problems in the Production environment. We had the following error.

``` log
2020-09-28 08:40:14,597 ERROR [io.sma.rea.mes.provider] (main) SRMSG00200: The method fr.axians.qiot.edge_service.service.telemetry.TelemetryService#streamGasData has thrown an exception: java.lang.ClassCastException: class java.lang.Integer cannot be cast to class java.lang.Double (java.lang.Integer and java.lang.Double are in module java.base of loader 'bootstrap')
```

We had wasted time trying to figure out why we had an error in the code when the code version was exactly the same.

After investigation, the problem came from the QIoT Sensor Service which returned an INT for the ADC value when it could not find a value to harvest. While the QIoT Edge Service was waiting for a Double.

``` json
// adc in Double
{
  "result":{
    "adc":0.0,
    "instant":"2020-09-28 09:04:29GMT",
    "nh3":363047.61904761917,
    "oxidising":22772.37851662404,
    "reducing":26907.133243606997
  }
}
```

``` json
// adc in INT
{
  "result":{
    "adc":0,
    "instant":"2020-09-28 09:05:29GMT",
    "nh3":363047.61904761917,
    "oxidising":22772.37851662404,
    "reducing":26907.133243606997
  }
}
```

In particular, we lost time on this problem because we worked in a decentralized manner and the Edge Service sub-team had not seen the operation of the Sensor Service part.

### -PNative

When we packaged our application and launched our executable application we encountered the error below. This problem seems to be associated with the RestEasy library that allow our code to read and interprete JSON into Java object. When we worked in our development environment we did not have any problem but due to unknown reason we had it in a Pnative mode. We have try to modify different type of our variable and modify our code to properly transform the variable we get from our RestClient Interface. But until we still did not have a solution. 
Of course our team has an idea of the problem and at matter of fact that is our python team that have build the image for us we think that those beared men have tried to sabotage us .. ;p 

``` log
__  ____  __  _____   ___  __ ____  ______
 --/ __ \/ / / / _ | / _ \/ //_/ / / / __/
 -/ /_/ / /_/ / __ |/ , _/ ,< / /_/ /\ \
--\___\_\____/_/ |_/_/|_/_/|_|\____/___/
[...]
2020-09-28 08:41:49,847 WARN  [org.jbo.res.res.i18n] (main) RESTEASY002165: No valueOf() method available for int, trying constructor...
2020-09-28 08:41:49,850 ERROR [io.sma.rea.mes.provider] (main) SRMSG00200: The method fr.axians.qiot.edge_service.service.telemetry.TelemetryService#streamGasData has thrown an exception: javax.ws.rs.ProcessingException: java.lang.IllegalArgumentException: RESTEASY003360: int has no String constructor
```

## Contributors

<a href="https://github.com/QIoT-fr-FR-utf8/qiot-fr-fr-utf8.github.io/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=QIoT-fr-FR-utf8/qiot-fr-fr-utf8.github.io" />
</a>
