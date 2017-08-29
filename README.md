# Database 
- Table and field names MUST be lowercase and use snake_case.
- Table names should use the plural form of the actual real life object it is storing. Like for example, the table name for blog posts should be posts not post.
-Primary keys should be named “id” in the table names. While the foreign key it represents in other table should be on singularform_id. (e.g. table: post, primary key: id, foreign key: post_id )


# Coding-Style

PHP 
- Class names must be declared in StudlyCaps.
- Class constants must be declared in all upper case with underscore separators.for e.g. 
    const NEW_YEARS_DAY          = "01/01/2017"; //e.g.
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





