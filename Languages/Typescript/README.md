# Typescript notes

## Unit testing

I found an article that looked like what I was looking for, but I didn't end
up going far enough on the project to vet this:

[Unit testing node applications with TypeScript — using mocha and chai](https://journal.artfuldev.com/unit-testing-node-applications-with-typescript-using-mocha-and-chai-384ef05f32b2)

Here's the gist of the article:


### Install

    $ npm install chai mocha ts-node @types/chai @types/mocha --save-dev

### Code

    export const hello = () => 'Hello world!';


### Write tests

    import { hello } from './hello-world';
    import { expect } from 'chai';
    import 'mocha';

    describe('Hello function', () => {

      it('should return hello world', () => {
        const result = hello();
        expect(result).to.equal('Hello world!');
      });

    });

### Run tests

In `package.json` add:

    {
      "scripts": {
        "test": "mocha -r ts-node/register src/**/*.spec.ts",
      },
    }

and run `npm test`

much of the rest of the article is about dealing with `webpack` and typescript.


## Tools

- Formatting: [typescript-formatter](https://github.com/vvakame/typescript-formatter)
- Linter: [tslint](https://github.com/palantir/tslint)
