

# \[Name]

**Description:**
\[General description of the Name]

---

## Table (Markdown)

**Description:** General description of the table

| Column      | Type           | Description                    | Mass Assignment | Relationships |
| ----------- | -------------- | ------------------------------ | --------------- | -------------- |
| id          | BIGINT (PK)    | Primary key                    | —               |                |
| name        | VARCHAR(150)   | Example: Name of the record    | fillable        |                |
| slug        | VARCHAR(150)   | URL-friendly unique identifier | fillable        |                |
| description | TEXT NULL      | Optional description text      | fillable        |                |
| is_active   | TINYINT(1)     | Active flag (true/false)       | fillable        |                |
| created_at  | TIMESTAMP      | Record creation time           | —               |                |
| updated_at  | TIMESTAMP      | Record update time             | —               |                |
| deleted_at  | TIMESTAMP NULL | Soft delete timestamp          | —               |                |

---

## Relationships (High-Level)

* \[List the relationships here manually for quick reference]

---

## Artisan Command

```bash
php artisan make:model [ModelName] -a
```

---

## Laravel – Migration

File: `database/migrations/[timestamp]_create_[table_name]_table.php`
**Description:** Full migration with comments and support for local/international data.

```php
<?php
/**
 * --------------------------------------------------
 * Migration: [Table Name]
 * --------------------------------------------------
 * Notes:
 * - This migration creates the [table_name] table
 * - Set Engine/Charset/Collation if needed
 * - Add all fields here
 * - Use softDeletes() if needed
 * - Remember to add indexes
 */
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration {
    public function up(): void {
        Schema::create('[table_name]', function (Blueprint $table) {
            // Engine/charset (optional):
             $table->engine = 'InnoDB';
             $table->charset = 'utf8mb4';
             $table->collation = 'utf8mb4_unicode_ci';
             $table->comment('Table comment');

            // Primary key
            $table->id()->comment('Primary Key');

            // Example columns:
             $table->string('name', 150)->comment('Name of the item');
             $table->boolean('is_active')->default(true)->comment('Active flag');

            // Timestamps & Soft deletes
            $table->timestamps();
            $table->softDeletes();

            // Index examples:
             $table->unique('slug', 'uq_[table_name]_slug');
             $table->index('name', 'idx_[table_name]_name');
        });
    }

    public function down(): void {
        Schema::dropIfExists('[table_name]');
    }
};

```

---


## Seeder
File: `database/seeders/[TableName]Seeder.php`

```php
<?php
/**
 * --------------------------------------------------
 * Seeder: [TableName]
 * --------------------------------------------------
 * Notes:
 * - This seeder populates the [table_name] table with initial data
 * - Can be used to model the data import file
 * - Add default or example records
 * - Can use Factory or direct insert
 */
namespace Database\Seeders;

use Illuminate\Database\Seeder;
use App\Models\[ModelName];

class [TableName]Seeder extends Seeder
{
    /**
     * Run the database seeds.
     */
    public function run(): void
    {
        // Example: insert static records (one or many)
        [ModelName]::insert([
            [
                 'name' => 'Example One',
                 'slug' => 'example-one',
                 'is_active' => true,
                 'created_at' => now(),
                 'updated_at' => now(),
            ],
            [
                 'name' => 'Example Two',
                 'slug' => 'example-two',
                 'is_active' => true,
                 'created_at' => now(),
                 'updated_at' => now(),
            ],
        ]);

        // OR use factory for fake data:
        // [ModelName]::factory()->count(10)->create();
    }
}

```

Register in DatabaseSeeder.php:
```php
$this->call([TableName]Seeder::class);
```

## Factory

File: `database/factories/[TableName]Factory.php`

```php
<?php
/**
 * --------------------------------------------------
 * Factory: [TableName]Factory
 * --------------------------------------------------
 * Notes:
 * - Use Faker to generate realistic test data
 * - Factories are mainly for seeding and testing
 * - Always match generated data with your table schema
 */
namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;
use App\Models\[ModelName];

class [TableName]Factory extends Factory
{
    /**
     * The name of the factory's corresponding model.
     *
     * @var string
     */
    protected $model = [ModelName]::class;

    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition(): array
    {
        return [
            // Example fields (replace with real columns):
            'name' => $this->faker->company,
            'slug' => $this->faker->unique()->slug,
            'is_active' => true,
        ];
    }
}
```


