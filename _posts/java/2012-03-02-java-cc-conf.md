---
layout: page

title: Configuration file
tags:
- Java
---

#Configuration files for Java applications

For more information about the general usage of configuration files, please refer to <a href="/cc-conf/">this page</a>.

## For Maven deploy type

For every Java project using Maven, you need to write a small specific JSON
file, placed at the root of your project. Make sure this file is called **cc_conf.json**

This JSON is the configuration file that you will need for some deployments and builds. Here is the syntax:
{% highlight javascript%}
    {
        "build": {
            "type": "<string>",
            "goal": "<string>"
        },
        "deploy": {
            "javaVersion": <integer>,
            "goal": "<string>"
        }
    }
{% endhighlight %}


* ``"build"`` is an object with the goal to execute.
  * ``"type"`` can be ``"maven"`` or ``"ant"``.
  * ``"goal"`` is the target you want to use to build your project.
* ``"deploy"`` is an object containing the type of deploy (Maven, Ant or SBT) and the goal to execute.
  * ``"goal"``: the goal/target and options you want to execute to deploy/run you project.
  * ``"javaVersion"``: the version of java you want to use to run your app. Values: 6, 7. Default : 7.

Example of cc_conf.json for a Maven deploy:

{% highlight javascript%}
    {
      "deploy": {
        "goal": "-Dtest.active=false -Dexec.mainClass=\"com.example.Main\" assembly:jar-with-dependencies exec:java"
      }
    }

{% endhighlight %}

Example of cc_conf.json for Ant (available soon) build:

{% highlight javascript%}
    {
      "build": {
        "type": "ant",
        "goal": "exterminate -Ddoctor.version=11"
      }
    }
{% endhighlight %}

## For War deploy type

For java applications, you need the following fields in the cc_conf.json:

{% highlight javascript %}
    {
       "deploy": {
          "server": "<string>",
          "war": "<string>"
       }
    }
{% endhighlight %}

* ``"server"`` should contain the application server / servlet container to use;
  the table below lists and describes you the possible values for the `server`
  field;
* ``"war"`` should be the relative path to the war file to run.

<table class="table table-bordered table-stripped">
   <thead>
      <tr>
         <th>Value</th>
         <th>Description</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>GLASSFISH3</td>
         <td>Use Glassfish 3.x
         (see <a href="http://glassfish.java.net/">http://glassfish.java.net/</a>)</td>
      </tr>
      <tr>
         <td>JBOSS6</td>
         <td>Use JBoss AS 6.x
         (see <a href="http://www.jboss.org/jbossas">http://www.jboss.org/jbossas</a></td>
      </tr>
      <tr>
         <td>JBOSS7</td>
         <td>Use JBoss AS 7.x
         (see <a href="http://www.jboss.org/jbossas">http://www.jboss.org/jbossas</a>) </td>
      </tr>
      <tr>
         <td>RESIN3</td>
         <td>Use Resin AS 3.x (see <a
         href="http://www.caucho.com/resin-3.1/doc/">http://www.caucho.com/resin-3.1/doc/</a>)</td>
      </tr>
      <tr>
         <td>JETTY6</td>
         <td>Use Jetty servlet container 6.x (see <a
         href="http://jetty.codehaus.org/jetty/">http://jetty.codehaus.org/jetty/</a>)</td>
      </tr>
      <tr>
         <td>JETTY7</td>
         <td>Use Jetty servlet container 7.x (see <a
         href="https://www.eclipse.org/jetty/">https://www.eclipse.org/jetty/</a>)</td>
      </tr>
      <tr>
         <td>JETTY8</td>
         <td>Use Jetty servlet container 8.x (see <a
         href="https://www.eclipse.org/jetty/">https://www.eclipse.org/jetty/</a>)</td>
      </tr>
      <tr>
         <td>JETTY9</td>
         <td>Use Jetty servlet container 9.x (see <a
         href="http://www.eclipse.org/jetty/documentation/current/">http://www.eclipse.org/jetty/documentation/current/</a>)</td>
      </tr>
      <tr>
         <td>TOMCAT4</td>
         <td>Use Tomcat servlet container 4.x (see <a
         href="https://tomcat.apache.org/">https://tomcat.apache.org/</a>)</td>
      </tr>
      <tr>
         <td>TOMCAT5</td>
         <td>Use Tomcat servlet container 5.x (see <a
         href="https://tomcat.apache.org/">https://tomcat.apache.org/</a>)</td>
      </tr>
      <tr>
         <td>TOMCAT6</td>
         <td>Use Tomcat servlet container 6.x (see <a
         href="https://tomcat.apache.org/">https://tomcat.apache.org/</a>)</td>
      </tr>
      <tr>
         <td>TOMCAT7</td>
         <td>Use Tomcat servlet container 7.x (see <a
         href="https://tomcat.apache.org/">https://tomcat.apache.org/</a>)</td>
      </tr>
   </tbody>
</table>

