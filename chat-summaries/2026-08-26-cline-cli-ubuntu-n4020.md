# Chat Summary — Cline CLI on Ubuntu / Intel Celeron N4020

**Conversation date:** 2026-08-06 (continued/reference added 2026-08-26)

## Goal
Run **Cline CLI** directly on the user's Ubuntu machine and eventually use it as an AI coding/agent CLI.

## Machine / environment
- Ubuntu terminal user: `otgpc`
- CPU: **Intel Celeron N4020 @ 1.10GHz**
- Architecture: `x86_64`
- Node.js: **v22.22.1**
- npm: **9.2.0**
- CPU flags include SSE/SSE2/SSSE3/SSE4.1/SSE4.2, AES, SHA-NI, etc.
- CPU flags do **not** include `avx` or `avx2`.

## Installation sequence
Initially:
```text
cline: command not found
```

Attempted:
```bash
npm install -g cline
```
This failed because the normal user could not write to `/usr/local/lib/node_modules`:
```text
EACCES: permission denied, mkdir '/usr/local/lib/node_modules'
```

Then installed successfully with:
```bash
sudo npm install -g cline
```
Installation result:
```text
added 324 packages in 39s
```

Installed Cline version:
```text
cline@3.0.51
```

Executable resolution:
```text
/usr/local/bin/cline
```
which is a symlink to:
```text
../lib/node_modules/cline/bin/cline
```

## Failure
Running:
```bash
cline --version
```
produced:
```text
Illegal instruction (core dumped)
```

Bypassing the launcher also crashed:
```bash
node /usr/local/lib/node_modules/cline/bin/cline --version
```
Result:
```text
Illegal instruction (core dumped)
```

`NODE_OPTIONS="--trace-uncaught"` did not change the result.

Node itself works normally:
```bash
node -e "console.log('Node works:', process.version)"
```
Output:
```text
Node works: v22.22.1
```

And:
```bash
node -e "console.log(process.arch, process.platform)"
```
Output:
```text
x64 linux
```

## Native Cline component identified
`npm ls --depth=0` showed:
```text
@cline/cli-linux-x64@3.0.51
```

The package contains the native executable:
```text
node_modules/@cline/cli-linux-x64/bin/cline
```

`file` identified it as:
```text
ELF 64-bit LSB executable, x86-64, dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2
```

Running the native executable directly:
```bash
./node_modules/@cline/cli-linux-x64/bin/cline --version
```
also produced:
```text
Illegal instruction (core dumped)
```

This establishes that the crash is in the native Linux x64 Cline component rather than the Node executable itself.

## Cleanup
Cline was subsequently removed with:
```bash
sudo npm uninstall -g cline
```
Result:
```text
removed 324 packages in 3s
```

After removal:
```text
cline: command not found
```

## Important diagnostic conclusion
Do **not** treat this as an npm permissions problem or a broken Node installation. Node v22.22.1 runs correctly. The installed Cline 3.0.51 package's native `@cline/cli-linux-x64` executable crashes with `Illegal instruction` on the Celeron N4020. The N4020 does not advertise AVX/AVX2. CPU-instruction incompatibility is a strong suspect, but should not be stated as mathematically proven without identifying the exact instruction or testing a compatible Cline build.

## Next intended task
The user's explicit requirement is: **run Cline CLI**, not replace it with another coding agent. The next investigation should therefore focus on finding a Cline CLI release/build whose Linux x64 native component works on the Intel Celeron N4020, rather than switching to another agent.

Avoid repeatedly reinstalling Cline 3.0.51 because it reproduces the same native-binary crash.
