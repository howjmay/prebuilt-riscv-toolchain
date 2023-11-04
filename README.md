# prebuilt-riscv-toolchain

The release from the official repository [riscv-gnu-toolchain](https://github.com/riscv-collab/riscv-gnu-toolchain) has a lack of several necessary features. Therefore, this repository provides a latest prebuilt RISCV GNU toolchain binary on `x86` architecture for Linux. This can help developers to set up CI (e.g. GitHub Action).

This repository includes the cross compiled toolchains and qemu simulators.

And it is built with `--enable-multilib`, which means both 32bit and 64bit architectures are supported.

## Usage

The developers can simple download the binary and export to the PATH environment variable.

An example from [neon2rvv](https://github.com/howjmay/neon2rvv/blob/main/.github/workflows/github_actions.yml#L18-L21) is shown as following

```bash
# create the folder for binaries
mkdir /opt/riscv
# download the binaries and extract them
wget https://github.com/howjmay/prebuilt-riscv-spike/releases/download/latest/riscv.tar.gz
sudo tar -xzf riscv.tar.gz -C /opt/
# export the path of binaries
export PATH=$PATH:/opt/riscv/bin
```

### File Structure

The file structure is the same as the release of [riscv-gnu-toolchain](https://github.com/riscv-collab/riscv-gnu-toolchain).

```
riscv/
├─ bin/
├─ include/
├─ lib/
├─ libexec/
├─ riscv64-unknown-elf/
├─ share/
```

### Requirement

In addition glibc version should be greater than `GLIBC_2.32`.
In GitHub Action, you can use runner-image `ubuntu-22.04` (in other words using `runs-on: ubuntu-22.04`) to solve the problem.
