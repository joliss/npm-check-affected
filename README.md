# npm-check-affected

Check that none of the installed Node packages, as listed by `npm ls`, match a
given version spec of known-bad packages.

This is a typically used to verify that an application is unaffected by some
vulnerability or other issue.

## Installation

```
npm install -g npm-check-affected
```

## Usage

```bash
cd project-dir
npm install

# Supply JSON version spec of affected versions
npm-check-affected '{ "express": "< 3.0.4", "connect": "< 2.0.0" }'

# Or, supply JSON file
npm-check-affected affected-versions.json

# Or, supply HTTP URL
npm-check-affected http://.../affected-versions.json
```

This will check the installed packages as reported by `npm ls`, and report
whether any of them are affected.

## Exit Code

`npm-check-affected` will return with zero exit code if no affected packages
were found. It will return non-zero if at least one affected package was
found, or if some error occurred while looking for installed packages.
