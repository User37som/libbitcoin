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

BX is planning to implement automated code coverage metrics tooling as soon as it is available as a GitHub service for C++ projects. At this point we will have better visibility into actual test coverage. This objective is not yet achieved as coverage is known to be less than complete.

#### Quality Gate
All code should pass through a quality gate before being committed to the repository.

BX achieves this objective using [Travis](https://travis-ci.org) automated build tooling integrated with GitHub. A full build with 100% successful execution of non-functional tests is required for merging code. The quality gate test doubles as the end-user installation script, which ensures that the script is verified with any published change.  The quality gate covers all supported build targets and configurations with the exception of Windows builds which are not currently supported by Travis.