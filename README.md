# HeavyWater Machine Learning Problem

### Solution:
The code for modeling process is present in "Document classification.ipynb." Please open the file to see the steps followed.
The Flask Application is a lightweight web application which I have deployed on AWS Elastic Beanstalk.
URL: http://heavywater-document-classifier.us-east-2.elasticbeanstalk.com/.
A working cURL command is added at the end of this readme file.

### Purpose

The purpose of this problem is to evaluate your abilities in several dimensions at once.

  1. Do you understand the principles of ML/AI/data science/<insert fancy other term here>
  1. Can you build something that works
  1. Do you have a grasp of the tool chain from code on your local to code in production
  1. Can you explain your design and thinking process
  1. Are you excited by learning and challenges


### Problem Statement

We process documents related to mortgages, aka everything that happens to originate a mortgage that you don't see as a borrower. Often times the only access to a document we have is a scan of a fax of a print out of the document. Our system is able to read and comprehend that document, turning a PDF into structured business content that our customers can act on.

This dataset represents the output of the OCR stage of our data pipeline. Since these documents are sensitive financial documents we have not provided you with the raw text that was extracted. Instead we have had to obscure the data. Each word in the source is mapped to one unique value in the output. If the word appears in multiple documents then that value will appear multiple times. The word order for the dataset comes directly from our OCR layer, so it should be _roughly_ in order.

Here is a sample line:

```
CANCELLATION NOTICE,641356219cbc f95d0bea231b ... [lots more words] ... 52102c70348d b32153b8b30c
```

The first field is the document label. Everything after the comma is a space delimited set of word values.

The dataset is included as part of this repo.

### Your Mission

Should you choose to accept it ...

Train a document classification model. Deploy your model to a public cloud platform (AWS/Google/Azure/Heroku) as a webservice, send us an email with the URL to you github repo, the URL of your publicly deployed service so we can submit test cases and a recorded screen cast demo of your solution's UI, its code and deployment steps. Also, we use AWS so we are partial to you using that ... just saying.


### Measurement Criteria

