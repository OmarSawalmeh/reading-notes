# **Sequelize-Normalization**
## **Associations**
- ## Sequelize supports the standard associations: One-To-One, One-To-Many and Many-To-Many.

To do this, Sequelize provides four types of associations that should be combined to create them:

The HasOne association
The BelongsTo association
The HasMany association
The BelongsToMany association
The guide will start explaining how to define these four types of associations, and then will follow up to explain how to combine those to define the three standard association types (One-To-One, One-To-Many and Many-To-Many).

- ## Defining the Sequelize associations
The four association types are defined in a very similar way. Let's say we have two models, A and B. Telling Sequelize that you want an association between the two needs just a function call:
```js
const A = sequelize.define('A', /* ... */);
const B = sequelize.define('B', /* ... */);

A.hasOne(B); // A HasOne B
A.belongsTo(B); // A BelongsTo B
A.hasMany(B); // A HasMany B
A.belongsToMany(B, { through: 'C' }); // A BelongsToMany B through the junction table C
```
They all accept an options object as a second parameter (optional for the first three, mandatory for belongsToMany containing at least the through property):
```js
A.hasOne(B, { /* options */ });
A.belongsTo(B, { /* options */ });
A.hasMany(B, { /* options */ });
A.belongsToMany(B, { through: 'C', /* options */ });
```
The order in which the association is defined is relevant. In other words, the order matters, for the four cases. In all examples above, A is called the source model and B is called the target model. This terminology is important.

The A.hasOne(B) association means that a One-To-One relationship exists between A and B, with the foreign key being defined in the target model (B).

The A.belongsTo(B) association means that a One-To-One relationship exists between A and B, with the foreign key being defined in the source model (A).

The A.hasMany(B) association means that a One-To-Many relationship exists between A and B, with the foreign key being defined in the target model (B).

These three calls will cause Sequelize to automatically add foreign keys to the appropriate models (unless they are already present).

The A.belongsToMany(B, { through: 'C' }) association means that a Many-To-Many relationship exists between A and B, using table C as junction table, which will have the foreign keys (aId and bId, for example). Sequelize will automatically create this model C (unless it already exists) and define the appropriate foreign keys on it.

Note: In the examples above for belongsToMany, a string ('C') was passed to the through option. In this case, Sequelize automatically generates a model with this name. However, you can also pass a model directly, if you have already defined it.

These are the main ideas involved in each type of association. However, these relationships are often used in pairs, in order to enable better usage with Sequelize. This will be seen later on.

## **Creating the standard relationships**
As mentioned, usually the Sequelize associations are defined in pairs. In summary:

To create a One-To-One relationship, the hasOne and belongsTo associations are used together;
To create a One-To-Many relationship, the hasMany and belongsTo associations are used together;
To create a Many-To-Many relationship, two belongsToMany calls are used together.
Note: there is also a Super Many-To-Many relationship, which uses six associations at once, and will be discussed in the Advanced Many-to-Many relationships guide.
This will all be seen in detail next. The advantages of using these pairs instead of one single association will be discussed in the end of this chapter.

## **One-To-One relationships**


Before digging into the aspects of using Sequelize, it is useful to take a step back to consider what happens with a One-To-One relationship.

Let's say we have two models, Foo and Bar. We want to establish a One-To-One relationship between Foo and Bar. We know that in a relational database, this will be done by establishing a foreign key in one of the tables. So in this case, a very relevant question is: in which table do we want this foreign key to be? In other words, do we want Foo to have a barId column, or should Bar have a fooId column instead?

In principle, both options are a valid way to establish a One-To-One relationship between Foo and Bar. However, when we say something like "there is a One-To-One relationship between Foo and Bar", it is unclear whether or not the relationship is mandatory or optional. In other words, can a Foo exist without a Bar? Can a Bar exist without a Foo? The answers to these questions helps figuring out where we want the foreign key column to be.

## **One-To-Many relationships**
One-To-Many associations are connecting one source with multiple targets, while all these targets are connected only with this single source.

This means that, unlike the One-To-One association, in which we had to choose where the foreign key would be placed, there is only one option in One-To-Many associations. For example, if one Foo has many Bars (and this way each Bar belongs to one Foo), then the only sensible implementation is to have a fooId column in the Bar table. The opposite is impossible, since one Foo has many Bars.

## **Many-To-Many relationships**

Many-To-Many associations connect one source with multiple targets, while all these targets can in turn be connected to other sources beyond the first.

This cannot be represented by adding one foreign key to one of the tables, like the other relationships did. Instead, the concept of a Junction Model is used. This will be an extra model (and extra table in the database) which will have two foreign key columns and will keep track of the associations. The junction table is also sometimes called join table or through table.

---
- [BACK (Main Page)](./README.md)
---

