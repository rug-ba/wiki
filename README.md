Übersicht

Anfang

Ruby Grundlagen

* Ruby ist eine interpretierte Sprache
* keien Typisierung

ruby -v

--> zeigt Version an

whereis ruby

--> welche envrionment ist aktiv


ruby -e 'puts "Hello World!"'
ergibt
Hello World!

mkdir workshop
gedit hello_world.rb

Code:
puts "Hello World!"

ruby hello_world.rb

puts("Hallo Welt!") --> Funktionsaufruf

Klammern nicht extra notwendig, außer bei explziten Dingen

puts --> mit Zeilenvorschub/Umbruch
print --> ohne Zeilenvorschub/Umbruch

http://ruby-doc.org/ -> puts

http://www.ruby-doc.org/core-2.0.0/IO.html

irb --> inline Command Interpreter

Variablen definieren:
zahl = 10

puts zahl
--> 10

Ruby:
* Alles ist ein Objekt
* Alles bassiert auf dem Objekt
zahl.cass
--> String
zahl.methods
--> alle methoden


name = "Peter"
name.upcase
--> PETER

bang -- !
verändert die Variable direkt
name.upcase!
name
--> PETER

1+2
1.class
1.methods

prüfen auf null, aber nil ist auch ein Objekt
haus.nil?
-->undifined

Arrays
------
ary = [1,2]

Zugriff:
ary[0]

Pry Installation
----------------

gem --> Packagemanager für 

Gems @ http://rubygems.org/

Statistiken und Co zu Gems: https://www.ruby-toolbox.com/

gem search pry
--> lokale Suche

gem install crack
--> installation von gems

Pry
---

* kann syntaxhighlighting
* Tab completion für variablen
* methods verwendet less für Anzeige wenn es zu viele Methods gibt
* sorgt für bessere Struktur
* hat 

namen = ["Peter","Heiner","markus"]

namen.size
-->3


namen.size

namen[0][0]
-->
"P"

Alternative:
tiere = Array.new(["Ziege","Pferd"])

auto = %w(vw porsche mercedes)
auto << "opel"
auto
=> [
  [0] "vw",
  [1] "porsche",
  [2] "mercedes",
  [3] "opel"
]

auto << ["bmw","tesla"]
--> fügt direkt als ein objekt ein

auto.concat(["bmw","tesla"])
--> fügt als einzelnen objekte ein

auto.flatten
--> flache hierachie

auto.flatten!

auto.collect{|auto| auto.upcase}

--> Schleife

ri Array.collect
--> ruby interactive/info
--> quasi offline manpage

auto.reverse

Unterschied each & collect
--------------------------

* each geht nur über die elemente drüber, macht nur das was im each block steht
* collect liefert ein array zurück

auto.collect{|auto| auto.upcase}.each{ |auto| puts auto }
