# Use PNPM instead of NPM

PNPM is just another package manager for Node.JS. It is a package manager that is based on [Yarn](https://yarnpkg.com/), but much faster and more efficient.

## Problem with Yarn or NPM

Yearn is just small improvements over the prebuilt NPM with a hot cache and a few other features. But both yarn and npm have to download the whole package index from the internet every time you run a command. It creates a redundant and huge amount of data.

If you deal with large repositories and have several packages, all the node_modules eat up your disk space.

## How it tackles the problem

The name PNPM is abbreviated from the word Performant-Node-Package-Manager. The function promptly fits the name.

Whenever you install a package, it is downloaded from the internet. It is kept in global storage. Now, if you use the same package again in _another project_, it is not downloaded again. Rather, it creates a symlink to the global storage.

This hugely improves the speed as well as the storage usage. It reduces the size of the folder.

Moreover, if you deal with monorepo workspace, it is possibly the best choice.

## Advantages

- **Security**: Like Yarn, pnpm has a special file with all the installed packages’ checksums to verify the integrity of every installed package before its code is executed.
- **Offline Mode**: pnpm saves all the downloaded package tarballs in a local registry mirror. It never makes requests when a package is available locally. With the --offline parameter, HTTP requests can be prohibited at all.
- **Fast**: pnpm is not only faster than npm, but it is also faster than Yarn. It is faster than Yarn both with cold and hot cache. Yarn copies files from cache whereas pnpm just links them from the global store.
- **Supports monorepos**: npm was only designed to manage individual projects. As of now, it doesn’t have any functionality to support monorepos. pnpm has built-in support for multiple packages in a repository.
- **Space Efficient**: pnpm doesn't need to download the same file repeatedly and make a clutter. It just links the file from the global store.
- **Ease of Use**: all the commands of the pnpm are the same as npm. So you do not need to learn anything new.

---

In conclusion, pnpm is always a better choice than any other package manager. The most lucrative feature of pnpm is its ability to manage multiple packages in a repository and space management.
