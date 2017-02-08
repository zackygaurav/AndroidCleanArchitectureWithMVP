# AndroidCleanArchitectureWithMVP
Clean architecture in Android with MVP presentation layer.

The problem
-------
How to design a simple, decoupled, testable [clean architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) for Android, using [MVP](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter) for the presentation layer.

The solution
-------
The solution is an extension based on the [boilerpart code for asynchronous MVP design for Android, without 3rd party libraries](https://github.com/ovicon/AndroidAsynchronousMVPBoilerpart). 

Systems based on clean arhitecture have the following characteristics: separation of concerns, multilayered, independent of frameworks, independent of user interface, independent of databases, tetsable by layer, with a dependency rule that says that code dependencies can only point inwards, from lower leves like the presentation layer, to higher levels like the data layer.  
From now on, I shall only talk about clean arhitecture, in the context of the example application:

![AndroidCleanArchitectureWithMVP](http://www.ovidiuconeac.ro/wp-content/uploads/2017/02/AndroidCleanArchitectureWithMVP_emulator-169x300.png "AndroidCleanArchitectureWithMVP")

The example application is based on the following 3-tier clean arhitecture: the presentation layer, the domain layer, and the data layer.
![Generic 3-tier clean architecture](http://www.ovidiuconeac.ro/wp-content/uploads/2017/02/clean_architecture_layers.png "Generic 3-tier clean architecture")

The presentation layer is implemented as an MVP design, the domain layer contains plain Java objects, and the data layer is just a dummy singelton implementaion. 

You can have as many layer as needed, and there is not rule that says that clean arhitecture should be implemented with only three layers.

The presentation layer represents the application, and is an Android phone & table module. The domain layer and data layer are Java libraries, and used as gradle dependencies. The presentation layer depends of the domain layer and the domain layer depends on the data layer. There is also an extra module, named models, that contains the models of the application. For the sake of simplicity, these modules are used in all the layers of the application. In a more complex application usually each layer has its own data modeling.

![Modules in Android Studio](http://www.ovidiuconeac.ro/wp-content/uploads/2017/02/modules.png "Modules in Android Studio")

Because gradle manages dependencies between layers, the models module is only defined as a dependency in the data layer, which is used as a dependency in the domain layer, which in turn is used as a dependency in the presentation layer. In this way the models dependency becaomes availabe in all the layers. It is called transitivity and it is how gradle handles dependencies.

To better understand the arhitecture, let's see another overview but from a different perspective:

![Clean architecture layers overview](http://www.ovidiuconeac.ro/wp-content/uploads/2017/02/clean_architecture_layers_onion_overview.png "Clean architecture layers overview")

![Clean architecture layers details](http://www.ovidiuconeac.ro/wp-content/uploads/2017/02/clean_architecture_layers_onion_detail.png "Clean architecture layers details")



I do encourage further reading on this topic, starting with this two excelent resources: [The Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) and [Architecting Android…The clean way?](http://fernandocejas.com/2014/09/03/architecting-android-the-clean-way/)

In progress...


