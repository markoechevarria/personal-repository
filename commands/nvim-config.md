## Instalation and initial setup

`sudo pacman -S neovim` : install neovim
`sudo pacman -S xclip wl-clipboard`: clipboard system interaction with neovim
`sudo pamcan -S python python-pip nodejs npm`: preparation for plugins and LSP
`sudo install pynvim`: python integration

Create the configuration directory and the file init.lua

```
mkdir -p ~/.config/nvim/
touch ~/.config/nvim/init.lua
````

## init.lua configuration

```
vim.opt.nu = true               -- show line number
vim.opt.relativenumber = true   -- show relatives line number
vim.opt.tabstop = 4             -- tab width
vim.opt.shiftwidth = 4          -- width for automatic identation
vim.opt.expandtab = true        -- spaces instead tabs
vim.opt.autoident = true        -- automatic identation
vim.opt.smartident = true       -- intelligent identation
vim.opt.wrap = true             -- line autofit
vim.opt.hlsearch = true         -- highlights search match
vim.opt.incsearch = true        -- incremental search
vim.opt.termguicolors = true    -- enable true colors for themes
vim.opt.undofile = true         -- save undo history
vim.opt.updatetime = 300        -- reduce time for swaps
vim.opt.signcolumn = "yes"      -- show color signs
vim.opt.scrolloff = 8           -- remain cursor 8 lines before screen border
vim.opt.cursorline = true       -- highlights current line
vim.opt.conceallevel = 0        -- show hiden characters
vim.opt.swapfile = false        -- disable swap files

vim.g.mapleader = " "           -- set the leader tab to space

vim.keymap.set({'v', 'x'}, 'J', ":m '>+1<CR>gv=gv") -- set visual mode 1
vim.keymap.set({'v', 'x'}, 'K', ":m '<-2<CR>gv=gv") -- set visual mode 2

vim.keymap.set('n', 'n', 'nzzzv') -- remain cursor at the center to search
vim.keymap.set('n', 'N', 'Nzzzv') -- remian cursos at the center to search

vim.keymap.set('n', '<leader>e', ':NvimTreeToggle<CR>', {desc = 'Toggle file explorer'}) -- open explorer file with "leader" + "e"

vim.keymap.set('n', '<leader>q', ':bd<CR>', {desc = 'Close current buffer'}) -- close buffer with "leader" + "q"
```
## Plugins manage with lazy.nvim

1. Install lazy.nvim
git clone --filter=blob:none https://github.com/folke/lazy.nvim.git --branch=stable ~/.local/share/nvim/lazy/lazy.nvim

2. Set up init.lua (~/.config/nvim/init.lua)

```
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
    vim.fn.system({"git", "clone", "--filter=blob:none", "https://github.com/folke/lazy.nvim.git", "--branch=stable", lazypath})
end 
vim.opt.rtp:preprend(lazypath)

--plugins definition
require("lazy").setup({
    here are the plugins
})
```

## Manage files with NvimTree

```
leader + e  -- open nvimtree
Usa las teclas j (abajo) y k (arriba) para moverte entre archivos y directorios.

Presiona Enter para abrir un archivo o para expandir/colapsar un directorio.

Presiona - (guion) para subir un nivel en el directorio (ir al directorio padre).

Presiona i para alternar la visibilidad de los archivos ocultos (dotfiles).

Presiona R para recargar el árbol (útil si hiciste cambios fuera de Neovim).

Presiona a para crear un nuevo archivo o directorio (te pedirá un nombre).

Presiona d para eliminar (delete) un archivo o directorio.

Presiona r para renombrar (rename) un archivo o directorio.

Presiona x para cortar (cut) un archivo o directorio.

Presiona c para copiar (copy) un archivo o directorio.

Presiona p para pegar (paste) el archivo o directorio cortado/copiado.

Cambiar el foco entre NvimTree y el editor:

Usa Ctrl + h para moverte a la ventana de la izquierda (si es NvimTree).

Usa Ctrl + l para moverte a la ventana de la derecha (si es tu archivo de edición).

Estos son mapeos básicos de Vim para moverse entre ventanas (Ctrl + w + h/l/j/k).
```
## Gestión de Buffers (Archivos Abiertos)
```
En Neovim, cada archivo que abres reside en un "buffer". Puedes tener muchos buffers abiertos y cambiar entre ellos sin cerrar Neovim.

