---
description: >-
  The solutions built at the Booktower support a wide range of on- and offline
  services that rely on each other. To keep this durable, we chose a specific
  approach to building software.
---

# Architectuur Dienstverlening Boekentoren

## Event-driven approach

The systems we build listen to each other with a publish-subscribe model. We built safe-guards to make sure that if one system goes down, others can survive by the way we approached the event-driven communication: loosely coupled.

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="27:3088" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=27%3A3088&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

## Loosely-coupled

{% hint style="success" %}
We deal with software and hardware solutions that often are outdated, built with different languages and standards. The way software is built is not always within in our direct control.
{% endhint %}

We couple systems in a way they don't depend _directly_ on each other. Systems don't need to know of each other's existence nor understand each other's _language_. By using brokers (glue) and message streams, our systems can survive when one of these services go down and can easily be restarted.

If our context requires us to do so, systems can easily be interchanged by internal or external services.

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="27:3410" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=27%3A3410&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

If we want to consume information from more (external) services, our architecture is flexible enough to integrate it in a way that is suitable for our needs.

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="27:3570" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=27%3A3570&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="28:3670" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=28%3A3670&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

{% hint style="success" %}
Outside of the booktower, Ghent University and the world rely on our services, such as sharing knowledge and archiving.
{% endhint %}

Another upside specifically for our environment, is that when more (external) services want to plug in on ours this does not affect other services or overloads the system.

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="28:3754" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=28%3A3754&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

## Scaleable, interchangeable & maintainable for small teams

Building our software like this allows us to iterate over time, keeps future changes in mind, and allows for experiment in separate playgrounds. This helps our small team to prioritise and keeps complex processes manageable – and these processes won't get in each other's way.

{% @figma/embed fileId="fEJGbDVHQ4rR6rpB0emvva" nodeId="27:3181" url="https://www.figma.com/file/fEJGbDVHQ4rR6rpB0emvva/gitbook-architecture?type=design&node-id=27%3A3181&mode=design&t=dYAdkwfzAp6xRnfY-1" %}

