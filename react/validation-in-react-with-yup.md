# Validation in React with Yup

__[Yup](https://www.npmjs.com/package/yup) is a JavaScript schema builder for value parsing and validation. Define a schema, transform a value to match, validate the shape of an existing value, or both. Yup schema are extremely expressive and allow modeling complex, interdependent validations, or value transformations.__

Yup makes our lives far easier for validating the data our apps consume and manipulate, in an abstract way that does not interfere with the rest of our business logic.

Beside forms, Yup also can be used to validade any object that we need to: data from APIs or an external API library, or any object or array that needs to adhere to a particular schema.

## So how does Yup work exactly?

Let’s use form validation as a use case for our Yup example.

### A Schema Object.
This is the type of data I am expecting from a form, or my schema for a particular object. If my object does not match this schema, it is not valid.

```
import * as Yup from 'yup';

const schema = Yup.object().shape({
  name: Yup.string().required('Name is required'),
  email: Yup.string()
    .required('Email is required')
    .email('Enter a valid email'),
  password: Yup.string().min(6, '6 characters minimum'),
});
```

### Validating Objects with My Schema
Let's imagine the application received an entry (object) called "data" to be validated: 

```
const valid = await schema.validate(data);
```
---

More about [Yup documentation here](https://www.npmjs.com/package/yup).

It's also possible check [more examples in this React project](https://github.com/diogorodrigues/appointment-scheduling-app) that I build.

