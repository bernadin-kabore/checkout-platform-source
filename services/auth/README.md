# auth

Issues and validates session tokens for the checkout flow

A Go service inside this application's source repository. It builds its own
container image and deploys independently of its siblings — see the repository
root `README.md` for how the application fits together, and the GitOps
repository for how this service is actually running.

It requires **Go 1.26 or newer**, declared in `go.mod` and pinned in the
Dockerfile builder stage. The Go standard library is compiled into the
binary, so the toolchain that builds this image determines the stdlib
advisories reported against it -- the builder tag is a security decision,
not a build-tooling one.

## Working on it

```bash
go test ./...
go run .
```

CI runs `go vet`, `go test` and golangci-lint for this directory whenever a
commit touches it, plus CodeQL, gosec, govulncheck, a Trivy filesystem scan,
and a 70% line coverage gate.
