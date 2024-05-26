#### #What is reflection in Java, and why is it used?

* Reflection in Java is a feature that allows a program to inspect and manipulate its own structure at runtime. It is used to dynamically inspect classes, methods, fields, and constructors, making it possible to create flexible and generic code that can operate on objects of unknown types at compile time.

#### #Can you provide a simple example of using reflection to inspect class metadata?

* Sure! Here’s a basic example:

<pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">Class<?> clazz = String.class;
Method[] methods = clazz.getDeclaredMethods();
for (Method method : methods) {
    System.out.println(method.getName());
}
</code></div></div></pre>

#### #What are annotations in Java, and how do they differ from comments?

* Annotations in Java are a form of metadata that provide information about the code but do not affect its execution. Unlike comments, annotations can be accessed at runtime via reflection, allowing programs to retrieve metadata and use it to influence behavior.

#### #How can you create a custom annotation in Java?

* You can create a custom annotation by defining an interface with the @interface keyword and specifying any required elements. For example:

<pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface MyAnnotation {
    String value();
}
</code></div></div></pre>

#### #What is the purpose of the @Retention annotation in Java?

* The @Retention annotation specifies how long annotations with the annotated type are to be retained. It can have one of three values: SOURCE, CLASS, or RUNTIME. For example, @Retention(RetentionPolicy.RUNTIME) means the annotation will be available at runtime.

#### #How do you access annotations at runtime using reflection?

* You can access annotations at runtime by using reflection to inspect elements such as classes, methods, or fields. For example:

<pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">Method method = MyClass.class.getMethod("myMethod");
if (method.isAnnotationPresent(MyAnnotation.class)) {
    MyAnnotation annotation = method.getAnnotation(MyAnnotation.class);
    System.out.println(annotation.value());
}
</code></div></div></pre>

#### #Can you explain the difference between @Target and @Retention annotations?

* @Target specifies the kinds of program elements to which an annotation type is applicable (e.g., methods, fields, classes). @Retention specifies how long annotations are to be retained (e.g., source, class, or runtime).

#### #What is dynamic class loading, and how is it related to reflection?

* Dynamic class loading allows a program to load classes at runtime, enabling flexibility in choosing which classes to load based on runtime conditions. Reflection is often used to interact with dynamically loaded classes, allowing the program to inspect and invoke methods or access fields of those classes.

#### #What are the potential performance implications of using reflection in Java?

* Reflection can be slower than direct code because it involves types and members that must be resolved dynamically rather than statically. This dynamic resolution can introduce overhead, making reflection more resource-intensive and slower, especially when used excessively or in performance-critical sections of code.
