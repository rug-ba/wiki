Übersicht
---------

Anfang
------

Ruby Grundlagen
---------------

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

auto.map{ |auto| auto.upcase }

name = "Peter "
name.strip
--> "Peter"
name.strip.upcase
--> "PETER"

name = " Peter Schön "

name.strip.gsub("Schön", "Hässlich").upcase

gesubt = name.strip.gsub("Schön", "Hässlich").upcase

Assoziative Arrays - Hashs
------------------

paare = { peter: "Toni",hansi:"Vroni",karsten: "Maxim"}

self.class

Symbole:
paare[:hansi]
--> Vroni

h  = {"eins" => "zwei"}
h["eins"]
h = {:eins => "zwei"}

h = {eins: "zwei"}


paare.each{ |key,val| puts "#{key}: #{val}"}

peter: Toni
hansi: Vroni
karsten: Maxim
=> {
    :hansi => "Vroni",
  :karsten => "Maxim",
    :peter => "Toni"
}


Hash.collect

paare.collect { |key, val| val }

paare.collect do |key, val|
key.upcase
end


Strichpunkt ";" für mehr als ein Befehl in einer Zeile

paare.inject({}){|hsh, (key,val)| hsh[key.upcase] = val.upcase; hsh}

paare,inject({}) do |new_hash, (key, val)|
new_hash[key.upcase] = val.upcase
new_hash
end

Klassen
-------

* werden Groß geschrieben

class Klassenname
def self.welcome
puts "guten Morgen"
end
end

1.9.3 (main):0 > Greeter.welcome
guten Morgen
=> nil

Greeter.rb

Inhalt:
class Greeter

	def hello(salutation, name)
		puts "Hello #{salutation} #{name}"
	end

	def self.welcome
	puts "hello World"
	end

end

# Direkt auf der Klasse aufgerufen
Greeter.welcome

# mit Insatz und Instanzmethoden
g = Greeter.new
g.hello("Herr","Denis")

g.hello("",10)


Überladen von Funktionen nicht möglich

Statische Klassenvariablen und Klassenvariablen
```ruby
class Greeter

	@@counter = 0

	def initialize(salutation)
		@salutation = salutation
		@@counter +=1
	end

	def hello(name)
		puts "Hello #{@salutation} #{name} #{@@counter}"
	end

#	def hello(salutation, name)
#		puts "Hello #{salutation} #{name}"
#	end

	def self.welcome
	puts "hello World"
	end

end

´´´

# Direkt auf der Klasse aufgerufen
Greeter.welcome

# mit Insatz und Instanzmethoden
g = Greeter.new("Herr")
g.hello("Denis")

g = Greeter.new("Frau")

g.hello(10)


