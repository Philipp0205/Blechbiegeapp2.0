- [oop - Explanation of the UML arrows - Stack Overflow](https://stackoverflow.com/questions/1874049/explanation-of-the-uml-arrows) #[[Roam-Highlights]]
    - **UML Class Diagrams: Reference**: 
    
 
    - ![[UML_example.png]]
    
    - **5**: **Association**: A relationship between the members of two classifiers.
    - **5a**: **Aggregation**: An association representing a shared ownership relationship. The **Aggregation** property of the owner role is set to **Shared**.
    - **5b**: **Composition**: An association representing a whole-part relationship. The **Aggregation**
    - property of the owner role is set to **Composite**.
    - **9**: **Generalization**: The specific classifier inherits part of its definition from the general classifier. The general classifier is at the arrow end of the connector. Attributes, associations, and operations are inherited by the specific classifier. Use the **Inheritance** tool to create a generalization between two classifiers.
    - ![[UML_example2.png]]
    - **13**: **Import**: A relationship between packages, indicating that one package includes all the definitions of another.
    - **14**: **Dependency**: The definition or implementation of the dependent classifier might change if the classifier at the arrowhead end is changed.
    - ![[UML_example3.png]]
    - **15**: **Realization**: The class implements the operations and attributes defined by the interface. Use the **Inheritance** tool to create a realization between a class and an interface.
    - **16**: **Realization**: An alternative presentation of the same relationship. The label on the lollipop symbol identifies the interface.
	
- **UML Class Diagrams: Guidelines**: [http://msdn.microsoft.com/library/dd409416%28VS.140%29.aspx](https://msdn.microsoft.com/library/dd409416%28VS.140%29.aspx)
    - **Properties of an Association**
    - **Aggregation**: This appears as a diamond shape at one end of the connector. You can use it to indicate that instances at the aggregating role own or contain instances of the other.
    - **Is Navigable**: If true for only one role, an arrow appears in the navigable direction. You can use this to indicate navigability of links and database relations in the software.
    - **Generalization**: Generalization means that the specializing or derived type inherits attributes, operations, and associations of the general or base type. The general type appears at the arrowhead end of the relationship.
    - **Realization**: Realization means that a class implements the attributes and operations specified by the interface. The interface is at the arrow end of the connector.
