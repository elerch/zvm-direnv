zvm-direnv
==========

A way to use [zvm](https://zvm.app) with [direnv](https://direnv.net)

Installing
----------

Put the following lines in your `.envrc`:

```sh
if ! has zvm_direnv_version || ! zvm_direnv_version 1.0.0; then
  source_url "https://git.lerch.org/lobo/zvm-direnv/1.0.0/direnvrc" #"sha256-RuwIS+QKFj/T9M2TFXScjBsLR6V3A17YVoEW/Q6AZ1w="
fi
```

Usage
-----

```sh
$ echo "use zig 0.13.0" >> .envrc
$ direnv allow
```

If you haven't used direnv before, make sure to [hook it into your shell](https://direnv.net/docs/hook.html) first.

How it works
------------

This implementation utilizes zvm for installation of both [zig](https://ziglang.org)
and [zls](https://github.com/zigtools/zls). It avoids the use of `zvm use` as
this will change the zig version system-wide, possibly resulting in some
confusing behavior. Instead, it uses zvm to download the appropriate versions
if necessary, then prepends the desired version to the path used in the direnv
directory.
