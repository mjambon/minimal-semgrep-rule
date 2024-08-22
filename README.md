# A minimal semgrep rule

Here's a minimal [semgrep rule](https://semgrep.dev/docs/writing-rules/rule-syntax). It's sufficient to produce a test or a bug report. Call it `test.yaml` or `test.yml` or anything with a `.yml` or `.yaml` extension:
```
rules:
- id: test
  pattern: hello
  languages: [python]
  message: found something
  severity: ERROR
```

Here's a matching target file `test.py`:
```
# ruleid: test
hello
```

The special comment containing `ruleid:` is for `semgrep --test`. It tells semgrep that a match is expected on the next line.

Command for running a regular semgrep scan:
```
$ semgrep -c test.yaml test.py
```
Command for running semgrep in test mode:
```
$ semgrep --test -c test.yaml test.py
```
