---
title: How do you manage and use “Many to many” core data relationships?

createdAt: 2020-05-18T16:46:25Z
---

# How do you manage and use “Many to many” core data relationships?

Peter: "I have nine bosses, Bob." Bob: "Say again?" Peter: "Nine."

Take your brain out of the database. Do not ask how to access a cross-reference table. Ask how to find the employees for a manager or the managers for an employee.

If you use a custom subclass of NSManagedObject, you can declare the properties as documented. Then you can simply say:

```objective-c
NSSet *mgrsEmployees = mgr.employees;
NSSet *employeesMgrs = employee.managers;
```
That will not give you all the employees and all the managers, only all the employees for that manager and all the managers for that employee. To change relationships:

```objective-c
[mgr addEmployeesObject:newEmployee];
[newEmployee addManagersObject:mgr]; // not necessary, automatic if you define inverse

[mgr removeEmployeesObject:transferredEmployee];
[transferredEmployee removeManagersObject:mgr]; // not necessary
[newMgr addEmployeesObject:transferredEmployee];
[transferredEmployee addManagersObject:newMgr]; // not necessary
```

You only need to do either one of each pair of statements, and it will implicitly do the other, provided you have defined managers and employees as inverses of each other.

If you don't use a custom subclass, accessing is a little more verbose

```objective-c
NSSet *mgrsEmployees = [mgr valueForKey:@"employees"];
NSSet *employeesMgrs = [employee valueForKey:@"managers"];

NSMutableSet *changeMgrsEmployees = [mgr mutableSetValueForKey:@"employees"];
[changeMgrsEmployees addObject:newEmployee];
// not necessary
NSMutableSet *changeEmployeesMgrs = [employee mutableSetValueForKey:@"managers"];
[changeEmployeesMgrs addObject:mgr];
```

---

https://stackoverflow.com/questions/7572657/how-do-you-manage-and-use-many-to-many-core-data-relationships