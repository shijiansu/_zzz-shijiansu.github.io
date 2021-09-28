---
date: 2017-11-03
author: https://nordicapis.com/introduction-to-api-versioning-best-practices/
title: "Introduction to API Versioning Best Practices"
tags: ["2021", "TODO", "TO SUMMARIZE"]
categories: ["API Management", "API Versioning"]
description: >
---

Change is inevitable and growth is a good thing. When your API has reached the point of expanding beyond it’s original intent and capacity, it’s time to consider the next **version**.

Whether that next iteration is a whole number version bump or just a feature expansion, it’s important to consider the pros and cons of how you let your developers know about it. Far different than traditional software versioning, **API versioning** can have complex implications for the products using it downstream.

The big version bumps usually indicate a significant **milestone** in the codebase of the API. It declares a **significant change** in the requirements of API consumption and implementation. Feature additions that don’t necessarily change existing calls is part of the organic growth of a product and aren’t subject to the same considerations.

Once you start taking things away, or dramatically changing what’s in place, it’s time to consider another version. Often, these new versions become whole new products. Although they share a common ancestry, new versions of legacy APIs require careful thought into their implementation.

> For more advanced API versioning insights, read [API Change Strategy](https://nordicapis.com/api-change-strategy/) or [What’s The Difference Between Versioning and Revisioning APIs?](https://nordicapis.com/whats-the-difference-between-versioning-and-revisioning-apis/)

## Traditional API Versioning: n+1

Service changes that can warrant a new version include: removing an operation, renaming an operation, operation parameter changes that shift data types or order, and complex structural changes of data type.

A version increment can also indicate significant changes to API consumption requirements. It can also advertise a radical change in the underlying resources offered by the API. In either case, products and platforms that rely on an API for core functionality may need a **code refactor** to adapt.

That can be time and resource intensive, so a sane and **well documented** approach to URI versioning is crucial for multiple stakeholders. Versioning can be a controversial topic within teams, and often the first question is whether to even use it.

## One URI to Rule Them All

One school of thought is to focus on **one unchanging URI** with just one set of criteria for consumption. If the API structure is changed, resources altered, or parameter set modified, then the product is re-launched with the same URI. This pushes the obligation to refactor code to downstream developers.

Tim Berners-Lee gets name dropped by proponents of this approach. He is often [quoted as saying](https://www.technologyreview.com/s/403095/sir-tim-berners-lee/) “a cool URI is one which does not change.” In context, that quote was intended to address the nascent internet which depended on hyperlinks within web pages to endure. The [connected web](http://nordicapis.com/what-is-json-ld/), at that time, was a series of information nodes.

The world has changed, though, and we work with a interconnected matrix of powerful and resource heavy web services. Once services became widespread, early approaches were similar to software version numbers. But, standalone software has very different downstream implications than interdependent web services.

IBM addresses this in their own “[Best practices for Web services](https://www.ibm.com/developerworks/webservices/library/ws-version/)“:

> “The correct handling of API versioning has been one of the most difficult issues faced by developers of distributed systems. Various schemes have been proposed, ranging from the laissez faire approach taken by CORBA (Common Object Request Broker Architecture) to the stricter schemes used in DCOM (Distributed Component Object Model). With the advent of Web services, there are some new features that you can take advantage of that can help alleviate the problem, but the brutal fact of the matter is that versioning has not been built into the Web services architecture.”

What constitutes “best practices” has evolved over time and is determined by provider choices for their own products, not necessarily from any outside governing body. So, when it comes to choosing an approach to versioning, there are a wide variety of practices.

## On Backwards Compatibility

Another consideration is **backwards compatibility**. For many providers of web resource APIs, this is the primary consideration. Maintaining multiple versions of a resource intensive API can be a serious drain on the time and focus of engineering teams. It can also introduce long term stability problems to services that have moved on to more modern architectures.

For many, introducing a new version that substantially changes an API is, in fact, launching a **whole new service.** Treating it as a **new product**, with **new documentation**, Service Level Agreements, tier access changes, etc., can have major business implications. Many a whiteboard has been filled with figures debating whether a change is an engineering choice or a *business shift*.

Once the decision has been made to introduce a new version, it’s helpful to look around at established providers for battle tested solutions.

> Related: [The 5 Main Business Reasons for API Retirement](https://nordicapis.com/api-lifecycle-retirement-stage-a-history-of-major-public-api-retirements/)

## Examples of Versioning in the Wild

What can we learn from the versioning practices of established web API providers? [Google](https://cloud.google.com/apis/design/versioning) comes out of the gate with a blunt affirmation of numbered versioning: “Networked APIs should use **Semantic Versioning**.” Not much wiggle room there. They also have a similarly plain system. Version indicators use the form **v.MAJOR.MINOR.PATCH**.

[Twilio](https://www.twilio.com/docs/api/rest) uses a **timestamp** in the URL, instead of a version number. [Salesforce](https://developer.salesforce.com/blogs/developer-relations/2013/10/api-versions-and-the-salesforce-metadata-api.html) opts for vXX.X in the **middle** of the URL. [Facebook](https://developers.facebook.com/docs/apps/versions) goes for prepending the version to the endpoint path. The version is actually optional, with unspecified version requests being routed to the oldest version available.

Note that the granularity offered by vX.X is usually intended for development and not necessarily for production. Check the docs first, but it’s a good idea to opt for ordinal number references in production code.

[DevOps](http://nordicapis.com/avoid-walking-on-eggshells-and-use-devops/) folks may be familiar with the **UDDI** and **WDSL** approach to version definitions. HTTP solutions are much more popular, but there is support for this kind of approach. It entails a version request through an **XML** exchange to get the proper version.

Megalithic companies like Microsoft, IBM, and Oracle have references to this method in some of their documentation. Although, HTTP version indications are accepted in many divisions and products.

Dating network **Badoo** opts for [continuous versioning](https://nordicapis.com/continuous-versioning-strategy-for-internal-apis/), where features are added and endpoints stay the same. Legacy clients can use old fields and new clients use added fields. API requests are transactional, with a feature request call made and a list of available options returned. Feature checks can serve as a sort of state request.

The [API stylebook](http://apistylebook.com/design/topics/versioning) has a few more paths to explore on versioning. Without a codified set of specifications, companies continue to explore different options.

## Version With Accept Header

A common alternative to path parameters is **header exchanges**. They can be more verbose about the expected response and are usually included anyway for an HTTP request. Having a resource specific header approach allows for other parameters (such as caching, compression, and [content negotiation](http://nordicapis.com/content-negotiation/)) to be included.

API providers often communicate **resource criteria** and limitations in their response, so developers will need to examine the header exchange anyway. Besides just response codes, common header responses include [rate limit bounds](http://nordicapis.com/stemming-the-flood-how-to-rate-limit-an-api/), [specific error messages](http://nordicapis.com/best-practices-api-error-handling/), time-based data, and more.

A clever outlier is using **MIME** types to include a version indicator. API providers register these MIME types on their backend and then users include **Accept** and **Content-type headers**. IETF legitimized this approach in [RFC4627](http://www.ietf.org/rfc/rfc4627.txt). While this does work, developers choosing this approach will inevitably end up explaining their choice to management types who state, “but it doesn’t work on HTML forms, so why do you want to do it that way?”

```makefile
Accept: application/pre.company.app-v1+json
Content-Type: application/pre.company.app-v1+json
```

The debate over implementation is deep and will continue. So, developers and providers will have to make choices based on their specific needs. In general, the most common approach is a combination of **URI parameters** and **header criteria**. APIs accept URI requests with parameters and then return a payload with proper response codes and (hopefully) verbose **metadata** in the header of the response.

What constitutes a proper response code is something engineers will debate gleefully and loudly at company happy hours. But, here are some useful negative responses that are verbose enough to be helpful downstream.

```makefile
400: BAD_REQUEST: ApiVersionUnspecified: An API version is required, but was not specified
400: BAD_REQUEST: InvalidApiVersion: An API version was specified, but it is invalid
400: BAD_REQUEST: AmbiguousApiVersion: An API version was specified multiple times with different values
400, 405: BAD_REQUEST, METHOD_NOT_ALLOWED: UnsupportedApiVersion: The specified API version is not supported
301: MOVED_PERMANENTLY: movedPermanently: This request and future requests for the same operation have to be sent to the URL specified in the Location header of this response instead of to the URL to which this request was sent
410: GONE: deleted: The request failed because the resource associated with the request has been deleted
299: OK: Warning: "Deprecated API"
```

For More on Error Responses read: [Best Practices for API Error Handling](https://nordicapis.com/best-practices-api-error-handling/)

## Business Motives Will Direct Versioning Choices

In some ways, the technical aspects of versioning are the easiest to work out. The real debate comes down to product needs, **business concerns**, and future plans. The requirements for supporting multiple versions of an API can be very high in terms of engineering support, backend resources, and simple bandwidth.

Also, to be done well, a new version needs **rich documentation** to successfully transition. Since up-to-date documentation is often low on the priorities of fast moving companies, it can end up getting launched poorly as a mashup of old documentation and new. Bad documentation can yield deep costs in time and money.

The main takeaway here is that versioning is a **multi-faceted** conversation. It’s not just a technical problem. The downstream effects and legacy costs can be substantial and the entire process should be well thought out for effective growth.
