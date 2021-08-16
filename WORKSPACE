workspace(name = "skeleton")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_tweag_rules_nixpkgs",
    strip_prefix = "rules_nixpkgs-c40b35f73e5ab1c0096d95abf63027a3b8054061",
    urls = ["https://github.com/tweag/rules_nixpkgs/archive/c40b35f73e5ab1c0096d95abf63027a3b8054061.tar.gz"],
    sha256 = "47fffc870a25d82deedb887c32481a43a12f56b51e5002773046f81fbe3ea9df",
)

http_archive(
  name = "rules_haskell",
  strip_prefix = "rules_haskell-c0e0759dc9c170ec589953194c0efa8fb1f5341d",
  urls = ["https://github.com/tweag/rules_haskell/archive/c0e0759dc9c170ec589953194c0efa8fb1f5341d.tar.gz"],
  sha256 = "3ed7e30e3aefe33e5e1c785d5d10dce2467172d670695b6c55b69052028f240c",
)

load("@io_tweag_rules_nixpkgs//nixpkgs:repositories.bzl", "rules_nixpkgs_dependencies")
rules_nixpkgs_dependencies()

load("@rules_haskell//haskell:repositories.bzl", "rules_haskell_dependencies")
rules_haskell_dependencies()

load("@io_tweag_rules_nixpkgs//nixpkgs:nixpkgs.bzl", "nixpkgs_local_repository", "nixpkgs_python_configure", "nixpkgs_package")
nixpkgs_local_repository(name = "nixpkgs", nix_file = "//:nixpkgs.nix")
nixpkgs_python_configure(repository = "@nixpkgs")

load("@rules_haskell//haskell:nixpkgs.bzl", "haskell_register_ghc_nixpkgs")
haskell_register_ghc_nixpkgs(
  version = "8.10.4",
  attribute_path = "compiler",
  repository = "@nixpkgs",
)

load("@io_tweag_rules_nixpkgs//nixpkgs:nixpkgs.bzl", "nixpkgs_cc_configure")
nixpkgs_cc_configure(repository = "@nixpkgs")

nixpkgs_package(
    name = "hspec-discover",
    attribute_path = "haskellPackages.hspec-discover",
    repository = "@nixpkgs",
)
