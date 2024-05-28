# Chapter 1: Your First Core Data App
![HitList](https://github.com/mrgsdev/Various_Tutorials/assets/157994617/8149b081-cdd4-4388-863e-0a23149ef91c)

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


## Code

```swift
import CoreData
```

```swift
var people = [NSManagedObject]()
```

```swift
override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        guard let appDelegate = UIApplication.shared.delegate as? AppDelegate else {
            return
        }
        
        let managedContext = appDelegate.persistentContainer.viewContext
        let fetchRequest = NSFetchRequest<NSManagedObject>(entityName: "Person")
        
        do {
            people = try managedContext.fetch(fetchRequest)
        } catch let error as NSError {
            print(error.userInfo)
        }
        
    }
```

```swift
func save(name:String) {
        guard let appDelegate = UIApplication.shared.delegate as? AppDelegate else { return }
        let managedContext = appDelegate.persistentContainer.viewContext
        let entity = NSEntityDescription.entity(forEntityName: "Person", in: managedContext)!
        let person = NSManagedObject(entity: entity, insertInto: managedContext)
        person.setValue(name, forKey: "name") 
        do {
            try managedContext.save()
            people.append(person)
        } catch let error as NSError {
            print(error.localizedDescription)
        }
        
    }
}
```
```swift
cell.textLabel?.text = people[indexPath.row].value(forKeyPath: "name") as? String
```
