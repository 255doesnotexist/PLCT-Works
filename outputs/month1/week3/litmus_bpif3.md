```bash
root@k1:~# opam init; opam install herdtools7
[WARNING] Running as root is not recommended
No configuration file found, using built-in defaults.
Checking for available remotes: rsync and local, git, darcs.
  - you won't be able to use mercurial repositories unless you install the hg command on your system.


<><> Fetching repository information ><><><><><><><><><><><><><><><><><><><><><>
Processing  1/1: [default: http]
[default] Initialised
default (at https://opam.ocaml.org): 
    [WARNING] opam is out-of-date. Please consider updating it (https://opam.ocaml.org/doc/Install.html)


<><> Required setup - please read <><><><><><><><><><><><><><><><><><><><><><><>

  In normal operation, opam only alters files within ~/.opam.

  However, to best integrate with your system, some environment variables
  should be set. If you allow it to, this initialisation step will update
  your bash configuration by adding the following line to ~/.profile:

    test -r /root/.opam/opam-init/init.sh && . /root/.opam/opam-init/init.sh > /dev/null 2> /dev/null || true

  Otherwise, every time you want to access your opam installation, you will
  need to run:

    eval $(opam env)

  You can always re-run this setup with 'opam init' later.

Do you want opam to modify ~/.profile? [N/y/f]
(default is 'no', use 'f' to choose a different file) 
<><> Creating initial switch 'default' (invariant ["ocaml" {>= "4.05.0"}] - initially with ocaml-system) 

<><> Installing new switch packages <><><><><><><><><><><><><><><><><><><><><><>
Switch invariant: ["ocaml" {>= "4.05.0"}]

<><> Processing actions <><><><><><><><><><><><><><><><><><><><><><><><><><><><>
∗ installed base-bigarray.base
∗ installed base-threads.base
∗ installed base-unix.base
∗ installed host-arch-riscv64.1
∗ installed host-system-other.1
⬇ retrieved ocaml-system.4.13.1  (https://opam.ocaml.org/cache)
∗ installed ocaml-system.4.13.1
⬇ retrieved ocaml-config.2  (2 extra sources)
∗ installed ocaml-config.2
∗ installed ocaml.4.13.1
Done.
# Run eval $(opam env --switch=default) to update the current shell environment
[WARNING] Running as root is not recommended
The following actions will be performed:
  ∗ install conf-which      1        [required by herdtools7]
  ∗ install conf-gmp        4        [required by zarith]
  ∗ install conf-pkg-config 3        [required by zarith]
  ∗ install dune            3.16.0   [required by herdtools7]
  ∗ install ocamlfind       1.9.6    [required by zarith]
  ∗ install menhirSdk       20240715 [required by menhir]
  ∗ install menhirLib       20240715 [required by menhir]
  ∗ install menhirCST       20240715 [required by menhir]
  ∗ install zarith          1.14     [required by herdtools7]
  ∗ install menhir          20240715 [required by herdtools7]
  ∗ install herdtools7      7.57
===== ∗ 11 =====
Do you want to continue? [Y/n] y

<><> Processing actions <><><><><><><><><><><><><><><><><><><><><><><><><><><><>
⬇ retrieved conf-gmp.4  (https://opam.ocaml.org/cache)
∗ installed conf-pkg-config.3
∗ installed conf-which.1
∗ installed conf-gmp.4
⬇ retrieved herdtools7.7.57  (https://opam.ocaml.org/cache)
⬇ retrieved menhir.20240715  (https://opam.ocaml.org/cache)
⬇ retrieved menhirLib.20240715  (cached)
⬇ retrieved menhirSdk.20240715  (cached)
⬇ retrieved dune.3.16.0  (https://opam.ocaml.org/cache)
⬇ retrieved zarith.1.14  (https://opam.ocaml.org/cache)
⬇ retrieved menhirCST.20240715  (https://opam.ocaml.org/cache)
⬇ retrieved ocamlfind.1.9.6  (https://opam.ocaml.org/cache)
∗ installed ocamlfind.1.9.6
∗ installed zarith.1.14
∗ installed dune.3.16.0
∗ installed menhirCST.20240715
∗ installed menhirSdk.20240715
∗ installed menhirLib.20240715
∗ installed menhir.20240715
Processing 32/33: [herdtools7: make build]已杀死
root@k1:~# 
```

- 编译 OOM 惹
- UPD: 其实任务是复现那个 issue
- UPD2: 没来得及复现已经修复了