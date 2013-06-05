#Perl

## Perlbrew

    curl -L http://xrl.us/perlbrewinstall | bash
    source ~/perl5/perlbrew/etc/bashrc
    perlbrew install perl-5.***
    perlbrew install-cpanm
    
    cpanm --installdeps .

今は plenv の方がおすすめ


## デバッグ

    use Data::Dumper;
    warn Dumper($value);

