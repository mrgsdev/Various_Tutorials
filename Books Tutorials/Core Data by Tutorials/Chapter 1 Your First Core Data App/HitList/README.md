
# Chapter 1: Your First Core Data App

By the end of the chapter you’ll know how to:
>- [x] Model data using Xcode’s model editor
>- [x] Add new records to Core Data
>- [x] Fetch a set of records from Core Data
>- [x] Display the fetched records using a table view. 

## Key Points
>- [x] Core Data provides on-disk persistence, which means your data will be accessible even after terminating your app or shutting down your device. This is different from in-memory persistence, which will only save your data as long as your app is in memory, either in the foreground or in the background.
>- [x] Xcode comes with a powerful Data Model editor, which you can use to create your managed object model.
>- [x] A managed object model is made up of entities, attributes and relationships
>- [x] An entity is a class definition in Core Data.
>- [x] An attribute is a piece of information attached to an entity.
>- [x] A relationship is a link between multiple entities.
>- [x] An NSManagedObject is a run-time representation of a Core Data entity. You can read and write to its attributes using Key-Value Coding.
>- [x] You need an NSManagedObjectContext to save() or fetch(_:) data to and from Core Data.