Ver Buffers Abiertos:

:ls - Lista todos los buffers abiertos con sus números.

:buffers - Es un alias de :ls.

Navegar entre Buffers:

:b + [número] - Ir directamente a un buffer por su número (ej: :b 3).

:bnext o :bn - Ir al siguiente buffer en la lista.

:bprevious o :bp - Ir al buffer anterior en la lista.

:bfirst - Ir al primer buffer.

:blast - Ir al último buffer.

Cerrar Buffers:

:bd - Cierra el buffer actual. Si es el único buffer en una ventana, también cerrará la ventana.

:bd! - Cierra el buffer actual sin guardar los cambios (¡cuidado!).

leader + q: Ya tienes un mapeo en tu init.lua para bd: vim.keymap.set('n', '<leader>q', ':bd<CR>', {desc = 'Close current buffer'}). ¡Úsalo!

Mantener un buffer pero cerrar la ventana:

:q - Cierra la ventana actual. Si el buffer no tiene otras ventanas abiertas que lo muestren, el buffer se mantendrá en memoria pero no será visible.
```
## Windows and Splits
```
Neovim te permite dividir tu pantalla en múltiples ventanas (splits) para ver varios archivos a la vez, o diferentes partes del mismo archivo.

Crear Splits:

:sp - Crear un split horizontal (divide la ventana actual en dos horizontalmente, mostrando el mismo buffer).

:vsp - Crear un split vertical (divide la ventana actual en dos verticalmente, mostrando el mismo buffer).

:sp [filename] - Abrir filename en un split horizontal.

:vsp [filename] - Abrir filename en un split vertical.

Navegar entre Splits:

Ctrl + w + h: Mover a la ventana de la izquierda.

Ctrl + w + l: Mover a la ventana de la derecha.

Ctrl + w + j: Mover a la ventana de abajo.

Ctrl + w + k: Mover a la ventana de arriba.

Ctrl + w + w: Ciclar entre todas las ventanas.

Redimensionar Splits:

Ctrl + w + >: Aumentar ancho (derecha).

Ctrl + w + <: Disminuir ancho (izquierda).

Ctrl + w + +: Aumentar alto (abajo).

Ctrl + w + -: Disminuir alto (arriba).

Ctrl + w + =: Hacer que todas las ventanas tengan el mismo tamaño.

Cerrar Splits:

Ctrl + w + c: Cerrar la ventana actual.

Ctrl + w + o: Cerrar todas las ventanas excepto la actual.
```
## Uso de Telescope:
```
leader + ff: Find Files - Busca archivos en tu proyecto (ignorando .git, node_modules, etc.). Escribe parte del nombre del archivo y Telescope lo encontrará rápidamente.

leader + fg: Live Grep - Busca contenido dentro de los archivos de tu proyecto. Escribe un texto y Telescope mostrará todas las ocurrencias.

leader + fb: Find Buffers - Lista todos tus buffers abiertos. Muy útil para cambiar rápidamente entre archivos ya abiertos.

leader + fo: Find Oldfiles - Muestra una lista de archivos visitados recientemente.

Dentro de Telescope (cuando una ventana de Telescope está abierta):

Usa las teclas de dirección (j, k, Ctrl + n, Ctrl + p) para moverte por los resultados.

Presiona Enter para abrir el archivo seleccionado.

Presiona Ctrl + v para abrir el archivo en un split vertical.

Presiona Ctrl + x para abrir el archivo en un split horizontal.

Presiona Ctrl + t para abrir el archivo en una nueva pestaña (tab).

Presiona Escape para cerrar la ventana de Telescope.
```
## Tabs
```
Las pestañas en Neovim son como "espacios de trabajo" o "diseños de ventanas" completos. Cada pestaña puede tener su propio conjunto de splits y buffers abiertos.

Crear una nueva pestaña:

:tabnew - Abre una nueva pestaña vacía.

:tabnew [filename] - Abre filename en una nueva pestaña.

gt: Ir a la siguiente pestaña.

gT: Ir a la pestaña anterior.

:tabn (next) o gt

:tabp (previous) o gT

:tabfirst o g0

:tablast o g$

:tabclose - Cierra la pestaña actual.

:tabonly - Cierra todas las pestañas excepto la actual.
```
