# 👌 Handling errors globally

__If we want our program to be secure, resilient, performant, and bug-free, we should have good Node.JS error handling so we need to know what that looks like.__

There are different ways to handle errors in Node.JS by using try/catch. But a standard practice in Express is to handle errors in a centralized object that handles all types of errors and use middlewares for it.

It's important to install the [express-async-errors](https://www.npmjs.com/package/express-async-errors) to add support for async/await in ExpressJS.

So there are 3 steps to follow in order to create a handling errors using TypeScript:

- Create an Error class.
- Create a middleware.
- Return the error in the Routes.

---

## Create an Error class

The first step is to create a class for errors.

```
class AppError {
  public readonly message: string;

  public readonly statusCode: number;

  constructor(message: string, statusCode = 400) {
    this.message = message;
    this.statusCode = statusCode;
  }
}

export default AppError;
```

-- 

## Create a middleware

The second step is to create a Midleware after the routes be called:

```
routes.use(
  (err: Error, request: Request, response: Response, _: NextFunction) => {
    if (err instanceof AppError) {
      return response.status(err.statusCode).json({
        status: 'error',
        message: err.message,
      });
    }

    console.error(err);

    return response.status(500).json({
      status: 'error',
      message: 'Internal server error',
    });
  },
);
```

-- 

## Triggering a trow error

Finally the service/control needs to return a trow error in case of errors using the created class.

```
if (!user) {
  throw new AppError('Incorrect email/password combination.', 401);
}
```
