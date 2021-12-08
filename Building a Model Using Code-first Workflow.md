# Building a Model Using Data-base First Workflow 



## Code First with A New Database

### Step 1
Open Package Manager Console
Import Entity Framework
 
    initial-package EntityFramework

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


