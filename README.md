# NAME

WWW::Myki - A simple Perl interface to Myki online account management portal

# VERSION 0.01

# SYNOPSIS

    use WWW::Myki;

    my $myki = WWW::Myki->new(
				username => 'myusername',
				password => 'mypassw0rd'
			);

    # Print card number, card holder, Myki money and Myki pass balances
   

    foreach $card ( $myki->cards ) {
      print "Card number: ". $card->id ." - Holder: ". $card->holder "\n";
      print "Myki money balance : ". $card->money ." - Myki pass balance: ". $card->pass ."\n";
    }

    # Print the date, time, service, description and cost of our last 15 transactions

    foreach my $trip ( $card->transactions ) { 
      printf( "%10s %8s %-10s %-20s %-5s\n", $trip->date, $trip->time, 
              $trip->service, $trip->desc, $trip->debit )
    } 
      

# DESCRIPTION

[WWW::Myki](http://search.cpan.org/perldoc?WWW::Myki) provides a simple interface to the Myki online account management portal functionality
for registered Myki users.

# METHODS

## new ( %args )

Constructor.  Creates a new WWW::Myki object and  attempts a login using the provided credentials.
On successful login, returns a WWW::Myki object.

The constructor accepts an anonymous hash of two mandatory parameters:

- username

Your registered Myki account username.

- password

Your registered Myki account password.

## cards

  my @cards = $myki->cards;

Returns an array of [WWW::Myki::Card](http://search.cpan.org/perldoc?WWW::Myki::Card) objects.  Each object is representative of a Myki card
registered to the specified account.

# AUTHOR

Luke Poskitt, `<ltp at cpan.org>`

# BUGS

Please report any bugs or feature requests to `bug-www-myki at rt.cpan.org`, or through
the web interface at [http://rt.cpan.org/NoAuth/ReportBug.html?Queue=WWW-Myki](http://rt.cpan.org/NoAuth/ReportBug.html?Queue=WWW-Myki).  I will be notified, and then you'll
automatically be notified of progress on your bug as I make changes.

# SUPPORT

You can find documentation for this module with the perldoc command.

    perldoc WWW::Myki

You can also look for information at:

- RT: CPAN's request tracker

[http://rt.cpan.org/NoAuth/Bugs.html?Dist=WWW-Myki](http://rt.cpan.org/NoAuth/Bugs.html?Dist=WWW-Myki)

- AnnoCPAN: Annotated CPAN documentation

[http://annocpan.org/dist/WWW-Myki](http://annocpan.org/dist/WWW-Myki)

- CPAN Ratings

[http://cpanratings.perl.org/d/WWW-Myki](http://cpanratings.perl.org/d/WWW-Myki)

- Search CPAN

[http://search.cpan.org/dist/WWW-Myki/](http://search.cpan.org/dist/WWW-Myki/)

# LICENSE AND COPYRIGHT

Copyright 2012 Luke Poskitt.

This program is free software; you can redistribute it and/or modify it
under the terms of either: the GNU General Public License as published
by the Free Software Foundation; or the Artistic License.

See http://dev.perl.org/licenses/ for more information.

# SEE ALSO

[WWW::Myki::Card](http://search.cpan.org/perldoc?WWW::Myki::Card), [WWW::Myki::Transaction](http://search.cpan.org/perldoc?WWW::Myki::Transaction)
