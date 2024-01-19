# Example Legacy Library for Sublime Text

Legacy libraries (former "dependencies") bundle python packages,
so they can be re-used by Sublime Text packages.

Platform specific variants are organized in sub folders.

| folder                  | description
|-------------------------|-------------------
| `all`                   | no restrictions, universally compatible with all versions of Sublime Text, python and platform
| `st3`                   | requires at least ST3
| `st3_{os}`              | ... and specific os
| `st3_{os}_{arch}`       | ... and specific architecture
| `st4`                   | requires at least ST4
| `st4_{py}`              | ... and specific python version
| `st4_{py}_{os}`         | ... and specific os
| `st4_{py}_{os}_{arch}`  | ... and specific architecture

| variable | valid values
|----------|---------------
| `{os}`   | "osx", "linux", "windows"
| `{arch}` | "x32", "x64", "arm64"
| `{py}`   | "py33", "py38"

Package Control installs most specific and best matching variant of a library.

When running Sublime Text 3,

- `all` and `st3` are actually only synonyms as Sublime Text 2 is no longer supported.
- all folders beginning with `st4` are ignored.

When running Sublime Text 4,

- all folders beginning with `st4` are prefered, if present.
- `st3` is installed for python 3.3 and 3.8
- `st3_{os}` and `st3_{os}_{arch}` are considdered containing binaries and thus are installed for python 3.3, only.

When running ST4 on 64bit Windows, it prefers ...

1. `st4` over `st3`
2. `st4_py38` over `st4`
3. `st4_py38_windows` over `st4_py38`
4. `st4_py38_windows_x64` over `st4_py38_windows`


> [!WARNING]
>
> Package Control downloads the whole repository including all folders
> and drops all but the required variant when installing the library.
>
> This may result in reasonable bandwith being wasted,
> depending on amount of variants and size of packages.
>
> **It is therefore recommended to ship libraries as platform specific
> python wheels using asset based releases, instead.**
