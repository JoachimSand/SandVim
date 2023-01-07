## Personal Neovim Configuration

This is a pure Lua-based neovim configuration based heavily off https://github.com/LunarVim/Neovim-from-scratch


### FSharp Setup
FSharp LSP support on Linux is brittle at best. However, it can work with some effort. 

1. Clone https://github.com/fsprojects/fsharp-language-server.
2. Go to the `src/FSharpLanguageServer/` directory.
3. Build with `dotnet build FSharpLanguageServer.fsproj -c Release`. `dotnet tool restore` may need to be run first.
4. Overwrite the cmd path in `lua/user/lsp/mason.lua`. For example:

```
lspconfig["fsharp_language_server"].setup{
    cmd = {"dotnet", "/home/joachimls/fsharp-language-server-0.1.60/src/FSharpLanguageServer/bin/Release/net6.0/FSharpLanguageServer.dll"},
    on_attach = require("user.lsp.handlers").on_attach,
    capabilities = require("user.lsp.handlers").capabilities,
    settings = {}
}
```

### TODO
Install Treesitter.
Autopair closing.
Gitsigns.
Better buffer/tab/windows.
