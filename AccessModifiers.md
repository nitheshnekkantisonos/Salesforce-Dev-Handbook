
### Private

If you declare a class as private it is only known to the block in which it is declared.

-   By default all the inner classes are private.

### Public

If you declare class as a public, this class is visible throughout your application and you can access the application anywhere.

### global

If you declare a class as global, this apex class is visible to all the apex applications in the application or outside the application.

-   If a method or a class(inner) is declared as global, then the top level class also must be declared as global.

### With Sharing

If you declare a class as a With Sharing, Sharing rules given to the current user will be taken into the consideration and the user can access or perform the operations based on the permissions given to him on object and fields (Field Level Security, Sharing rules).

### Without Sharing

If you declare a class as a Without Sharing, then this Apex class runs in system mode which means Apex code has access to all the objects and field irrespective of current users  [sharing rules](https://www.tutorialkart.com/salesforce/sharing-rules-salesforce-salesforce-security/),  [field level security](https://www.tutorialkart.com/salesforce/salesforce-security-field-level-security-admin-tutorials/)  and Object permissions.

-   If the class is not declared as With Sharing or Without Sharing then the class is by default taken as With Sharing.
-   Both inner classes and outer classes can be declared as With Sharing.
-   If inner class is declared as With Sharing and top level class is declared as Without Sharing, then by default entire context will run in With Sharing Context.
-   If a class is not declared as With/Without Sharing and if this class is called by another class in which sharing rules is enforced then both the classes run with With Sharing.
-   Outer class is declared as With Sharing and inner class is declared as Without Sharing, then inner class runs in Without Sharing Context only(Inner class don’t take the Sharing properties from outer class).

### Virtual

If a class is declared with Keyword “Virtual”, then this class can be extended (Inherited) or this class methods **can** be overridden by using a class called ‘overridden’.

### Abstract

This class contains Abstract methods.then this class can be extended (Inherited) or this class methods **must** be overridden by using a class called ‘overridden’.

### Inherited Sharing
With "**Inherited Sharing**" we can run our apex code with both **with** or **without sharing** settings, depending on the context it is being called from.  

- Allows the class to run in the  **sharing mode of the class that called it**. If Apex class with Inherited Sharing is being called from some other class which is having without sharing setting, then it will run in without sharing mode.
-  Enables you to pass  **security review** and ensure that your privileged Apex code is not used in unexpected or insecure ways.
-  If a class declared as  **Inherited Sharing**, it runs as with sharing by default.
