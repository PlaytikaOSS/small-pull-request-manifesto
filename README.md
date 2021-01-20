# Small Pull Request Manifesto

* * * * *

Background
----------

The document is aimed to describe a better process of reviewing pull requests. Current approach gives possibility to simplify and speed up the process both for reviewer and committer.

Benefits for reviewer
---------------------

-   You are able to review code quickly (within 10 minutes).
-   As a result you don't need to schedule time slot for reviewing that specific big pull request.
-   You are able to change feature design before all work is done.
-   You do not need to re-review the whole pull request, when new changes are introduced.
-   In small PRs it's more simple to find bugs.

Benefits for committer
----------------------

-   There is no endless review when each change adds more comments from reviewer.
-   You don't need to work the whole week on the changes that reviewer will reject because of the bad design.
-   No more multiple reviews on the same code.
-   Big feature is not a never ending story anymore. You can precisely say that 5/7 subtasks are already done.
-   Completing small tasks gives psychological sense of completeness.
-   Changes can be split between different developers depending on their competence, time availability etc.
-   There are more chances your pull request gets accepted ASAP as reviewer is confident in the changes.

Core requirements
-----------------

-   **Single Responsibility**: one PR makes one and only one *logical change* (business logic, configuration, technical change).
-   **Clean Code**: code follows the [Clean Code conventions](https://github.com/leonardolemie/clean-code-java).
-   **Clear Intention**: PR contents are understandable, author can quickly explain the change to everyone.
-   **Always Test**: any change should go with tests. It is acceptable to ignore some tests, specifying point at which it either
    -   *should be* unignored or
    -   *was* ignored permanently.

-   **Completeness**: PR should compile and pass tests.

Best practices
--------------

-   **Splitting:**
    -   If feature is going to be done by developer from other team, create small meeting or just discuss it in Skype.\
        Anyway before estimating task and splitting it into subtasks you need to have a small overview of code that should be changed.\
        If it takes decent amount of time to estimate task - create separate task for investigation how this task can be done.
    -   Think in terms of a task broken down into few sub-tasks. Plan better.
    -   One PR per sub-task is the best way of splitting, prefer it instead of multiple commits in single PR.
-   **Naming:**
    -   Best practice for naming each pull request is to prefix its name with [Part N]
-   **Branching model**:
    -   Create branch for story
    -   Branch subtasks from story-branch, pointing PRs to parent (story) branch
    -   When story is ready, you can choose either to squash commits or to leave them as is, after that create PR from story-branch to main development branch.
-   **Interface Extension**: When changing existing interface (e.g. method signature), try to **ADD**, and **not to REMOVE** code in 1st PR.\
    It serves two main purposes:
    -   Trace change easily
    -   Keep PR size smaller\
        Next PRs remove old interface and *integrate* new one.
-   **Optional and required tasks.** While reviewing pull request you may request optional or required changes from the committer. In case of optional change you should start your comment with *[Optional]* prefix to indicate to the committer that this change may or may be not implemented. In case of required change you should add Stash task with the tick box to the comment.
-   **Change Integration**: When developing new functionality, split PR into separate parts:

    -   Implementation: core logic with unit tests
    -   Integration: wire new code into existing infrastructure e.g. provide beans, inject dependencies, etc
    -   Tiers: for example, avoid mixing changes in persistence layer with changes in REST
-   **Refactoring**:
    -   If your change requires refactoring changes or increases technical debt -- do refactoring before main story.

-   **Self Review.** Before opening PR or when committing new changes into the PR -- review your code before giving it to other people. This way you will look at the code through the eyes of the others and will find mistakes easily.

Exceptional Cases
-----------------

-   **Renaming**: This kind of change typically affects a lot of files, but it still makes no sense to split the PR.\
    The only requirement is to ***NOT*** include any other changes except the renaming itself.
-   **Functional tests**: Sometimes it is acceptable to introduce func tests in separate PR.

How-to
------

For splitting big changes in the code into smaller, manageable parts - you can use Mikado method.
<https://www.manning.com/books/the-mikado-method>

Links
-----

-   <https://cleancoders.com/>
-   <https://dzone.com/articles/naming-conventions-from-uncle-bobs-clean-code-phil>
-   <https://smallbusinessprogramming.com/optimal-pull-request-size/>