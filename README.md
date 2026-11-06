# SDLC platform governance

The Vrixel platform constitution. Every product inherits it; product constitutions may tighten it, never loosen it.
Changes are pull requests approved by the platform owner (see CODEOWNERS).

## Files

- `platform/constitution.md`: the platform constitution.
- `platform/alert-rules.yaml`: the OpenChoreo alert rules every backend component gets (exceptions
  logged, memory near its limit). The SDLC tool adds them before a component's first deployment;
  firing rules reach the tool as signals.
- `platform/aws-resources.yaml`: the AWS services products may use (VX-19), what each is for, the
  data classes and regions allowed, the IAM actions behind each access, sizes with planning costs,
  and the emulator for tests. Each type has a Crossplane Composition in
  `vrixel-tools/platform-resources`; adding one is a pull request in both.
