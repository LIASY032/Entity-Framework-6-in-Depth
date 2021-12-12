# Building a Model Using Data-base First Workflow 



## Code First with A New Database

### Step 1
Open Package Manager Console
Import Entity Framework
 ```bash
initial-package EntityFramework
```
### Step 2
Make sure a class inherited from : DbContext
 DbSet represents a table
Ex:
```c#
  public class PlutoContext : DbContext
    {
        public DbSet<Course> Courses { get; set; }
        public DbSet<Author> Authors { get; set; }
        public DbSet<Tag> Tags { get; set; }

        public PlutoContext()
            : base("name=DefaultConnection")
        {

        }
    }

```


### Step 3
Open App.config or Web.config
add below in configuration tag
```
	<connectionStrings>
		<add name="DefaultConnection" connectionString="data source=(localdb)\MSSQLLocalDB; initial catalog=PlutoCodeFirst; integrated security=SSPI" providerName="System.Data.SqlClient"/>
	</connectionStrings>
```
DefaultConnection is used by PlutoContext base
source is your server name
initial catalog is database name
integrated security=SSPI means Windows Authentication

### Step 4
Open Package Manager Console
InitialModel is the name of the model; you can type any name you want
```bash
enable-migrations
add-migration InitialModel
update-database
```

## Code First with Existing Database
![77547673fbb467974bd9abc80188c1e](https://user-images.githubusercontent.com/66517361/145331241-d742b887-cd26-4894-bbf7-57ead2b32e5f.png)

### Step 1
Add New Item then choose ADO.NET Entity Data Model
![e7e50062389a907252cf6c750a9345f](https://user-images.githubusercontent.com/66517361/145331254-b0beff0f-7159-4e3e-9b74-781dec3a0fc7.png)

### Step 2 
Choose Code First from database
![2c5f5c1dc8c5b617b2cb6d6b4c83d72](https://user-images.githubusercontent.com/66517361/145331261-b54db497-7388-47ae-ab0e-ea7b197ea92d.png)


### Step 3
Connect your server
![1639021498(1)](https://user-images.githubusercontent.com/66517361/145331272-fa465232-d881-4cab-a727-9ad1965538cf.png)


### Step 4

enable-migrations

same as step 4 above
