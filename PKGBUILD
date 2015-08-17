pkgname=vim-cisco
pkgver=20130930
pkgver(){
  date +%Y%m%d
}
pkgrel=1
pkgdesc="Vim syntax highlighting for Cisco configuration files, Cisco ASA firewall, Cisco ACL"
arch=("any")
url="http://www.vim.org/"
license=("custom")
depends=("vim"
         "git"
        )
options=("emptydirs")
source=("cisco.vim::git://github.com/vim-scripts/cisco.vim.git"
        "ciscoacl.vim::git://github.com/vim-scripts/ciscoacl.vim.git"
        "ciscoasa.vim::git://github.com/vim-scripts/ciscoasa.vim.git"
       )
md5sums=("SKIP"
         "SKIP"
         "SKIP"
        )
prepare(){
cat << EOL > "$srcdir/ftdetect-ciscoacl.vim"
augroup filetype 
  au! BufRead,BufNewFile *.acl   set filetype=ciscoacl
augroup END
EOL
}
package() {
  sed -i "s/let b:current_syntax = \"cisco\"/let b:current_syntax = \"ciscoacl\"/g" "$srcdir/ciscoacl.vim/syntax/ciscoacl.vim"
  install -Dm644 "$srcdir/cisco.vim/syntax/cisco.vim"       "$pkgdir/usr/share/vim/vimfiles/syntax/cisco.vim"
  install -Dm644 "$srcdir/ciscoacl.vim/syntax/ciscoacl.vim" "$pkgdir/usr/share/vim/vimfiles/syntax/ciscoacl.vim"
  install -Dm644 "$srcdir/ciscoasa.vim/syntax/ciscoasa.vim" "$pkgdir/usr/share/vim/vimfiles/syntax/ciscoasa.vim"
  install -Dm644 "$srcdir/ftdetect-ciscoacl.vim"            "$pkgdir/usr/share/vim/vimfiles/ftdetect/ciscoacl.vim"
} 
