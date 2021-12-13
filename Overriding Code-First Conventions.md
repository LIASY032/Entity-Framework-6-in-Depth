# Overriding Code-First Conventions

## Data Annotation
Table Name
```c#
[Table("tbl_Course"), Schema="catalog"]
public class Course
```

Column Name
```c#
[Column("sName"), TypeName="varchar"]
public string Name {get; set;}
```
Primary Key
```c#

[Key]
[DatabaseGenerated(DatabaseGeneratedOption.None)] 
public string ISBN {get; set;}
```


Composite Keys


```c#
public class OrderItem
{
    [Key]
    [Column(Order =1)]
    public init OrderID {get; set;}
    [Key]
    [Column(Order =2)]
    public init OrderItemID {get; set;}
}
```

Nulls
```c#
[Required]
public string Name {get; set;}
```
Length of Strings
```c#
[MaxLength(255)]
public string Name {get; set;}
```


Index

```c#
[Index(IsUnique = true)]
public string Name {get; set;}
```

```c#
[Index("IX_AuthorStudentsCount"), 1]
public int AuthorId {get; set;}
[Index("IX_AuthorStudentsCount"), 2]
public int StudentsCount {get; set;}
```


Foreign Keys
```c#
public class Course
{
     [ForeignKey("AuthorId")]
    public int AuthorId {get; set;}

   
    public Author Author {get; set;}
}
```



## Fluent API
```c#
protected override void OnModelCreating(DbModelBuilder modelBuilder)
{
    // Apply configuration using Fluent API
    
    //Basics
    modelBuilder.Entity<Course>()


    //Table Names
    modelBuilder.Entity<Course>().ToTable("tbl_Course");

    //Primary Keys
    modelBuilder.Entity<Book>().HasKey(t => t.ISBN);


    // Composite Keys
    modelBuilder.Entity<OrderItem>().HasKey(t => new {t.OrderId, t.OrderItemId});

    //Column Names
    modelBuilder.Entity<Course>().Property(t => t.Name).HasColumnName("sName");

    //Column Types
    modelBuilder.Entity<Course>().Property(t => t.Name).HasColumnType("varchar");

    //Column Orders
    modelBuilder.Entity<Course>().Property(t => t.Name).HasColumnOrder(2);

    //Database Generated
    modelBuilder.Entity<Book>().Property(t => t.ISBN).HasDatabaseGeneratedOption(DatabaseGeneratedOption.None);

    //Nulls
    modelBuilder.Entity<Course>().Property(t => t.Name).IsRequired();


    //Length of Strings
    modelBuilder.Entity<Course>().Property(t => t.Name).HasMaxLength(255);

}

```