---


## Laravel – Model

File: `app/Models/[ModelName].php`

```php
<?php
/**
 * --------------------------------------------------
 * Model: [ModelName]
 * --------------------------------------------------
 * Notes:
 * - Define fillable fields to allow mass assignment
 * - Define casts (json, boolean, datetime, etc.)
 * - Define relationships (hasMany, belongsTo, etc.)
 */
namespace App\Models;

use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;
use Illuminate\Database\Eloquent\Factories\HasFactory;

class [ModelName] extends Model
{
    use HasFactory;
    use SoftDeletes;

    /**
     * --------------------------------------------------
     * Table configuration
     * --------------------------------------------------
     */

    /**
     * The table associated with the model.
     *
     * @var string
     */
    protected $table = '[table_name]'; // Explicit table name if not plural

    /**
     * The primary key for the table.
     *
     * @var string
     */
    protected $primaryKey = 'id';

    /**
     * Indicates if the IDs are auto-incrementing.
     *
     * @var bool
     */
    public $incrementing = true;

    /**
     * The data type of the primary key.
     *
     * @var string
     */
    protected $keyType = 'int';

    /**
     * Indicates if the model should have timestamps.
     *
     * @var bool
     */
    public $timestamps = true;

    /**
     * --------------------------------------------------
     * Mass assignment & casting
     * --------------------------------------------------
     */

    /**
     * --------------------------------------------------
     * Mass Assignment
     * --------------------------------------------------
     * Notes:
     * - $fillable: attributes allowed for mass assignment
     * - Always list only safe, user-fillable fields
     */
    protected $fillable = [
        // 'name',
        // 'slug',
        // 'description',
        // 'is_active',
    ];

    /**
     * --------------------------------------------------
     * Hidden Attributes
     * --------------------------------------------------
     * Notes:
     * - $hidden: attributes hidden from array/JSON serialization
     * - Useful for sensitive fields like passwords, tokens, etc.
     */
    protected $hidden = [
        // 'password',
        // 'remember_token',
    ];

    /**
     * --------------------------------------------------
     * Attribute Casting
     * --------------------------------------------------
     * Notes:
     * - $casts: defines how attributes should be cast when accessed
     * - Supported types: boolean, integer, datetime, array, json, etc.
     */
    protected $casts = [
        // 'is_active' => 'boolean',
        // 'created_at' => 'datetime',
        // 'meta_json' => 'array',
    ];

    /**
     * --------------------------------------------------
     * Guarded Attributes
     * --------------------------------------------------
     * Notes:
     * - $guarded: attributes NOT mass assignable
     * - Opposite of $fillable (you can use one or the other, not both)
     * - Setting it to [] means all attributes are mass assignable
     */
    protected $guarded = [
        // 'id',
        // 'created_at',
        // 'updated_at',
    ];

     /**
     * --------------------------------------------------
     *  Eloquent: Relationships
     * --------------------------------------------------
     */

    /**
    * --------------------------------------------------
    * Relationships (Reusable Template)
    * --------------------------------------------------
    * Notes:
    * - استبدل [RelatedModel], [pivot_table], [foreign_key], [owner_key], [local_key]
    * - classic: hasOne/hasMany/belongsTo/belongsToMany
    * - through & polymorphic موجودين لو تحتاجهم
    */

    /* ------- Classic ------- */

    // One-To-One
    // public function [singular](): \Illuminate\Database\Eloquent\Relations\HasOne
    // {
    //     return $this->hasOne([RelatedModel::class], '[foreign_key]', '[local_key]');
    // }

    // One-To-Many
    // public function [plural](): \Illuminate\Database\Eloquent\Relations\HasMany
    // {
    //     return $this->hasMany([RelatedModel::class], '[foreign_key]', '[local_key]');
    // }

    // Belongs-To (inverse)
    // public function [owner](): \Illuminate\Database\Eloquent\Relations\BelongsTo
    // {
    //     return $this->belongsTo([RelatedModel::class], '[foreign_key]', '[owner_key]')
    //                 ->withDefault();
    // }

    // Many-To-Many (pivot)
    // public function [plural](): \Illuminate\Database\Eloquent\Relations\BelongsToMany
    // {
    //     return $this->belongsToMany([RelatedModel::class], '[pivot_table]', '[this_fk]', '[related_fk]')
    //                 ->withPivot(['position'])   // optional
    //                 ->withTimestamps();         // optional
    // }

    /* ------- Through ------- */

    // hasOneThrough
    // public function [singular]Through(): \Illuminate\Database\Eloquent\Relations\HasOneThrough
    // {
    //     return $this->hasOneThrough([FinalModel::class], [IntermediateModel::class]);
    // }

    // hasManyThrough
    // public function [plural]Through(): \Illuminate\Database\Eloquent\Relations\HasManyThrough
    // {
    //     return $this->hasManyThrough([FinalModel::class], [IntermediateModel::class]);
    // }

    /* ------- Polymorphic ------- */

    // morphOne
    // public function [singular](): \Illuminate\Database\Eloquent\Relations\MorphOne
    // {
    //     return $this->morphOne([RelatedModel::class], '[morph_name]');
    // }

    // morphMany
    // public function [plural](): \Illuminate\Database\Eloquent\Relations\MorphMany
    // {
    //     return $this->morphMany([RelatedModel::class], '[morph_name]');
    // }

    // morphTo (inverse)
    // public function [morphable](): \Illuminate\Database\Eloquent\Relations\MorphTo
    // {
    //     return $this->morphTo();
    // }

    // morphToMany
    // public function [plural](): \Illuminate\Database\Eloquent\Relations\MorphToMany
    // {
    //     return $this->morphToMany([RelatedModel::class], '[morph_name]')
    //                 ->withTimestamps();
    // }

    // morphedByMany (inverse morphToMany)
    // public function [plural](): \Illuminate\Database\Eloquent\Relations\MorphedByMany
    // {
    //     return $this->morphedByMany([RelatedModel::class], '[morph_name]')
    //                 ->withTimestamps();
    // }

    /* ========== Extras & Scopes ========== */

    /**
    * Constrained relationship example
    * - Filters related records (e.g. only active) and orders by a column.
    */
    // public function active[RelatedModel]s(): \Illuminate\Database\Eloquent\Relations\HasMany
    // {
    //     return $this->hasMany([RelatedModel]::class)
    //                 ->where('is_active', true)
    //                 ->orderBy('name');
    // }

    /**
    * Local query scopes (recommended for reusable filters)
    * Usage: [ModelName]::active()->ordered()->get();
    */
    // public function scopeActive($query)
    // {
    //     return $query->where('is_active', true);
    // }
    //
    // public function scopeOrdered($query, $column = 'name', $direction = 'asc')
    // {
    //     return $query->orderBy($column, $direction);
    // }

    /**
    * Eager load defaults
    * - Always load these relationships with the model.
    * Example (place at class level):
    *
    * protected $with = ['[relatedModel1]', '[relatedModel2]'];
    */

    /**
    * Touch parents on save
    * - Updates the parent's updated_at when this model is saved.
    * Example (place at class level):
    *
    * protected $touches = ['[relatedModel]']; // triggers [relatedModel]->updated_at
    */

     /**
     * --------------------------------------------------
     *  Function  
     * --------------------------------------------------
     */ 

    /* ========== Custom Functions (Put at the end of the Model) ========== */

    /**
     * --------------------------------------------------
     * Notes:
     * - Add any custom functions here
     * - Examples: file upload, image handling, notifications, helpers
     * - Keep reusable logic here to keep controllers clean
     */
}
```

