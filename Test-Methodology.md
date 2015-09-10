Testing is no substitute for good design. However designing for testability is a forcing function for good design. For example a rigorous approach to unit testing leads directly to smaller and less conditional units and to a significant reduction in testable surface area through [elimination of repetition](http://en.wikipedia.org/wiki/Don't_repeat_yourself). These side effects of rigorous test methodology produce measurable benefits in the reduction of code complexity.

We break test scope into three distinct categories:

##### Unit Test
In order for unit testing to be meaningful a unit must have defined boundaries. The term unit refers to the scope of source code under test. The smallest independently testable unit of source code is a function or method. Therefore we consider a unit test as that which isolates test failures to a single function or method under test. External libraries are considered tested and are therefore not required to be isolated.

Faking is the process of isolating a unit and is accomplished through overriding [virtual methods](http://en.wikipedia.org/wiki/Virtual_function), [dependency injection](http://en.wikipedia.org/wiki/Dependency_injection) and [mocking](http://en.wikipedia.org/wiki/Mock_object). To achieve unit isolation the code under test much achieve complete [inversion of control](http://en.wikipedia.org/wiki/Inversion_of_control) (IoC).

BX exposes most public functionality via classes with full virtual interfaces, allowing depending libraries to utilize these techniques in the development of testable code. Some utility functions have yet to be virtualized. BX itself does not yet achieve full IoC due primarily to the lack of an [IoC container](http://www.martinfowler.com/articles/injection.html).

##### Component Test
Component testing verifies the interaction between a set of units. Ideally this is a supplement to unit testing, not a substitute. If discrete functionality is called for by design then testing it in isolation is the only way to ensure the design objective has been met. Just as a unit test must isolate failures to the unit under test, a component test must isolate failures to the set of units under test.

Component testing can be a useful iterative design tool, but is not essential to regression detection or completeness verification. These are the respective roles of unit and functional tests. As BX itself does not yet achieve full inversion of control most test coverage is achieved through component testing.

##### Functional Test
Functional testing might also be called "acceptance testing". It consists of testing the application as a single unit, which precludes any isolation of units behind the public interface. In other words faking is not an aspect of functional testing. The application is tested using a harness that is applied to the interface that the end user is expected to utilize. The execution environment may be controlled to any extent, but the application may not be modified. Because of this it can be hard if not impossible to reach various code paths.

Functional testing is easier to implement than testing in isolation. There are no design constraints on the application. However functional testing is an unreliable indicator of regression. The application environment is not faked and therefore environmental changes can lead to spurious failures. For example, functional tests of network commands can and do fail due to situations beyond the control of the code under test.

#### No Test Hooks
We define a test hook as an interface to the production application that exists for the purpose of testing. Test hooks are also known as "back doors" and we avoid them as bad test and production practice. Functional testing is applied to the only/public interface. Code that is hard to reach in a functional environment (e.g. handling a network failure) should be covered in unit and, if desired, component testing.

BX achieves this objective by not implementing test hooks. Setters exposed for each generated argument, option and setting property are currently called only in test setup, but are intended as an integral part of the public interface as it is not expected to rely on command line processing. As such these are part of the testable surface area.

#### Declarative Tests
A complex test needs to be tested. This sounds like a problem of infinite regression, but it is not. Unconditional code is not complex, and is generally verifiable through visual inspection. On the other hand, a complex test is not provably correct or necessarily able to reliably detect regression. Complexity is the direct consequence of conditionality. Each condition doubles the number of paths through a unit. Just 10 conditions produce 1024 paths. Iteration, which implies conditionality, introduces the possibility of infinite code paths. To be a test it must be declarative. Test helpers can isolate complexity but as complex code, must be tested as well.

All BX tests are concise, declarative and visually verifiable, achieving this objective.

#### Test One Thing
Ideally a test should test only one condition. That condition should be contained in the test name so that it's clear what is being tested and so that any regression points immediately to its cause.

BX achieves this objective in all tests with the exception that return code and stream output are tested together in each command unit test.

#### Independent Tests
All tests should be able to run concurrently and in any order. Global and static state precludes this objective and is avoided. 

BX achieves this objective as a matter of design. Typical test runs are configured with concurrency and order randomization.

#### Code Coverage
All code paths within a library under test should be covered. In other words the library should provide 100% non-functional test coverage by line. Coverage metrics should be published from regular test execution. External libraries are presumed to be tested independently.

Libbitcoin repositories each integrate automated code coverage metrics via Coveralls. The coverage objective is not yet achieved as coverage is less than complete. A The bar has been established that new code must be covered and no merge may reduce net coverage.

#### Quality Gate
All code should pass through a quality gate before being committed to the repository.

BX achieves this objective using [Travis](https://travis-ci.org) automated build tooling integrated with GitHub. A full build with 100% successful execution of non-functional tests is required for merging code. The quality gate test doubles as the end-user installation script, which ensures that the script is verified with any published change.  The quality gate covers all supported build targets and configurations with the exception of Windows builds which are not currently supported by Travis. Code coverage minimums are also incorporated into the gate.