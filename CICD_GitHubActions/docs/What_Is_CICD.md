# What is CI/CD

This topic covers the background and knowledge of CI/CD.

## What is CI

"CI" stands for "Continuous Integration".

Continuous Integration is the automation process of building, testing and merging code changes of an application to a shared repository.

For example, when a developer pushes code to his or her branch on the repository, the pushed code will automatically be built and tested via CI scripts.

This will ensure that the code is able to build properly and run smoothly without any bugs.

Afterwards, the developer can open a pull request, where the code can be automatically merged into the development branch after the CI scripts have been successfully run.

### History

The term Continuous Integration was first used by [Grady Booch](https://research.ibm.com/people/grady-booch) in 1994 (Karuturi, _An Introduction to Continuous Integration_).

It was used in Booch's book, [_Object-Oriented Analysis and Design with Applications_](https://a.co/d/9GV8wO5) (Sharma, 2018):

“The needs of the micro process dictate that many more internal releases to the development team will be accomplished, with only a few executable releases turned over to external parties.

These internal releases represent a sort of continuous integration of the system, and exist to force closure of the micro process.”

He also writes that testing should “be a continuous activity during the development process”.

Therefore, testing and continuous integration have been interconnected since early on.

Later, in 1997, Kent Beck and Ron Jeffries had brought the concept of Continuous Integration into practice while they were working on Chrysler Comprehensive Compensation System Project (Karuturi, _An Introduction to Continuous Integration_).

## What is CD

"CD" stands for "Continuous Delivery" and/or "Continuous Deployment".

Continuous Delivery ensures that it takes little effort to deliver new code that has been automatically tested and uploaded to the repository.

Basically, it ensures that the software is always ready to be deployed.

Continuous Delivery also requires Continuous Integration.

It relies on similar principles like cutting work into small increments (Sharma, 2018).

Continuous Deployment is similar to Continuous Delivery.

Instead of delivering new code however, it deploys changes from repository to production.

This deployment only occurs when all tests that have been run on the new changes pass successfully.

This new release is usable by customers.

### History

The concept of Continuous Delivery and Continuous Development came about around 2009 (Jonathan, 2021).

According to authors of the book [Continuous Delivery](https://amzn.to/3o80E15) Jez Humble and Dave Farely, Continuous Delivery and Continuous Development, as a concept, are “in essence the principle of continuous integration [pipelines] taken to its logical conclusion”.

## Next Topic

[What is GitHub Actions](./What_Is_GitHub_Actions.md)
