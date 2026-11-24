# SDLC platform governance

The Valxel platform constitution. Every product inherits it; product constitutions may tighten it, never loosen it.
Changes are pull requests approved by the platform owner (see CODEOWNERS).

## Files

- `platform/constitution.md`: the platform constitution.
- `platform/alert-rules.yaml`: the OpenChoreo alert rules every backend component gets (exceptions
  logged, memory near its limit). The SDLC tool adds them before a component's first deployment;
  firing rules reach the tool as signals.
- `platform/error-tracking.yaml`: where error reports may go: self-hosted GlitchTip for payments
  and for data in India, Sentry's SaaS (with a BAA for PHI) otherwise. Products choose in
  product.yaml `runtime.error_tracking`; the SDLC tool refuses a choice these rules don't allow.
- `platform/remediation.yaml`: what the SDLC tool may do in production by itself to end an
  incident (turn off a recent feature's flag, roll back a recent release), only when OpenChoreo's
  root-cause analysis agrees, and with which AI provider that analysis may run per data class;
  its track record bar; how long it must then stay quiet and who is paged when; and the gradual
  release plan G6 approves (5%, 25%, 50%, 100%). Products can narrow it or turn parts off in
  product.yaml `runtime.remediation`.
- `platform/catalog.yaml`: the managed services products may use (VX-19), by neutral type
  (key-value-table, queue...) with a block per cloud (AWS, Google Cloud): what each is for, the
  data classes and regions allowed, the access behind each verb, sizes with planning costs, its
  alarms and the emulator for tests. The version 1 AWS names still read as aliases. Each type has a
  Crossplane Composition per cloud in `valxel-platform/platform-resources`; adding one is a pull
  request in both.

## License

MIT, see [LICENSE](LICENSE).
