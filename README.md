# Summer Fun
[Summer Fun](https://julianjupiter.github.io/summer-fun) is a microframework for Java.

```java
import summer.fun.SummerFun;
import java.util.Arrays;
import java.util.List;

public class SampleApp {
    public static void main(String[] args) {
        Configuration config = ConfigurationBuilder.newBuilder()
            .withContextPath("/api")
            .build();
        SummerFun app = new SummerFun()
            .withConfiguration(config);

        app.get("/heroes", (request, response) -> {
            List<Hero> heroes = getHeroes();
            response.json().send(heroes);
        });

        app.run(() -> {
            System.out.println("Application is running on port " + config.getPort());
            System.out.println("Press any key to stop the server...");
        });
    }
    
    public static List<Hero> getHeroes() {
        Hero hero1 = new Hero();
        hero1.setId(1);
        hero1.setLastName("Rizal");
        hero1.setFirstName("Jose");
        
        Hero hero2 = new Hero();
        hero2.setId(2);
        hero2.setLastName("Bonifacio");
        hero2.setFirstName("Andres");
        
        return Arrays.asList(hero1, hero2);
    }
    
}

class Hero {
    private long id;
    private String lastName;
    private String firstName;
    
    public long getId() {
        return id;
    }
    
    public void setId(long id) {
        this.id = id;
    }
    
    public String getLastName() {
        return lastName;
    }
    
    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
    
    public String getFirstName() {
        return firstName;
    }
    
    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }
}
```

# Features
* Inspired by microframeworks from different programming languages - [Slim Framework](https://www.slimframework.com), [ExpressJS](https://expressjs.com), [Spark](http://sparkjava.com).
* Uses Grizzly HTTP Server framework, a component of [Grizzly](https://javaee.github.io/grizzly) NIO framework which has been designed to help developers to take advantage of the Java™ NIO API.
* Lightweight

# Getting started
Clone the repository and install using Maven:
```
git clone https://github.com/julianjupiter/summer-fun
cd summer-fun
mvn install
```

Clone, build, and run sample application:
```
git clone https://github.com/julianjupiter/summer-fun-sample
cd summer-fun-sample
mvn package
java -jar ./target/summer-fun-sample-1.0.0.jar
```

Open browser:
```
http://localhost:7000/
http://localhost:7000/app/users
http://localhost:7000/app/users/1
http://localhost:7000/app/users/2
http://localhost:7000/app/users/3
http://localhost:7000/app/users/10
http://localhost:7000/app/user-list
```

# Disclaimer
This is not ready for production yet. Any suggestions and help would be highly appreciated.

# License
Summer Fun, a Java microframework.  
Copyright (C) 2018  Julian V. Jupiter

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.
