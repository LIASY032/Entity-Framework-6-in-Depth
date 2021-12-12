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
    public int AuthorId {get; set;}

    [ForeignKey("AuthorId")]
    public Author Author {get; set;}
}
```