---

## Controller

File: `app/Http/Controllers/[ControllerName].php`

```php
<?php
/**
 * --------------------------------------------------
 * Controller: [ControllerName]
 * --------------------------------------------------
 * Notes:
 * - Basic CRUD operations
 * - Add search/filter if needed
 * - Includes __construct for middleware or auth
 * - Includes soft delete helpers (restore & forceDelete)
 */
namespace App\Http\Controllers;

use App\Http\Requests\Store[ModelName]Request;
use App\Http\Requests\Update[ModelName]Request;
use App\Http\Resources\[ModelName]Resource;
use App\Models\[ModelName];

class [ControllerName] extends Controller
{
    /**
     * --------------------------------------------------
     * Constructor
     * --------------------------------------------------
     * Example: Add middleware here if needed
     */
    public function __construct()
    {
        // $this->middleware('auth:api');
    }

    /**
     * Display a listing of the resource.
     */
    public function index()
    {
        // Default pagination
        $items = [ModelName]::paginate(20);

        return [ModelName]Resource::collection($items);
    }

    /**
     * Show the form for creating a new resource.
     */
    public function create()
    {
        return new [ModelName]Resource();
    }

    /**
     * Store a newly created resource in storage.
     */
    public function store(Store[ModelName]Request $request)
    {
        $item = [ModelName]::create($request->validated());

        return new [ModelName]Resource($item);
    }

    /**
     * Display the specified resource.
     */
    public function show([ModelName] $item)
    {
        return new [ModelName]Resource($item);
    }

    /**
     * Show the form for editing the specified resource.
     */
    public function edit([ModelName] $item)
    {
        return new [ModelName]Resource($item);
    }

    /**
     * Update the specified resource in storage.
     */
    public function update(Update[ModelName]Request $request, [ModelName] $item)
    {
        $item->update($request->validated());

        return new [ModelName]Resource($item);
    }

    /**
     * Soft delete the specified resource from storage.
     */
    public function destroy([ModelName] $item)
    {
        $item->delete();

        return response()->noContent();
    }

    /**
     * --------------------------------------------------
     * SoftDeletes Support
     * --------------------------------------------------
     */

    // Get all soft deleted records
    public function trashed()
    {
        $items = [ModelName]::onlyTrashed()->paginate(20);

        return [ModelName]Resource::collection($items);
    }

    // Restore a soft deleted record
    public function restore($id)
    {
        $item = [ModelName]::onlyTrashed()->findOrFail($id);
        $item->restore();

        return new [ModelName]Resource($item);
    }

    // Permanently delete a record
    public function forceDelete($id)
    {
        $item = [ModelName]::onlyTrashed()->findOrFail($id);
        $item->forceDelete();

        return response()->noContent();
    }
}
```


