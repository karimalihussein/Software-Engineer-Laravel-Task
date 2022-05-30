<h1 align="center">
				IT Directions - Software Engineer (Task)
</h1>

<br>

This Task is designed to test an examinee’s knowledge of PHP Design principles and its implementations on Laravel framework. It is divided into 3 levels, with each feature having to be accomplished consecutively.

**Assessment Point System**: The assessment total is 125 points with additional 
Passing grade is 100. See breakdown below for more detail.

| Levels  | Points |
| ------- | -----: | 
| Level 1 |     45 |    
| Level 2 |     30 |     
| Level 3 |     50 |    
|   TOTAL |    125 |    

**Asessment Duration**: Examinee is given 3 days to complete the assessment



<br>
<hr>
<br>

<a name="Level-1"></a>
### Level 1

##### Goals

- [ ] Implement Laravel’s default login feature
- [ ] Develop User CRUD functionalities
- [ ] Make Roles and Permissions without any package

<br>

##### Prerequisites

Base the user migration file in the following table:

```mysql
mysql> show columns from users;
+-------------------+-----------------+------+-----+---------+----------------+
| Field             | Type            | Null | Key | Default | Extra          |
+-------------------+-----------------+------+-----+---------+----------------+
| id                | bigint unsigned | NO   | PRI | NULL    | auto_increment |
| firstname         | varchar(255)    | NO   |     | NULL    |                |
| lastname          | varchar(255)    | NO   |     | NULL    |                |
| username          | varchar(255)    | NO   | UNI | NULL    |                |
| email             | varchar(255)    | NO   | UNI | NULL    |                |
| password          | text            | NO   |     | NULL    |                |
| photo             | text            | YES  |     | NULL    |                |
| remember_token    | varchar(100)    | YES  |     | NULL    |                |
| email_verified_at | timestamp       | YES  |     | NULL    |                |
| created_at        | timestamp       | YES  |     | NULL    |                |
| updated_at        | timestamp       | YES  |     | NULL    |                |
| deleted_at        | timestamp       | YES  |     | NULL    |                |
+-------------------+-----------------+------+-----+---------+----------------+
```

<br>

##### Instructions

