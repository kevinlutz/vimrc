# vimrc

vi .config/nvim/init.vim

" Map escape to jj
imap jj <Esc>

" Syntax highlighting
syntax on

" Set FZF Default to Ripgrep (must install ripgrep)
let $FZF_DEFAULT_COMMAND = 'rg --files --hidden --follow --no-ignore-vcs'

" Options viewable by using :options
" Set options viewable by using :set all
" Or help for individual configs can be accessed :help <name>
set nocompatible
set redrawtime=10000
set background=dark
set laststatus=2
set noerrorbells
set tabstop=2 softtabstop=2
set shiftwidth=2
set expandtab
set smartindent
set nu
set nowrap
set nobackup
set undodir=~/.vim/undordir
set undofile
set incsearch
" set relativenumber
set cursorline

" Column set to column 100
set colorcolumn=100

" Column color set to grey
highlight ColorColumn ctermbg=1

" Plugins are managed with "vim plug" google that to see how to use
call plug#begin('~/.vim/plugged')

" Make your Vim/Neovim as smart as VSCode
" Plug 'neoclide/coc.nvim', {'branch': 'release'}

" Formatter
Plug 'prettier/vim-prettier', { 'do': 'yarn install' }

" Comment and uncomment lines
Plug 'preservim/nerdcommenter'

" A light and configurable statusline/tabline plugin for Vim
Plug 'itchyny/lightline.vim'

" Directory tree
Plug 'scrooloose/nerdtree'

" Visualize undo history tree (in vim undo is not linear)
Plug 'mbbill/undotree'

" Syntax highlighting for languages
Plug 'sheerun/vim-polyglot'

" Fzf is a general-purpose command-line fuzzy finder
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'

" This plugin adds Go language support for Vim, with many features
" Plug 'fatih/vim-go', { 'do': ':GoUpdateBinaries' }

" for searching across files in project
Plug 'mileszs/ack.vim'

" Python code formatter
" Plug 'ambv/black'

" Gruvbox color theme
" Plug 'morhetz/gruvbox'

" Vim-monokai-tasty color theme
Plug 'patstockwell/vim-monokai-tasty'

call plug#end()

" Set mapleader to space
let mapleader = " "
" Maps
nmap <leader>hk :vsplit ~/.vim/hotkeys<cr>
"nmap <leader>gd <Plug>(coc-definition)
"nmap <leader>gr <Plug>(coc-references)
nmap <leader>n :NERDTreeToggle<cr>
nmap <leader>N :NERDTreeFind<cr>
nmap <leader><leader>p :Prettier<cr>
nmap <leader><leader>g :GoFmt<cr>
nmap <leader><leader>b :Black<cr>
nmap <leader><leader>u :UndotreeToggle<cr>
" Files (runs $FZF_DEFAULT_COMMAND if defined)
nmap <leader><leader>f :Files<cr>
nmap <leader><leader><leader>g :GoMetaLinter<cr>
"
" Control P (below) will fuzzy find across all files that are under version
" control
"
101 nnoremap <C-p> :GFiles<CR>

nnoremap <leader><leader>c :call NERDComment(0,"toggle")<CR>
vnoremap <leader><leader>c :call NERDComment(0,"toggle")<CR>
nnoremap <leader><Tab> :bnext<CR>
nnoremap <leader><Tab><Tab> :bprevious<CR>

"splits
nnoremap <leader>w <C-w>v<C-w>l
nnoremap <leader>h <C-w>s<C-w>j
" navigation across splits made easy
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

"quit files with leader q
nnoremap <leader>q :q<cr>

"ack settings
nnoremap <leader>a :Ack
let g:ackprg = 'rg --vimgrep --no-heading'
