# Ignore Grunt for running tests via SBT and Play

If you are using the [Play Framework](https://www.playframework.com/) then you'll be using SBT as your package manager, as many apps have front end componenets with their own asset pipeline (Grunt etc). I was running into a problem that Play as of version 2.3.X automatically tries to resolve dependencies if there is a `package.json` file (used by Grunt) within the project. You can avoid calling these by using the following in your SBT build.sbt file:

```scala

import sbt._
import Keys._
import com.typesafe.sbt.jse.JsEngineImport.JsEngineKeys
import com.typesafe.sbt.web.Import.{Assets, TestAssets}


lazy val root = (project in file(".")).enablePlugins(PlayJava).settings(
JsEngineKeys.npmNodeModules in Assets := Nil,
JsEngineKeys.npmNodeModules in TestAssets := Nil
)
```