We will measure your solution on the following criteria:

  1. Does your webservice work?
  1. Is your hosted model as accurate as ours? Better? (think confusion matrix)
  1. Your code, is it understandable, readable and/or deployable?
  1. Do you use industry best practices in training/testing/deploying?
  1. Do you use modern packages/tools in your code and deployment pipeline like [this](https://stelligent.com/2016/02/08/aws-lambda-functions-aws-codepipeline-cloudformation/)?
  1. The effectiveness of your demo, did you frame the problem and your approach to a solution, did you explain your thinking and any remaining gaps, etc?
  1. Are we able to run your testcases against your webservice? Can we run them against our webservice?


### A few more details

Webservice spec:

- RESTful API
- Respect content-type header (application/json and text/html minimum other bonus)
- Discoverable from root path
- URL encoded GET parameter "words" returns predicted document type (confidence is a bonus) in field "prediction" and "confidence"
- HTML pages should be readable by a human and allow for action, aka input field and submit buttons etc.
- Even a broken clock is right twice a day. A working webservice is a good first goal. It could return the highest likelihood doc class.




CURL to REST API:

curl --header "Content-Type: application/json" --request POST --data "{\"words\":\"a86e61940a88 87b8193a0183 11e7ba3aad70 5768721c4059 d38820625542 6ca2dd348663 5e3551cde154 20a84e403407 b1980f7134ca a86e61940a88 3994376f7e92 7d9e333a86da 31eba8335f91 79aa7fd11cec b136f6349cf3 036087ac04f9 1dfee5aa1e4c e872b963c663 7146e19b9776 9b16d62c7990 a0e2fc3c1c98 f3ac381a9884 43af6db29054 1b6d0614f2c7 10e45001c2f2 586242498a88 a0e2fc3c1c98 ba8f19d976a8 3fc879c6be39 ce1f034abb5d a0c020166d79 6dcc75eaf823 6101ed18e42f 8d21095e8690 d19b1c129f40 48d657cd9861 4e5019f629a9 6bff0c8c1185 ce00eff819b7 ce1f034abb5d 25c57acdf805 ff478dde1f33 81757efac276 21e314d3afcc a1d5a5e41756 78192456b1f6 8f75273e5510 ba7229c9285d 4019c142c6b0 e5e97c8ea817 cd0bd661a41e 26f768da5068 6af770640118 26f768da5068 6af770640118 26f768da5068 6af770640118 dd3e0f7ead71 867946c6808d 2979f8b5c8c4 73ef9fd67984 73ef9fd67984 61dbb745c724 26f768da5068 7d0b2f99f8dc 83ea375ad9e5 0c4ce226d9fe 73ef9fd67984 de4f651eb63b fff0cfcb20d5 cbfb3eb99bea 43565b1afa44 2bcce4e05d9d 5948001254b3 2b2acdf4a3ed eb562127f33e 8f75273e5510 09aea78efbe3 2979f8b5c8c4 dd3e0f7ead71 867946c6808d e096f0c08493 edd46208dcad 14eeb8096941 843a30201b85 26f768da5068 3eee1ce2a7bf a10b45c78387 7b13c1bc3fc2 98cd9c3a1e46 07ee0b485c47 aed969aac7a8 dd82af08389c 25c57acdf805 f95d0bea231b cdf741e78626 448cca02dae6 fe081ae57a8b 7d9e333a86da cdd31b2d9892 46c88d9303da a09620dd4350 6bf9c0cb01b4 f36e139d9400 c337a85b8ef9 b9699ce57810 f11e7777d8b5 7da013d33f12 1068682ce752 1068682ce752 1068682ce752 1068682ce752 1068682ce752 1068682ce752 1068682ce752 1068682ce752 1068682ce752 b208ae1e8232 1068682ce752 a86f2ba617ec a0c020166d79 c79b01c5629d db22d00336d3 a0c020166d79 c79b01c5629d 1b6d0614f2c7 c5dcd74b40a9 586242498a88 6ca2dd348663 d38820625542 5d3575dae8b7 b0102a0ac952 9ddcc56e3e27 79aa7fd11cec 1068682ce752 1068682ce752 e4c389c90168 8b363e6fdb6a 004029493d0e f066fbe0bc6e 6ca2dd348663 d38820625542 f066fbe0bc6e 586242498a88 586242498a88 79aa7fd11cec 7d9e333a86da b0102a0ac952 b814d9d78802 45809169e7c4 1c303d15eb65 3fb23551c726 ed1e3242ee34 55da856115d3 9db5536263d8 46c88d9303da a09620dd4350 641356219cbc 81757efac276 21e314d3afcc a0c020166d79 c79b01c5629d 1b6d0614f2c7 cdd31b2d9892 422068f04236 b59e343416f7 af671fbeb212 6bc122aa4b06 cd28aa0d62e2 e67eb757a353 6d25574664d2 0a4cda7f945f 6bc122aa4b06 cd28aa0d62e2 7a403ce898a7 9db5536263d8 f2b0e028fe2c 422068f04236 b73e657498f2 1ab34730c1e0 d493c688fb66 25c57acdf805 a1bb6b4223d9 b0102a0ac952 1169f8aa8528 2bcce4e05d9d 6a01047db3ab a0e2fc3c1c98 6ce6cc5a3203 e872b963c663 1dfee5aa1e4c 9b16d62c7990 7146e19b9776 036087ac04f9 a0c020166d79 c79b01c5629d 1b6d0614f2c7 641356219cbc 422068f04236 2c7bf164f375 af671fbeb212 81757efac276 21e314d3afcc 9b16d62c7990 1dfee5aa1e4c 036087ac04f9 7146e19b9776 e872b963c663 48d657cd9861 10e45001c2f2 b136f6349cf3 43af6db29054 586242498a88 018dd28f9cb5 c5dcd74b40a9 45ec8f372a45 25c57acdf805 5be138559904 286937d51e36 b73e657498f2 1ab34730c1e0 4e5019f629a9 d1c85e82b2b6 10e45001c2f2 10e45001c2f2 5579911eff73 5c02c2aaa67b e2e1fac9af82 04503bc22789 6bdb1352a45b 5be138559904 6101ed18e42f c5dcd74b40a9 422068f04236 6a01047db3ab 81757efac276 21e314d3afcc 0a4cda7f945f b59e343416f7 6d25574664d2 6dcc75eaf823 970fa0bfadc2 3fc879c6be39 1b6d0614f2c7 4ce4bfb42e22 a0c020166d79 1a237b972095 b7a0f56f6ce8 3639741fd757 9492c7c13404 ce1f034abb5d e5e97c8ea817 62916289176e 5ee06767bc0f 2de82c64620a 93790ade6682 4357c81e10c1 a31962fbd5f3 1c303d15eb65 3fb23551c726 ed1e3242ee34 b61f1af56200 036087ac04f9 b136f6349cf3 6bff0c8c1185 e67eb757a353\"}"  http://heavywater-document-classifier.us-east-2.elasticbeanstalk.com/predict
