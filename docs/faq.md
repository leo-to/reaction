## Frequently Asked Questions

### Is Reaction production ready?

No, not yet. We're currently in our Alpha preview release. Our [Vision page](https://reactioncommerce.com/vision) outlines what we have in store for our Beta release, which is when we'll be production ready. We are targeting Beta for late 2015.

### What's your roadmap for Reaction?

Our [Vision page](https://reactioncommerce.com/vision) outlines our roadmap and plans for Reaction. And here's our [project board](https://waffle.io/reactioncommerce/reaction).

### Do you offer hosted shops?

Yes. When you create a shop on our platform at [reactioncommerce.com](https://reactioncommerce.com), this launches a shop running the most current version of Reaction, and runs it on Docker, via Amazon EC2, with its own MongoHQ-powered database. Keep in mind that shops that are created during our Alpha release aren't guaranteed to always be up and running. If your shop becomes inactive, you can visit your Control Panel and click the Restart button to get it going again.

### Is it possible for me to host a Reaction shop anywhere I want?

Yes. You can host a Reaction shop on any host/virtual machine container that supports Meteor/Node.js and MongoDB. Our code is fully open source on GitHub at [github.com/reactioncommerce/reaction](https://github.com/reactioncommerce/reaction).

### Do you support multiple languages?

Yes. We have [internationalization support](https://github.com/reactioncommerce/reaction-core/blob/master/docs/i18n.md) for numerous languages, and we support currency conversion and localized currency formats.

### What is the pricing/licensing model?

Reaction Commerce is currently free, and there will always be a free, open source version available. Eventually, we will offer premium plans with tiered pricing structures on the reactioncommerce.com platform. Our code is licensed under the GPL v3 license. The Terms & Conditions for shops hosted on our reactioncommerce.com platform can be found at [https://reactioncommerce.com/terms](https://reactioncommerce.com/terms).

### Is MongoDB/NoSQL best suited for ecommerce?

We think so! We believe that the common SQL schema for legacy ecommerce platforms isn't just unnecessary; it's overkill. By rethinking the way the database is architected, there are numerous benefits of Mongo/NoSQL -- from speed to simplified code.

We enforce all of the typical joins, cascades, shemas, validation etc., with functionality that we have included (collections, schemas, hooks, helpers). But instead of trying to join a bunch of stuff together, we simply have an object that is a product. There are huge advantages to this approach, such as speed + easy code + the schema can be easily modified to accomodate any data requirements. This is unlike legacy platforms and their use of the entity - attribute - value lookup that is so complex and slow. In fact, legacy platforms have tried to architectect their way around these very real limitations of SQL that NoSQL easily handles (using EAV). By using NoSQL, we remove the very complex layer of looking up and joining attributes, and also the complexity of adding new field/values. (You just do it to the main object, and that’s going to persist throughout the life of the object.)  We also don’t have to deal with the continuous translation of database structure to a code object.

In reality, in our use, the DB is just the persistent storage of the JavaScript objects. For example, a product is a collection of variants (objects) like blue, green, etc., and are each their own object contained within a “product” object.

In localization (l10n), this can also mean different pricing, taxes, etc., for different regions, so pricing is at the variant level not at the product level.  This is even true with just one language when you have “Blue XXL” being more expensive than “Green XL."

### Have you tested Reaction on large shops with thousands of products?

We've done general performace testing and will be doing thorough testing as part of our Beta release.

We’re building everything to be "ephermal" in nature, so "cloud" scaling is the idea from the get-go. We believe scaling won’t be the same set of issues as with legacy platforms where you have to jump through a ton of hoops to get rid of the dependancies on the server (file system, sessions, etc).

Regardless, if it's Docker or other Virtual Machine (VM) containers, the idea is that the storefront itself should scale without issues. The bottleneck does become the database, but with sharding and lots of other solutions, we think that it’s an easier problem to solve. We created Launch Dock ([launchdock.io](http://launchdock.io) and open source at [github.com/ongoworks/launchdock](https://github.com/ongoworks/launchdock)) as our project for the server-side/Docker launching. In fact, the primary purpose of “Create a Shop” on the home page of reactioncommerce.com is to test deploying shops at scale and to work out database scaling issues early. We have a MongoDB cluster running on Amazon EC2, and our newest shops are using MongoHQ’s elastic deployments.

### Reaction is an open source project, how can I get involved?

You can find step-by-step instructions for becoming a contributor here: [http://thoughts.reactioncommerce.com/how-to-get-involved-with-reaction-commerce/](http://thoughts.reactioncommerce.com/how-to-get-involved-with-reaction-commerce/).

### The Reaction platform is reliant on JavaScript to run. Does that have a negative impact on SEO?

[Google now indexes JavaScript when crawling websites](http://googlewebmastercentral.blogspot.com.es/2014/05/understanding-web-pages-better.html).

Additionally, Reaction uses the Meteor spiderable package, which uses Phantomjs to render the static page version for search engines. You can read more about the Meteor spiderable package [here](http://docs.meteor.com/#spiderable), [here](http://www.meteorpedia.com/read/spiderable/), and [here](https://www.eventedmind.com/feed/meteor-the-spiderable-package). We currently have this disabled by default, as we are still heavily in development, but if a site needed spiderable, all that you need to do to enable is 'meteor add spiderable'.
