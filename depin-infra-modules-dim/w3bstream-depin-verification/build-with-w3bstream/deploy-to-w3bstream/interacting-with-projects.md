# Interacting with Projects

As the owner of the project NFT, you have the ability to query and interact with your W3bstream project at any time. Below are the operations you can perform on your W3bstream project:

## **Start the Project**

To start your project, use the following command:

```sh
ioctl ws project resume --id 1234
```

## **Query the Project**&#x20;

To query the status or details of your project, use the following command:

```sh
ioctl ws project query --id 1234
```

## **Set Required Prover Amount for the Project**

By default, the prover amount that processes the project's tasks is set to one. You can customize this amount using the following command:

```sh
ioctl ws project attributes set --id 1234 --key "RequiredProverAmount" --val "your expected amount"
```

## **Stop the Project**

If you need to stop the project's task processing, use the following command:

```sh
ioctl ws project pause --id "your project id"
```