1. Start a project in Laravel 8 or higher
1. Implement the default login feature using the [laravel/ui](https://packagist.org/packages/laravel/ui) package.
1. Add a page to list all users (users.index) in a table.
1. Add a page to display a single user (users.show).
1. Add a page to display the form to create a new user (users.create).
1. Add a page to edit a user (users.edit / users.update).
1. Add a button to delete a user (users.destroy).
1. Add a page to list all soft deleted users (users.trashed).
1. Add a button to restore a soft deleted user (users.restore).
1. Add a button to permanently delete a soft deleted user (users.delete).
1. Add roles and permissions and make it simple [Admin - Employee] only admins can delete users make unit test for that
1. all that feature requires unit test

<br>

##### ✎ Notes
- All users routes must implement the `auth` middleware.


<br>

##### ★ Bonus

- **+5 points** - Write and register a route macro for soft deletes, which can be used as:
	```php
	Route::softDeletes('users', 'UserController');
	```

	which contains the following route collection:
	```php
	Route::get('users/trashed', 'UserController@trashed')->name('users.trashed');
	Route::patch('users/{user}/restore', 'UserController@restore')->name('users.restore');
	Route::delete('users/{user}/delete', 'UserController@delete')->name('users.delete');
	```

- **+2 points** - Implement a model accessor called `getAvatarAttribute` which can be used as:
	```php
	$user = User::find(1);
	$user->avatar;
	```

	<details>
	<summary>which returns the photo or a default image</summary>

	```php
	/**
	 * Retrieve the default photo from storage.
	 * Supply a base64 png image if the `photo` column is null.
	 *
	 * @return string
	 */
	public function getAvatarAttribute(): string
	{
		// Code goes brrrr.
	}
	```
	</details>

- **+3 points** - Implement a model accessor called `getFullnameAttribute` which can be used as:
	```php
	$user = User::find(1);
	$user->fullname; // E.g. Juan P. dela Cruz
	```
	<details>
	<summary>which returns the first,  and last name of the user</summary>

	```php
	/**
	 * Retrieve the user's full name in the format:
	 *  [firstname][ mi?][ lastname]
	 * Where:
	 *  [ mi?] is the optional middle initial.
	 *
	 * @return string
	 */
	public function getFullnameAttribute(): string
	{
		// Code goes brrrrr.
	}
	```
	</details>




- **+1 point** - Style the pages using a preferred framework (e.g. bootstrap, vuetify, etc.).

<br>
<hr>
<br>

<a name="Level-2"></a>
### Level 2

##### Goals

- [ ] Implement a Service Pattern for User CRUD
- [ ] Write Unit testing for the service class
- [ ] Add Validation rules to the User CRUD
- [ ] Implement a repository pattern for User CRUD
- [ ] Tracking every Employee in the system who take the actions and display it for new page the admins only can visit that page without any pacakge


<br>

##### Prerequisites

- [Level 1](#Level-1) must be fully accomplished
- [phpunit/phpunit](https://packagist.org/packages/phpunit/phpunit) package must be installed

<br>

##### Instructions

1. Create a unit test file in `/tests/Unit/Services/UserServiceTest.php`
	<details>
 	<summary>Sample UserServiceTest.php</summary>

	```php

	namespace Tests\Unit\Services;

	use Illuminate\Foundation\Testing\DatabaseMigrations;
	use Illuminate\Foundation\Testing\RefreshDatabase;
	use Illuminate\Foundation\Testing\WithFaker;
	use Tests\TestCase;

	/**
	 * @runTestsInSeparateProcesses
	 * @preserveGlobalState disabled
	 */
	class UserServiceTest extends TestCase
	{
	    use DatabaseMigrations, RefreshDatabase, WithFaker;

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_return_a_paginated_list_of_users()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_store_a_user_to_database()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_find_and_return_an_existing_user()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_update_an_existing_user()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_soft_delete_an_existing_user()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_return_a_paginated_list_of_trashed_users()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_restore_a_soft_deleted_user()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_permanently_delete_a_soft_deleted_user()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

	    /**
	     * @test
	     * @return void
	     */
	    public function it_can_upload_photo()
	    {
		// Arrangements

		// Actions

		// Assertions
	    }

		/*
		* @test
		* @return void
		*/
		public function admins_can_delete_user()
		{
			// brrrr
		}

		/*
		* @test
		* @return void
		*/
		public function regular_user_cannot_delete_user()
		{
			// brrr
		}
	}

	```
	</details>
1. Create a file `/app/Services/UserService.php`
	<details>
	<summary>Sample UserService.php</summary>

	```php

    namespace User\Services;

    use App\User;
    use Illuminate\Http\Request;
    use Illuminate\Http\UploadedFile;
    use Illuminate\Pagination\LengthAwarePaginator;

    class UserService implements UserServiceInterface
    {
        /**
         * The model instance.
         *
         * @var App\User
         */
        protected $model;

        /**
         * The request instance.
         *
         * @var \Illuminate\Http\Request
         */
        protected $request;

        /**
         * Constructor to bind model to a repository.
         *
         * @param \App\User                $model
         * @param \Illuminate\Http\Request $request
         */
        public function __construct(User $model, Request $request)
        {
            $this->model = $model;
            $this->request = $request;
        }

        /**
         * Define the validation rules for the model.
         *
         * @param  int $id
         * @return array
         */
        public function rules($id = null)
        {
            return [
                /**
                 * Rule syntax:
                 *  'column' => 'validation1|validation2'
                 *
                 *  or
                 *
                 *  'column' => ['validation1', function1()]
                 */
                'firstname' => 'required',
            ];
        }

        /**
         * Retrieve all resources and paginate.
         *
         * @return \Illuminate\Pagination\LengthAwarePaginator
         */
        public function list()
        {
            // Code goes brrrr.
        }

        /**
         * Create model resource.
         *
         * @param  array $attributes
         * @return \Illuminate\Database\Eloquent\Model
         */
        public function store(array $attributes)
        {
            // Code goes brrrr.
        }

        /**
         * Retrieve model resource details.
         * Abort to 404 if not found.
         *
         * @param  integer $id
         * @return \Illuminate\Database\Eloquent\Model|null
         */
        public function find(int $id):? Model
        {
            // Code goes brrrr.
        }

        /**
         * Update model resource.
         *
         * @param  integer $id
         * @param  array   $attributes
         * @return boolean
         */
        public function update(int $id, array $attributes): bool
        {
            // Code goes brrrr.
        }

        /**
         * Soft delete model resource.
         *
         * @param  integer|array $id
         * @return void
         */
        public function destroy($id)
        {
            // Code goes brrrr.
        }

        /**
         * Include only soft deleted records in the results.
         *
         * @return \Illuminate\Pagination\LengthAwarePaginator
         */
        public function listTrashed()
        {
            // Code goes brrrr.
        }

        /**
         * Restore model resource.
         *
         * @param  integer|array $id
         * @return void
         */
        public function restore($id)
        {
            // Code goes brrrr.
        }

        /**
         * Permanently delete model resource.
         *
         * @param  integer|array $id
         * @return void
         */
        public function delete($id)
        {
            // Code goes brrrr.
        }

        /**
         * Generate random hash key.
         *
         * @param  string $key
         * @return string
         */
        public function hash(string $key): string
        {
            // Code goes brrrr.
        }

        /**
         * Upload the given file.
         *
         * @param  \Illuminate\Http\UploadedFile $file
         * @return string|null
         */
        public function upload(UploadedFile $file)
        {
            // Code goes brrrr.
        }
    }

	```
	</details>
1. Create an Interface class file `/app/Services/UserServiceInterface.php`
	1. The Interface must have a public method called `hash(string $password): string`, which should be used when saving the password field.
		<details>
		<summary>See Sample file</summary>

		```php

		namespace App\Services;

		interface UserServiceInterface
		{
		    /**
		     * Generate random hash key.
		     *
		     * @param  string $key
		     * @return string
		     */
		    public function hash(string $key);
		}
		```
		</details>
1. Build your test cases. See the following test cases for the minimum coverage requirements:
	```
	+-------------------------------------------------+---------------------------------------------------------+------------------------------------------------------------------------------------+
	| Unit Test                                       | Coverage                                                | Remarks                                                                            |
	+-------------------------------------------------+---------------------------------------------------------+------------------------------------------------------------------------------------+
	| it_can_return_a_paginated_list_of_users         | UserService@list                                        | Must implement and return the \Illuminate\Pagination\LengthAwarePaginator instance |
	| it_can_store_a_user_to_database                 | UserService@store(array $attributes)                    |                                                                                    |
	| it_can_find_and_return_an_existing_user         | UserService@find(int $id)                               | Must use the findOrFail method of the User model.                                  |
	| it_can_update_an_existing_user                  | UserService@update(int $id, array $attributes)          |                                                                                    |
	| it_can_soft_delete_an_existing_user             | UserService@destroy(int $id)                            |                                                                                    |
	| it_can_return_a_paginated_list_of_trashed_users | UserService@listTrashed                                 |                                                                                    |
	| it_can_restore_a_soft_deleted_user              | UserService@restore(int $id)                            |                                                                                    |
	| it_can_permanently_delete_a_soft_deleted_user   | UserService@delete(int $id)                             |                                                                                    |
	| it_can_upload_photo                             | UserService@upload(\Illuminate\Http\UploadedFile $file) |                                                                                    |
	+-------------------------------------------------+---------------------------------------------------------+------------------------------------------------------------------------------------+
	```
1. If all test passed, inject the `UserService` instance to the `UserController@__construct` method.
1. Use the `UserService`'s methods inside `UserController` accordingly.
1. Add validation rules to the `UserService@rules`.
1. Create a `Request` class file `/app/Http/Requests/UserRequest.php`, and add the rules.
	<details>
	<summary>See sample `UserRequest.php`</summary>

	```php

	namespace App\Http\Requests;

	use Illuminate\Foundation\Http\FormRequest;
	use App\Services\UserServiceInterface;

	class UserRequest extends FormRequest
	{
	    /**
	     * Determine if the user is authorized
	     * to make this request.
	     *
	     * @return boolean
	     */
	    public function authorize()
	    {
		return true;
	    }

	    /**
	     * Get the validation rules that apply to the request.
	     *
	     * @return array
	     */
	    public function rules()
	    {
		
	    }
	}


	```
	</details>
1. Use the `UserRequest` class as the first parameter to `UserController@store` and `UserController@update`.
	```php
	public function store(UserRequest $request) { ... }

	public function update(UserRequest $request, int $id) { ... }
	```

<br>





<a name="Level-3"></a>
### Level 3

##### Goals

- [ ] Generate a table called <code>details</code> to save additional user background information
- [ ] Create facade to the only current user can update he's data and the admins
- [ ] use docker in the project
- [ ] make a trait to all image actions like upload or update or delete
- [ ] Generate api for retrieving all regular employees with the  [last_at, ip_address] ip he's login with and last time use sanctum for authentication

<br>


##### Instructions
new column for users table
[
	last_at,
	ip_address
]



<br>

##### ✎ Notes








<p align="center">
:four_leaf_clover:  Good luck!
</p>


