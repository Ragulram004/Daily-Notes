### Day 24: Unit Testing in Node.js

**Writing Unit Tests with Mocha and Chai**

Unit testing ensures that individual parts of your application work as expected. Today, we'll write unit tests for our Express.js application using Mocha and Chai.

**1. Install Mocha and Chai:**

```bash
npm install mocha chai --save-dev
```

**2. Set Up Mocha and Chai:**

Create a test directory and add a test file.

**3. Example Test File:**

```javascript
// test/user.test.js
const chai = require('chai');
const chaiHttp = require('chai-http');
const app = require('../app'); // Your Express app

chai.use(chaiHttp);
const expect = chai.expect;

describe('User API', () => {
  it('should register a new user', (done) => {
    chai.request(app)
      .post('/register')
      .send({ username: 'testuser', password: 'password' })
      .end((err, res) => {
        expect(res).to.have.status(201);
        done();
      });
  });

  it('should not register a user with existing username', (done) => {
    chai.request(app)
      .post('/register')
      .send({ username: 'testuser', password: 'password' })
      .end((err, res) => {
        expect(res).to.have.status(400);
        done();
      });
  });
});
```

**4. Run Tests:**

Add a test script to your package.json and run the tests.

```json
"scripts": {
  "test": "mocha"
}
```

```bash
npm test
```

**Conclusion:**

Today, we wrote unit tests for our Express.js application using Mocha and Chai. Unit tests help ensure the reliability of individual components in your application. Tomorrow, we'll focus on integration testing in

 Node.js.

---
