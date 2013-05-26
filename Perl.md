#Perl

## plenv

    git clone git://github.com/tokuhirom/plenv.git ~/.plenv
    exec $SHELL -l
    plenv available
    plenv install 5.*.*
    plenv install-cpanm


## Perlbrew

    curl -L http://xrl.us/perlbrewinstall | bash
    source ~/perl5/perlbrew/etc/bashrc
    perlbrew install perl-5.***
    perlbrew install-cpanm
    
    cpanm --installdeps .


## デバッグ

    use Data::Dumper;
    warn Dumper($value);

