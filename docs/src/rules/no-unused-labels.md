---
title: no-unused-labels
layout: doc
edit_link: https://github.com/eslint/eslint/edit/main/docs/src/rules/no-unused-labels.md
rule_type: suggestion
---

<!--RECOMMENDED-->

<!--FIXABLE-->

Disallows unused labels.

Labels that are declared and not used anywhere in the code are most likely an error due to incomplete refactoring.

```js
OUTER_LOOP:
for (const student of students) {
    if (checkScores(student.scores)) {
        continue;
    }
    doSomething(student);
}
```

In this case, probably removing `OUTER_LOOP:` had been forgotten.
Such labels take up space in the code and can lead to confusion by readers.

## Rule Details

This rule is aimed at eliminating unused labels.

Examples of **incorrect** code for this rule:

```js
/*eslint no-unused-labels: "error"*/

A: var foo = 0;

B: {
    foo();
}

C:
for (let i = 0; i < 10; ++i) {
    foo();
}
```

Examples of **correct** code for this rule:

```js
/*eslint no-unused-labels: "error"*/

A: {
    if (foo()) {
        break A;
    }
    bar();
}

B:
for (let i = 0; i < 10; ++i) {
    if (foo()) {
        break B;
    }
    bar();
}
```

## When Not To Use It

If you don't want to be notified about unused labels, then it's safe to disable this rule.

## Related Rules

* [no-extra-label](./no-extra-label)
* [no-labels](./no-labels)
* [no-label-var](./no-label-var)