## Requests

### Store Request

File: `app/Http/Requests/Store[ModelName]Request.php`

```php
<?php
/**
 * --------------------------------------------------
 * Store Request
 * --------------------------------------------------
 * Notes:
 * - Define validation rules for creating records
 * - authorize() controls who can access this request
 */
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class Store[ModelName]Request extends FormRequest
{
    /**
     * Determine if the user is authorized to make this request.
     */
    public function authorize(): bool
    {
        // Example: allow all authenticated users
        // return auth()->check();

        // Default: allow everyone (adjust if needed)
        return true;
    }

    /**
     * Get the validation rules that apply to the request.
     */
    public function rules(): array
    {
        return [
            // 'name' => 'required|string|max:150'
        ];
    }
}
```

---

### Update Request

File: `app/Http/Requests/Update[ModelName]Request.php`

```php
<?php
/**
 * --------------------------------------------------
 * Update Request
 * --------------------------------------------------
 * Notes:
 * - Validation rules for updating records
 * - authorize() controls who can access this request
 */
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class Update[ModelName]Request extends FormRequest
{
    /**
     * Determine if the user is authorized to make this request.
     */
    public function authorize(): bool
    {
        // Example: only admins can update
        // return auth()->user()?->isAdmin() ?? false;

        // Default: allow everyone (adjust if needed)
        return true;
    }

    /**
     * Get the validation rules that apply to the request.
     */
    public function rules(): array
    {
        $id = $this->route('[table_name]')?->id;

        return [
            // 'name' => 'required|string|max:150|unique:[table_name],name,' . $id,
        ];
    }
}
```

---

بهذا الشكل التمبليت صار رسميًا يحتوي على:

* `authorize()` لكل **Store** و **Update Request**.
* ملاحظات واضحة إنك تقدر تخليها `auth()->check()` أو شرط ثاني (مثلاً admin).

تحب أطبّق نسخة `brands.md` مرّة ثانية بهالـ update الجديد (مع authorize) عشان تشوفه مطبّق كامل؟

## Policy

File: `app/Policies/[ModelName]Policy.php`

```php
<?php
/**
 * --------------------------------------------------
 * Policy: [ModelName]Policy
 * --------------------------------------------------
 * Notes:
 * - Control authorization for CRUD actions
 */
namespace App\Policies;

use App\Models\User;
use App\Models\[ModelName];

class [ModelName]Policy
{
    public function viewAny(User $user) { return true; }
    public function view(User $user, [ModelName] $item) { return true; }
    public function create(User $user) { return true; }
    public function update(User $user, [ModelName] $item) { return true; }
    public function delete(User $user, [ModelName] $item) { return true; }
}
```

---

