# Angular Reactive Forms
Materials for my Pluralsight course: ["Angular Reactive Forms"](https://app.pluralsight.com/library/courses/angular-2-reactive-forms).

`Demo-Start`: The starter files. **Use this to code along with the course**.

`Demo-Final`: The completed files. Use this to see the completed solution from the course.

`APM`: Angular reactive form in the context of a more full-featured application. Includes examples of CRUD (Create, Read, Update, and Delete) operations.

Angular v12 turns strict typing on by default. Angular forms is not very strongly typed, so some changes are required to support strict typing. Use these files if you are using Angular v12 or newer or if you turn on strict typing.

`demo-start-v12`: The starter files updated to Angular v12.

`demo-final-v12`: The completed files updated to Angular v12.

`apm-v12`: Angular reactive form in the context of a more full-featured application updated to Angular v12. Includes examples of CRUD (Create, Read, Update, and Delete) operations.

See the `README.md` file under each folder for details on installing and running the application.

Please see the `CHANGELOG.md` for the most recent changes to this repo.

### Template-Driven vs Reactive Forms

#### Template-Driven

* Easy to use
* 2 way databinding -> Minimal component code
* Automatically tracks form and input element state

#### Reactive

* More flexible and can handle more complex scenarios(Complex validation scenarios like User selection or other form state)
* Immutable data model
* Easier to perform an action on a value change(Like transforming to Uppercase or Partial Lookup)
* Access to Reactive tranformations such as DebounceTime or DistinctUntilChanged
* Can easily add input elements dynamically
* Easier Unit Testing

### Form States(Input Element and Form)

* Value
  * pristine: Unchanged
  * dirty: Changed
  * If all Input elements on a Form are Pristine, then the Form State is Pristine
  * If any Input element on a Form is Dirty, then the Form State is Dirty
* Validity
  * valid: If it passes all the defined Validation Rules
    * The Form itself is valid if all Input elements on the form are valid
  * errors: Array containing Validation errors
    * Key of each Array element is the name of the Validation rule associated with the Error
* Visited
  * touched: Visited an input element
    * User has set focus into the Input and then left the Input element
    * A Form is touched if any input element has been touched
  * untouched

### Form Building Blocks

* FormControl: Tracks the value and state of an individual Input element(such as input box)
* FormGroup: Tracks the value and state of group of FormControls(such as for the form itself(*Root FormGroup*), group of input elements for a mailing address block etc)
* The above 2 are actually Classes provided when we work with Angular Forms
  * Instances of these classes define the Form Model
* Form Model: Data Structure that represents the HTML Form
  * Retains Form State like dirty, touched, valid, disabled etc
  * Retains Form Value in the value property
  * Tracks all of the FormControls
* Form Model is same for Template Driven and Reactive Forms but the way they are created is different

### Template-Driven Forms

* In Template
  * HTML in template for the Form element, each Input element, Data binding, Validation Rules using Attributes and Validation Error messages
  * Angular automatically generates the associated Form Model
* Component Class
  * Define Properties for data binding(data model)
  * Methods for form operations such as Submit

### Reactive Forms

* Shift the responsiblity for creating the Form Model to the Component class
* Template
  * Form element and Input element(s)
  * Binding to Form Model
* Component Class
  * Define Form Model
  * Validation rules and error messages
  * Properties for managing data(data model)
  * Methods for form operations such as submit

### Form Directives and imports

* Template-driven(FormsModule)
  * ngForm: Automatically assigned by Angular when it detects a form
    * Angular creates a Form Model starting with the Root FormGroup instance and automatically binds it to the form
    * If we want to access form model, export ngForm directive into a template reference variable(#signUpForm="ngForm")
  * ngModel
    * Use this directive on each Input element to keep the Component class property in sync with the user-entered value
    * [(ngModel)]="customer.firstName"
    * 2 way data binding and name for keeping track of control
    * When ngModel is added to an input element within a form, Angular automatically creates a FormControl instance and adds it to the form model using the input element's name as the key
    * Access state by exporting ngModel directive into a template reference variable(#firstNameVar="ngModel")
  * ngModelGroup
* Reactive(ReactiveFormsModule)
  * formGroup
  * formControl
  * formControlName
  * formGroupName
  * formArrayName