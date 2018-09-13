# AndroidX + Android Test Orchestrator Bug

This repo demonstrates a bug where tests are not properly run when the following conditions are met:
1. `android.useAndroidX=true` and `android.enableJetifier=true` are enabled in `gradle.properties`
2. Having `testOptions { execution 'ANDROID_TEST_ORCHESTRATOR' }` in the module's `android` block 
where the test(s) reside

## Steps to reproduce
1. Ensure that `android.useAndroidX=true` and `android.enableJetifier=true` are enabled in 
`gradle.properties`
2. Ensure `testOptions { execution 'ANDROID_TEST_ORCHESTRATOR' }` is present in the `app` module's
`android` block
3. Run `ExampleInstrumentedTest`

When the tests are run, the test should print:
```
Client not ready yet..
Started running tests
Tests ran to completion.
Empty test suite.
```

## To verify that this config worked in the first place
1. `git checkout pre_androidx`
2. Run `ExampleInstrumentedTest`

When tests are run, you should see the single test pass.
