# Steps
1) make table in db, always use id then foreign key as id unsigned int(10), setup foreign keys
2) run infoym api generator
3) delete soft deletes, and deleted_at if we're not using this column as it is not necessary
4) make sure there are not duplicate relationships. add relationships if necessary
5) wrap the resource around a guest, to confirm it works
6) give a name to the route, then make it an api route 
7) log-on to superadmin and add permissions
8) create menu item and add menu item to config.js with correct controllers and views
9) ensure you include controller to index.html and controllers.js 
10) make service  using the abstract factory and include it with the index.html
11) use the service with the controller
12) if you want to get a list of all objects then you would do <serviceName>.getList(<params>).then(function(result) { })
13) if you want to create a object <serviceName>.create(<object>)
14) if you want to use a variable in the view, then use $scope.<variableName> same goes for functions which have interaction with the view.
    
    


# Database 
- Table and field names MUST be lowercase and use snake_case.
- Table names should use the plural form of the actual real life object it is storing. Like for example, the table name for blog posts should be posts not post.
-Primary keys should be named “id” in the table names. While the foreign key it represents in other table should be on singularform_id. (e.g. table: post, primary key: id, foreign key: post_id )



-a naming convention is always necessary if the database is expected to last and evolve with the application it supports, and here are some guidelines to establish a succinct, simple, and readable one:

-No limitations on table or column name size. It is better to have a descriptive name than an acronym that no one remembers or understands.
Names that are equal have the same meaning. Avoid having fields that have the same name but with different types or meanings; this will be confusing sooner or later.

-Unless necessary, don’t be redundant. For example, in the table “Item,” there is no need to have columns like “ItemName,” “PriceOfItem,” or similar names; “Name” and “Price” are enough.

-Beware of DBE reserved words. If a column is to be called “Index,” which is a SQL reserved word, try to use a different one like “IndexNumber.”

-If sticking to the simple primary key rule (single integer auto generated), name it “Id” in every table.

-If joining to another table, define the necessary foreign key as an integer, named “Id” followed by the name of the joined table (e.g., IdItem).

-If naming constraints, use a prefix describing the constraint (e.g., “PK” or “FK”), followed by the name of the table or tables involved. Of course, using underscores (“_”) sparingly helps make things more readable.

-To name indexes, use the prefix “IDX” followed by the table name and the column or columns of the index. Also, use “UNIQUE” as a prefix or suffix if the index is unique, and underscores where necessary.

https://www.toptal.com/database/database-design-bad-practices


# Coding-Style

HTML/CSS
- follow https://www.toptal.com/front-end/frontend-clean-code-guide


PHP 
- Class names must be declared in StudlyCaps.
- Class constants should be used whenever you're setting a constant value that doesn't get changed,      const $startOfYear = "01/01/2017"; //e.g.
- Method names must be declared in camelCase
- Property names should be camelCase. 
- Code MUST use 4 spaces for indenting, not tabs.
- lines should be 80 characters or less, the max is 120 characters
- There MUST be one blank line after the namespace declaration, and there MUST be one blank line after the block of use declarations.
- The PHP constants true, false, and null MUST be in lower case.
- The var keyword MUST NOT be used to declare a property.

Models should have relevant methods and shouldn't be so much in controllers.

```php
namespace App\Models;
use Eloquent as Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Menus extends Model
{
    use SoftDeletes;

    public $table = 'menus';
    
    const CREATED_AT = 'created_at';
    const UPDATED_AT = 'updated_at';
    protected $dates = ['deleted_at'];

    public $fillable = [
        'parent_id',
        'name',
        'tool_tips',
        'icon',
        'view_name',
        'order_number'
    ];

    protected $casts = [
        'id' => 'integer',
        'parent_id' => 'integer',
        'name' => 'string',
        'tool_tips' => 'string',
        'icon' => 'string',
        'view_name' => 'string',
        'order_number' => 'integer'
    ];

  
    public static $rules = [
        
    ];

    public function roles()
    {
        return $this->belongsToMany(Role::class, 'menus_role');
    }
}
```


Angular
- controller names must always be capitalized e.g. FileController
- controller filename camelCase
- views must be camelCase
- service filename must be studlyCase
- Service name must be Capitalized e.g. FileRespository





