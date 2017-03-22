# torrent 🌊

**torrent** is a code notebook for the machine learning platform [h2o-3](https://github.com/h2oai/h2o-3). **torrent** combines code execution, text, mathematics, plots and rich media to build machine learning workflows.  

**torrent** is written in [es2015](https://babeljs.io/learn-es2015/) [Javascript](https://en.wikipedia.org/wiki/JavaScript). **torrent** uses the [Pug](https://github.com/pugjs/pug) templating engine _(formerly known as [Jade](https://github.com/pugjs/pug#rename-from-jade))_ to define HTML views and lay out pages.  **torrent** uses the [KnockoutJS](https://github.com/knockout/knockout) Model-View-View-Model library for declarative data binding.  

**torrent** contains a veritable heap of little embedded [DSL](https://en.wikipedia.org/wiki/Domain-specific_language)s for reactive [dataflow programming](https://en.wikipedia.org/wiki/Dataflow_programming), markup generation, lazy evaluation and multicast signals/slots. **torrent** sandboxes and evaluates user-Javascript in the browser via static analysis and tree-rewriting. **torrent**'s storytelling environment for exploratory data analysis & machine learning, features async, re-scriptable record/replay capabilities.

**torrent** is a fork of the [h2o-flow](https://github.com/h2oai/h2o-flow) project

## user guide

there is a nice [user guide](https://github.com/h2oai/h2o-3/blob/8858aac90dce771f9025b16948b675f92b542715/h2o-docs/src/product/flow/README.md) for **h2o-flow** housed over in the [h2o-3](https://github.com/h2oai/h2o-3) repo that describes many features also found in **torrent**

## dev setup

clone [h2o-3](https://github.com/h2oai/h2o-3) and **torrent** in the same parent directory. 

it is best to run [h2o-3](https://github.com/h2oai/h2o-3) in the Java [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) [IntelliJ IDEA](https://www.jetbrains.com/idea/).  This enables you the developer to see your changes to *torrent*  in the browser immediately after you run the `npm run build` command, without waiting the 90+ secods to build a new `h2o.jar` binary and run `java -jar h2o.jar` to restart [h2o-3](https://github.com/h2oai/h2o-3).  

inside of [IntelliJ IDEA](https://www.jetbrains.com/idea/):

1. clean up all previous built files:  `cd h2o-3 && ./gradlew clean`
2. open the [h2o-3](https://github.com/h2oai/h2o-3) directory in IDEA, then build and launch `H2OApp.java`
3. Run 

```
cd torrent
npm install
npm run build
```

to install **torrent**'s dependencies and create the **torrent** bundle. you can now access and debug **torrent** at [http://localhost:54321/](http://localhost:54321/)

4. after each change you make to the **torrent** source code, run the command 

`npm run build`

to copy your changes to the instance of [h2o-3](https://github.com/h2oai/h2o-3) running locally inside of IDEA

further [instructions](https://github.com/h2oai/h2o-3#47-setting-up-your-preferred-ide-environment) for setting up the [h2o-3](https://github.com/h2oai/h2o-3) project in [IntelliJ IDEA]() are [here](https://github.com/h2oai/h2o-3#47-setting-up-your-preferred-ide-environment)


## testing a new **torrent** feature with Sparkling Water  

**torrent** can also be used with [Sparkling Water](https://github.com/h2oai/sparkling-water)  
follow this guide develop and test new Sparkling Water features in **torrent**.  
adapted from the comments on this PR https://github.com/h2oai/h2o-flow/pull/13  

##### copy built js files from one place to another  
in the `h2o-3` directory run:  
`cp h2o-web/src/main/resources/www/flow/js/* h2o-web/lib/h2o-flow/build/js/`  

##### build h2o-3  
in the `h2o-3` directory run:  
`./gradlew publishToMavenLocal -x test`  

##### build sparkling water  
in `sparkling-water` directory run:  
`./gradlew clean build -x test -x integTest`  

##### open the Sparkling Water Shell  
in `sparkling-water` directory run:  
`bin/sparkling-shell`  

in the sparkling water shell  
at the `scala>` prompt run:  
`import org.apache.spark.h2o._`  
`H2OContext.getOrCreate(sc)`  

now open **torrent** at the IP address specified  
in the sparkling water shell  

now test your changes in **torrent**  