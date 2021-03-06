ClickatellJavaLibrary
=====================

This is a basic library to demonstrate the use of the Clickatell Rest and HTTP APIs.

Usage
-----

The class files can be copied directly into your project, then reference the json-simple-1.1.1.jar library. and then use as follows:

To initialize:

```
ClickatellHttp click = new ClickatellHttp(USERNAME, APIID, PASSWORD);
ClickatellRest clickRest = new ClickatellRest(API_KEY);
```

To send one message:

```
ClickatellHttp.Message response = click.sendMessage("27821234567",
                    "Hello, this is a test message!");
ClickatellRest.Message response = clickRest.sendMessage("27821234567",
                    "Hello, this is a test message!");
```

To get the status of a message:

```
int status = click.getMessageStatus("b305c3445e37626ffabb21edc9320e1e");
```

To get the cost of a message:

```
ClickatellHttp.Message reply = click.getMessageCharge("b305c3445e37626ffabb21edc9320e1e");
System.out.println("Charge: " + reply.charge);
System.out.println("Status: " + reply.status);
```

To get the cost and status of message in REST:

```
ClickatellRest.Message msg = clickRest.getMessageStatus(response.message_id);
System.out.println("ID:" + msg.message_id);
System.out.println("Status:" + msg.status);
System.out.println("Status Description:" + msg.statusString);
System.out.println("Charge:" + msg.charge);
```

To do a coverage check:

```
double reply = click.getCoverage("27820909090");
```

To do a message stop request:

```
click.stopMessage("b305c3445e37626ffabb21edc9320e1e");
```

To check your balance:

```
double balance = click.getBalance();
```

Testing Sample Code
-------------------

Compile:

```
javac -cp json-simple-1.1.1.jar ClickatellRest.java ClickatellHttp.java Runner.java
```

Run:

```
java -cp .:json-simple-1.1.1.jar Runner
```