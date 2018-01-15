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
  - `tslint.json` from vscode:
    https://github.com/Microsoft/vscode/blob/master/tslint.json
  - [local copy](vscode-tslint.json)


### Editing

## Emacs

Use [TIDE](https://github.com/ananthakumaran/tide)!

I'm pretty sure that I was lazy and didn't want this loaded by default, so I'd
just search for TIDE, and run the following snippet in a `*scratch*` buffer:



    (defun setup-tide-mode ()
      (interactive)
      (tide-setup)
      (flycheck-mode +1)
      (setq flycheck-check-syntax-automatically '(save mode-enabled))
      (eldoc-mode +1)
      (tide-hl-identifier-mode +1)
      ;; company is an optional dependency. You have to
      ;; install it separately via package-install
      ;; `M-x package-install [ret] company`
      (company-mode +1))

    ;; aligns annotation to the right hand side
    (setq company-tooltip-align-annotations t)

    ;; formats the buffer before saving
    (add-hook 'before-save-hook 'tide-format-before-save)

    (add-hook 'typescript-mode-hook #'setup-tide-mode)


I should fix that!


## VSCode

Working through this at the moment: https://github.com/Microsoft/TypeScript-Vue-Starter
