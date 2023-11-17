# helm-diff-comment

Post a comment message with a Helm output on a pull request associated with running
the corresponding Helm action.

## Example

```yaml
steps:
  - uses: helmfile/helmfile-action@v1.5.0
    id: helmfile-apply
    with:
      helmfile-args: apply --environment production
  - uses: kamu-data/helm-diff-comment@v1.3.2
    with:
      helm-output: ${{ steps.helmfile-apply.outputs.helmfile-stdout }}
      environment-name: production
      helm-action: apply
```

## Inputs

The following inputs are supported

* **environment-name** &mdash; The name of the environment Helm action was running on.
* **helm-action** &mdash; The name of the action that produced the output.
* **helm-output** &mdash; The output of the helm action. It will be posted in the diff section of the comment.

## Outputs

This action has no outputs.
