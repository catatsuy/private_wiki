#Perl
##インストール

    curl -L http://xrl.us/perlbrewinstall | bash
    source ~/perl5/perlbrew/etc/bashrc
    perlbrew install perl-5.***
    perlbrew install-cpanm
    
    cpanm --installdeps .


##デバッグ

    use Data::Dumper;
    warn Dumper($value);

