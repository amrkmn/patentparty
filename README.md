# patentparty

### copyparty with patent-restricted features added back in

patentparty is a drop-in replacement for the official Docker image of [copyparty](https://github.com/9001/copyparty).  
It adds back in H265/HEVC, HEIF and non-LC AAC support.  
These features were [removed](https://github.com/9001/copyparty/commit/1bec91d11ca2f35313053c2a8d9bc6415ed38128) from copyparty due to [wanting to avoid patent issues](https://github.com/9001/copyparty/blob/hovudstraum/docs/bad-codecs.md).

All credits for the copyparty application go to the original author, [ed, "9001"](https://github.com/9001).

This repository was taken from and/or inspired by [0x464e/patentparty](https://github.com/0x464e/patentparty).

# Docker Images

This repo only builds docker images, since that is the only real affected platform.  
The docker images are published to [Quay.io](https://quay.io/repository/amrkmn/patentparty).  
patentparty supports the same CPU architectures as the corresponding official copyparty images.

The GitHub Actions build runs on a schedule and can also be triggered manually.

Images are published per variant under `quay.io/amrkmn/patentparty/<variant>`.

# GitHub Actions

The workflow in [`.github/workflows/build.yml`](.github/workflows/build.yml) checks the latest copyparty release, builds all supported variants when a new version is available, pushes the images to Quay.io, and records the built version in [`.github/upstream.txt`](.github/upstream.txt).

Configure these repository secrets before running it:

- `QUAY_USERNAME`
- `QUAY_PASSWORD`

A manual run can set `version_override` to build a specific copyparty tag.

### ac

- `quay.io/amrkmn/patentparty/ac:1.20.10` - version tagged
- `quay.io/amrkmn/patentparty/ac:latest` - latest ac version

### iv

- `quay.io/amrkmn/patentparty/iv:1.20.10` - version tagged
- `quay.io/amrkmn/patentparty/iv:latest` - latest iv version

### dj

- `quay.io/amrkmn/patentparty/dj:1.20.10` - version tagged
- `quay.io/amrkmn/patentparty/dj:latest` - latest dj version

# Compatibility

patentparty is used exactly like the official copyparty Docker images.  
Any and every config option, feature, etc. works exactly the same as with the official image.  
Refer to the official copyparty documentation for usage.

# Building

If you want to build the images yourself instead of using the images pushed by GitHub Actions,
you can clone this repo or download the Dockerfile and then build the variant (ac, iv or dj) of your choice by running:

```sh
docker build -t patentparty-dj --build-arg VARIANT=dj .
```

If you want to build a version other than the latest, add the build arg:

```sh
docker build -t patentparty-dj --build-arg VARIANT=dj --build-arg IMAGE_TAG=1.20.10 .
```

# License

This repository is licensed under the MIT License. See [LICENSE](LICENSE).
