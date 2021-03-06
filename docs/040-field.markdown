[chapter Field]

Field Manipulation using Mirror. Just to inform, field lookup is also done on 
superclasses and interfaces.

[section Reflecting]

Reflect a field by name (will return null if not found):

[java]
Class clazz;
Field f = new Mirror().on(clazz).reflect().field("fieldName");
[/java]

Reflecting all fields of a class (will return an empty list if none found):

[java]
Class clazz;
List<Field> l = new Mirror().on(clazz).reflectAll().fields();
[/java]

Reflecting all fields of a class that matches a Matcher<Field> (will return an empty list if none found):

[java]
Class clazz;
List<Field> l = new Mirror().on(clazz).reflectAll().fields()
                                     .matching(new YourCustomMatcher());
[/java]

You can also map your fields to other types:
[java]
Class clazz;
List<String> l = new Mirror().on(clazz).reflectAll().fields()
                                    .mappingTo(new YourFieldToStringMapper());
[/java]

[section Setting Values]

Setting value of a static field:

[java]
Class clazz;
new Mirror().on(clazz).set().field("fieldName").withValue(value);
[/java]

Setting value of an instance field:

[java]
Object target;
new Mirror().on(target).set().field("fieldName").withValue(value);
[/java]

You can also pass a java.lang.reflect.Field instead of fieldName String:

Setting value of a static field:

[java]
Field aField;
Class clazz;
new Mirror().on(clazz).set().field(aField).withValue(value);
[/java]

[section Getting Values]

Getting value of a static field:

[java]
Class clazz;
Object value = new Mirror().on(clazz).get().field("fieldName");
[/java]

Getting value of a instance field:

[java]
Object target;
Object value = new Mirror().on(target).get().field("fieldName");
[/java]

You can also pass a java.lang.reflect.Field instead of fieldName String:

Getting value of a static field:

[java]
Field aField;
Class clazz;
Object value = new Mirror().on(clazz).get().field(aField);
[/java]