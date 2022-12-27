# setup-dune-action
Github action to set-up dune

This action will install ocaml, opam, dune as well as any additional Opam packages specified.

The action will cache opam packages to speed up builds.

You can use this action as follows:
```yml
- name: Setup dune
  uses: nmittu/setup-dune@v1
  with:
    packages: js_of_ocaml ppx_jane js_of_ocaml-ppx incr_dom ojs
    compiler: 4.12.0
- name: build
  run: |
    eval $(opam config env)
    dune build bin/main.bc.js --profile="release"
```

After installing dune with the action, you bust run `eval $(opam config env)` before running any dune commands. Alternativly, you steps may source from `~/.bash-profile`
