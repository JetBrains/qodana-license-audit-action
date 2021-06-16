## Qodana License Audit Action for GitHub Actions

[![Qodana EAP version alert](resources/eap-alert.png)](https://www.jetbrains.com/help/qodana/getting-started.html#License)

**Qodana License Audit** helps to avoid problems with incompatible third-party licenses in software projects. The tool is easy to integrate into existing CI pipelines.

**Table of Contents**

<!-- toc -->

- [Usage](#usage)
- [Output Results](#output-results)
- [License Summary](#license-summary)
- [Contact](#contact)

<!-- tocstop -->


## Usage

Input parameters:
* `project-dir` - Project folder to inspect (default `${{ github.workspace }}`)
* `results-dir` - Save results to folder (default `${{ github.workspace }}/qodana`)
* `options` – Image environment options (default – empty)

```yaml
- name: Qodana - License Audit
  uses: JetBrains/qodana-license-audit-action@v2.0-eap
```

All action's inputs are optional.
```yaml
- name: Qodana - License Audit
  uses: JetBrains/qodana-license-audit-action@v2.0-eap
  with:
      project-dir: ${{ github.workspace }}
      results-dir: ${{ github.workspace }}/qodana
      options: PYTHON_VERSION=3.8.10 PHP_VERSION=7.4.16

```

Before you begin, view the list of [Supported Technologies](https://github.com/JetBrains/Qodana/blob/main/General/supported-technologies.md). For the full documentation of the action's inputs, see [action.yaml](action.yaml).

## Output Results

An example of the Qodana License Audit command-line summary output:
```
1/4 Gathering project metadata...
┏━━━━━━━━━━━━━━━━━━━━┳━━━━━━━┓
┃ Dependency Type    ┃ Count ┃
┡━━━━━━━━━━━━━━━━━━━━╇━━━━━━━┩
│ gradle             │  39   │
└────────────────────┴───────┘
2/4 Obtaining licenses for 39 dependencies...
┏━━━━━━━━━━━━━━━━━━━━┳━━━━━━━┓
┃ License Type       ┃ Count ┃
┡━━━━━━━━━━━━━━━━━━━━╇━━━━━━━┩
│ Permissive         │  26   │
│ Unstated License   │   2   │
│ Copyleft           │   2   │
│ Public Domain      │   3   │
│ Copyleft Limited   │   1   │
└────────────────────┴───────┘
3/4 Checking project with licenses (Apache-2.0) and dependencies for problems...
┏━━━━━━━━━━━━━━━━━━━━┳━━━━━━━┓
┃ Problem Type       ┃ Count ┃
┡━━━━━━━━━━━━━━━━━━━━╇━━━━━━━┩
│ Unrecognized       │   3   │
│ dependency license │       │
│ Prohibited         │   2   │
│ dependency license │       │
│ No dependency      │   4   │
│ licenses           │       │
│ Uncategorized      │   4   │
│ dependency license │       │
└────────────────────┴───────┘
✨   Done!
```

Full License Audit results are available in the file `report.json` located in the `results-dir` folder.

## License Summary

By using Qodana, you agree to the [JetBrains EAP user agreement](https://www.jetbrains.com/legal/agreements/user_eap.html) and [JetBrains privacy policy](https://www.jetbrains.com/company/privacy.html).

## Contact

Contact us at [qodana-support@jetbrains.com](mailto:qodana-support@jetbrains.com) or via [our issue tracker](https://youtrack.jetbrains.com/newIssue?project=QD). We are eager to receive your feedback on the existing Qodana functionality and learn what other features you miss in it.
