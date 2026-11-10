# Changelog

All notable changes to this project will be documented in this file. See [commit-and-tag-version](https://github.com/absolute-version/commit-and-tag-version) for commit guidelines.

## [1.1.0](https://github.com/tonylea/ansible-role-longhorn-node/compare/v1.0.2...v1.1.0) (2026-11-10)

### Features

* prepare a node to use Longhorn volumes without storing data ([d890db1](https://github.com/tonylea/ansible-role-longhorn-node/commit/d890db1aedad019b88385c0951f8e3b79fe5ad21))

### Documentation

* add a contributing guide ([f82fbb1](https://github.com/tonylea/ansible-role-longhorn-node/commit/f82fbb1a7b1d00b00023e410895f746933545d5b))
* put each sentence of the README on its own line ([09dadba](https://github.com/tonylea/ansible-role-longhorn-node/commit/09dadbae287d96aae8c3e22c5cf45f77f358ecb7))

## [1.0.2](https://github.com/tonylea/ansible-role-longhorn-node/compare/v1.0.1...v1.0.2) (2026-11-08)

### Bug Fixes

* **ci:** push releases with the repo's deploy key now the token is gone ([09c3164](https://github.com/tonylea/ansible-role-longhorn-node/commit/09c31646505f3d9e418357ca970bc85849c2ec95))

## [1.0.1](https://github.com/tonylea/ansible-role-longhorn-node/compare/v1.0.0...v1.0.1) (2026-11-08)

### Bug Fixes

* create Longhorn's partition right after root, not in the first gap ([c6a268e](https://github.com/tonylea/ansible-role-longhorn-node/commit/c6a268ef16b05f4b1323a776d2fc3141c2b1d397))

## 1.0.0 (2026-11-08)

### Features

* prepare a k3s node to store Longhorn data ([053aafd](https://github.com/tonylea/ansible-role-longhorn-node/commit/053aafdcfe972fd4b1ba7e6d64c684e427666fe7))

### Bug Fixes

* add only the new Longhorn partition to the kernel's table ([b6c453a](https://github.com/tonylea/ansible-role-longhorn-node/commit/b6c453a881a0828875e0f542dae0194c070785ec))
* decide whether Longhorn's partition exists from the partition table ([57fc7c5](https://github.com/tonylea/ansible-role-longhorn-node/commit/57fc7c5d41b6ea8685769fa3d13aec063cb21a51))
* tell the kernel about partition changes under the same conditions that make them ([f526e7d](https://github.com/tonylea/ansible-role-longhorn-node/commit/f526e7d3371b2e1ef9419c5cc681f0a527416096))

### Documentation

* describe what the role prepares and how it is tested ([4bc8a0c](https://github.com/tonylea/ansible-role-longhorn-node/commit/4bc8a0c80266c46e15f9f619942b5b259dcfb1f4))
