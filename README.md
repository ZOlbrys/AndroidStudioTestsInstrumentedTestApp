# AndroidStudioTestsInstrumentedTestApp
Test app showing off issues running tests via Android Studio in some configurations

See https://issuetracker.google.com/issues/281266702

Running AGP 7.4.2, which is setup in the `master` branch, you'll see that `test_sample_class` test passes successfully with no errors reported in console.

Switching to the `latest-agp` branch, which upgrades AGP to the latest AGP version the same `test_sample_class` test passes, but errors related to JaCoCo are printed out:

```
> Task :app:testDebugUnitTest
java.lang.instrument.IllegalClassFormatException: Error while instrumenting com/example/androidstudiotestsinstrumentedtestapp/SampleClass with JaCoCo 0.8.8.202204050719/5dcf34a.
	at org.jacoco.agent.rt.internal_b6258fc.CoverageTransformer.transform(CoverageTransformer.java:94)
	at java.instrument/java.lang.instrument.ClassFileTransformer.transform(Unknown Source)
	at java.instrument/sun.instrument.TransformerManager.transform(Unknown Source)
	at java.instrument/sun.instrument.InstrumentationImpl.transform(Unknown Source)
	at java.base/java.lang.ClassLoader.defineClass1(Native Method)
	at java.base/java.lang.ClassLoader.defineClass(Unknown Source)
	at java.base/java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.defineClass(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.findClassOnClassPathOrNull(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClassOrNull(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(Unknown Source)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(Unknown Source)
	at java.base/java.lang.ClassLoader.loadClass(Unknown Source)
	at com.example.androidstudiotestsinstrumentedtestapp.ExampleUnitTest.test_sample_class(ExampleUnitTest.kt:20)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.base/java.lang.reflect.Method.invoke(Unknown Source)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:59)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:56)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.BlockJUnit4ClassRunner$1.evaluate(BlockJUnit4ClassRunner.java:100)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:366)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:103)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:63)
	at org.junit.runners.ParentRunner$4.run(ParentRunner.java:331)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:79)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:329)
	at org.junit.runners.ParentRunner.access$100(ParentRunner.java:66)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:293)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:413)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.runTestClass(JUnitTestClassExecutor.java:108)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.execute(JUnitTestClassExecutor.java:58)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.execute(JUnitTestClassExecutor.java:40)
	at org.gradle.api.internal.tasks.testing.junit.AbstractJUnitTestClassProcessor.processTestClass(AbstractJUnitTestClassProcessor.java:60)
	at org.gradle.api.internal.tasks.testing.SuiteTestClassProcessor.processTestClass(SuiteTestClassProcessor.java:52)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.base/java.lang.reflect.Method.invoke(Unknown Source)
	at org.gradle.internal.dispatch.ReflectionDispatch.dispatch(ReflectionDispatch.java:36)
	at org.gradle.internal.dispatch.ReflectionDispatch.dispatch(ReflectionDispatch.java:24)
	at org.gradle.internal.dispatch.ContextClassLoaderDispatch.dispatch(ContextClassLoaderDispatch.java:33)
	at org.gradle.internal.dispatch.ProxyDispatchAdapter$DispatchingInvocationHandler.invoke(ProxyDispatchAdapter.java:94)
	at jdk.proxy2/jdk.proxy2.$Proxy5.processTestClass(Unknown Source)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker$2.run(TestWorker.java:176)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.executeAndMaintainThreadName(TestWorker.java:129)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.execute(TestWorker.java:100)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.execute(TestWorker.java:60)
	at org.gradle.process.internal.worker.child.ActionExecutionWorker.execute(ActionExecutionWorker.java:56)
	at org.gradle.process.internal.worker.child.SystemApplicationClassLoaderWorker.call(SystemApplicationClassLoaderWorker.java:113)
	at org.gradle.process.internal.worker.child.SystemApplicationClassLoaderWorker.call(SystemApplicationClassLoaderWorker.java:65)
	at worker.org.gradle.process.internal.worker.GradleWorkerMain.run(GradleWorkerMain.java:69)
	at worker.org.gradle.process.internal.worker.GradleWorkerMain.main(GradleWorkerMain.java:74)
Caused by: java.io.IOException: Error while instrumenting com/example/androidstudiotestsinstrumentedtestapp/SampleClass with JaCoCo 0.8.8.202204050719/5dcf34a.
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrumentError(Instrumenter.java:161)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:111)
	at org.jacoco.agent.rt.internal_b6258fc.CoverageTransformer.transform(CoverageTransformer.java:92)
	... 56 more
Caused by: java.lang.IllegalStateException: Cannot process instrumented class com/example/androidstudiotestsinstrumentedtestapp/SampleClass. Please supply original non-instrumented classes.
	at org.jacoco.agent.rt.internal_b6258fc.core.internal.instr.InstrSupport.assertNotInstrumented(InstrSupport.java:238)
	at org.jacoco.agent.rt.internal_b6258fc.core.internal.instr.ClassInstrumenter.visitField(ClassInstrumenter.java:56)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassVisitor.visitField(ClassVisitor.java:338)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.readField(ClassReader.java:1137)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.accept(ClassReader.java:739)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.accept(ClassReader.java:424)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:91)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:109)
	... 57 more
java.lang.instrument.IllegalClassFormatException: Error while instrumenting com/example/androidstudiotestsinstrumentedtestapp/LiveLiterals$SampleClassKt with JaCoCo 0.8.8.202204050719/5dcf34a.
	at org.jacoco.agent.rt.internal_b6258fc.CoverageTransformer.transform(CoverageTransformer.java:94)
	at java.instrument/java.lang.instrument.ClassFileTransformer.transform(Unknown Source)
	at java.instrument/sun.instrument.TransformerManager.transform(Unknown Source)
	at java.instrument/sun.instrument.InstrumentationImpl.transform(Unknown Source)
	at java.base/java.lang.ClassLoader.defineClass1(Native Method)
	at java.base/java.lang.ClassLoader.defineClass(Unknown Source)
	at java.base/java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.defineClass(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.findClassOnClassPathOrNull(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClassOrNull(Unknown Source)
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(Unknown Source)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(Unknown Source)
	at java.base/java.lang.ClassLoader.loadClass(Unknown Source)
	at com.example.androidstudiotestsinstrumentedtestapp.SampleClass.<clinit>(SampleClass.kt)
	at com.example.androidstudiotestsinstrumentedtestapp.ExampleUnitTest.test_sample_class(ExampleUnitTest.kt:20)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.base/java.lang.reflect.Method.invoke(Unknown Source)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:59)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:56)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.BlockJUnit4ClassRunner$1.evaluate(BlockJUnit4ClassRunner.java:100)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:366)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:103)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:63)
	at org.junit.runners.ParentRunner$4.run(ParentRunner.java:331)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:79)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:329)
	at org.junit.runners.ParentRunner.access$100(ParentRunner.java:66)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:293)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:413)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.runTestClass(JUnitTestClassExecutor.java:108)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.execute(JUnitTestClassExecutor.java:58)
	at org.gradle.api.internal.tasks.testing.junit.JUnitTestClassExecutor.execute(JUnitTestClassExecutor.java:40)
	at org.gradle.api.internal.tasks.testing.junit.AbstractJUnitTestClassProcessor.processTestClass(AbstractJUnitTestClassProcessor.java:60)
	at org.gradle.api.internal.tasks.testing.SuiteTestClassProcessor.processTestClass(SuiteTestClassProcessor.java:52)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.base/java.lang.reflect.Method.invoke(Unknown Source)
	at org.gradle.internal.dispatch.ReflectionDispatch.dispatch(ReflectionDispatch.java:36)
	at org.gradle.internal.dispatch.ReflectionDispatch.dispatch(ReflectionDispatch.java:24)
	at org.gradle.internal.dispatch.ContextClassLoaderDispatch.dispatch(ContextClassLoaderDispatch.java:33)
	at org.gradle.internal.dispatch.ProxyDispatchAdapter$DispatchingInvocationHandler.invoke(ProxyDispatchAdapter.java:94)
	at jdk.proxy2/jdk.proxy2.$Proxy5.processTestClass(Unknown Source)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker$2.run(TestWorker.java:176)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.executeAndMaintainThreadName(TestWorker.java:129)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.execute(TestWorker.java:100)
	at org.gradle.api.internal.tasks.testing.worker.TestWorker.execute(TestWorker.java:60)
	at org.gradle.process.internal.worker.child.ActionExecutionWorker.execute(ActionExecutionWorker.java:56)
	at org.gradle.process.internal.worker.child.SystemApplicationClassLoaderWorker.call(SystemApplicationClassLoaderWorker.java:113)
	at org.gradle.process.internal.worker.child.SystemApplicationClassLoaderWorker.call(SystemApplicationClassLoaderWorker.java:65)
	at worker.org.gradle.process.internal.worker.GradleWorkerMain.run(GradleWorkerMain.java:69)
	at worker.org.gradle.process.internal.worker.GradleWorkerMain.main(GradleWorkerMain.java:74)
Caused by: java.io.IOException: Error while instrumenting com/example/androidstudiotestsinstrumentedtestapp/LiveLiterals$SampleClassKt with JaCoCo 0.8.8.202204050719/5dcf34a.
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrumentError(Instrumenter.java:161)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:111)
	at org.jacoco.agent.rt.internal_b6258fc.CoverageTransformer.transform(CoverageTransformer.java:92)
	... 57 more
Caused by: java.lang.IllegalStateException: Cannot process instrumented class com/example/androidstudiotestsinstrumentedtestapp/LiveLiterals$SampleClassKt. Please supply original non-instrumented classes.
	at org.jacoco.agent.rt.internal_b6258fc.core.internal.instr.InstrSupport.assertNotInstrumented(InstrSupport.java:238)
	at org.jacoco.agent.rt.internal_b6258fc.core.internal.instr.ClassInstrumenter.visitField(ClassInstrumenter.java:56)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassVisitor.visitField(ClassVisitor.java:338)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.readField(ClassReader.java:1137)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.accept(ClassReader.java:739)
	at org.jacoco.agent.rt.internal_b6258fc.asm.ClassReader.accept(ClassReader.java:424)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:91)
	at org.jacoco.agent.rt.internal_b6258fc.core.instr.Instrumenter.instrument(Instrumenter.java:109)
	... 58 more
BUILD SUCCESSFUL in 8s
20 actionable tasks: 20 executed
```

If I set `enableAndroidTestCoverage` to false and/or remove this config entirely, the tests pass and no errors are reported, but this value is required for jacoco coverage (which I did not setup for this test, since the issue lies in running tests via Android Studio).

Update 11/2/23: It appears that this issue has been fixed in a recent alpha version of AGP 8.3.0!
