# Changelog

All notable changes to this project will be documented in this file. See [commit-and-tag-version](https://github.com/absolute-version/commit-and-tag-version) for commit guidelines.

## 1.0.0 (2026-11-08)

### Features

* prepare a k3s node to store Longhorn data ([053aafd](https://github.com/tonylea/ansible-role-longhorn-node/commit/053aafdcfe972fd4b1ba7e6d64c684e427666fe7))

### Bug Fixes

* add only the new Longhorn partition to the kernel's table ([b6c453a](https://github.com/tonylea/ansible-role-longhorn-node/commit/b6c453a881a0828875e0f542dae0194c070785ec))
* decide whether Longhorn's partition exists from the partition table ([57fc7c5](https://github.com/tonylea/ansible-role-longhorn-node/commit/57fc7c5d41b6ea8685769fa3d13aec063cb21a51))
* tell the kernel about partition changes under the same conditions that make them ([f526e7d](https://github.com/tonylea/ansible-role-longhorn-node/commit/f526e7d3371b2e1ef9419c5cc681f0a527416096))

### Documentation

* describe what the role prepares and how it is tested ([4bc8a0c](https://github.com/tonylea/ansible-role-longhorn-node/commit/4bc8a0c80266c46e15f9f619942b5b259dcfb1f4))
