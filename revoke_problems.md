I ran the tests for some of the most popular crates reported by `crates.io`.

## Methodology
All crates were tested using `MIRIFLAGS="-Zmiri-strict-provenance -Zmiri-disable-isolation" cargo miri test --all-features`.
If they did not compile, `--all-features` was omitted and only working features were selected.

The commit hash is shown in `()`. When a version is used instead, it was an error occurring in a
dependency that was not explicitly tested.

If a violation was detected, I fixed it and searched for more.

*Line numbers might be off by a couple of lines, if multiple errors occurred at different
points in time when testing.*

## No violations found in
- `syn` *all features* (`11b4a93da60cb75843359099ea3eeb2557181336`)
- `rand-core` *all features* (`f0f15b5ece4dabca62520bac936970a8b3e25d2f`)
- `libc` `["std", "align", "extra_traits", "const-extern-fn"]` (`cd99f681181c310abfba742aef11115d2eff03dc`)
- `cfg-if` `["compiler_builtins"]` (`dc3b5d027580074deb69d7c932a9847365cb7be1`)
- `quote` *all features* (`1fceb4a09d1692515a03059f47ffafa174704ead`)
- `unicode-xid` *all features* (`23c1e7d1dc36ea87f78609591315542cb4b52f5a`)
- `serde` *all features* (`2eed86cd67e2be73113ad138ea5eda77bade20d9`)


## Found simple problems (just need to reorder buffer/slice `len()` calls) in the following crates:
- `rand` `["std", "std_rng", "serde1", "nightly", "getrandom", "small_rng", "min_const_gen"]` (`f0f15b5ece4dabca62520bac936970a8b3e25d2f`):
	- `src/rng.rs:{355, 373}`
- `getrandom` (`0.2.6`):
	- `src/linux_android.rs:20`

## Weird errors
- `proc-macro2` *all features* (`8649302c7ee649c601b93d4a1d6cfc55482f0d9b`) fails the `test_debug_tokenstream` test when running under custom miri *currently not investigated further*
