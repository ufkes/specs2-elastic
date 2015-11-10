# spec2s-elastic
============

This project contains tools for testing using [specs2](http://etorreborre.github.io/specs2/) and
[elastic4s](https://github.com/sksamuel/elastic4s).

It currently contains a single trait (`TestElastic`)that, when mixed into your Specification, starts and stops a mongod
instance for use in your tests. The  connection configuration is available in a val called `testElastic`.

When the test is done, the database is destroyed along with the elastic instance.

How to use
----------
To use the trait:

### 1. Include as dependency
Add the following dependency to `libraryDependencies` in your `build.sbt` or `project/Build.scala` file:

```
"com.lunatech" %% "specs2-elastic" % "0.1.0"
```

### 2. Use the trait in your spec:

The following example is a specification for a Play 2 application

```scala
class MySpec extends Specification with TestElastic {

  "My spec" should {
    "have an elasticsearch database accessible" in {
      running(FakeApplication(additionalConfiguration = testElastic)) {
        // Test stuff goes here
      }
    }
  }

}
```

License
=======
Copyright 2015 Lunatech (http://www.lunatech.com).

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this project except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

