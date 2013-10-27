Übersicht
---------

Anfang
------

Ruby Grundlagen
---------------

* Ruby ist eine interpretierte Sprache
* keien Typisierung

```bash
ruby -v
```

--> zeigt Version an

```bash
whereis ruby
```

--> welche envrionment ist aktiv

```bash
ruby -e 'puts "Hello World!"'
```
ergibt
	Hello World!
```bash
mkdir workshop
gedit hello_world.rb
```

Code:
```ruby
puts "Hello World!"
```
```bash
ruby hello_world.rb
```
```ruby
puts("Hallo Welt!") # --> Funktionsaufruf
```

Klammern nicht extra notwendig, außer bei explziten Dingen

puts --> mit Zeilenvorschub/Umbruch
print --> ohne Zeilenvorschub/Umbruch

http://ruby-doc.org/ -> puts

http://www.ruby-doc.org/core-2.0.0/IO.html

irb --> inline Command Interpreter

Variablen definieren:
```ruby
zahl = 10
```
```ruby
puts zahl
```
--> 10

Ruby:
* Alles ist ein Objekt
* Alles bassiert auf dem Objekt
zahl.cass
--> String
zahl.methods
--> alle methoden

```ruby
name = "Peter"
name.upcase
```
--> PETER

bang -- !
verändert die Variable direkt
```ruby
name.upcase!
name
```
--> PETER

```ruby
1+2
1.class
1.methods
```

prüfen auf null, aber nil ist auch ein Objekt
haus.nil?
-->undifined

Arrays
------
```ruby
ary = [1,2]
```

Zugriff:
```ruby
ary[0]
```

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

```ruby
namen = ["Peter","Heiner","markus"]

namen.size
```
-->3

```ruby
namen.size

namen[0][0]
```
-->
"P"

Alternative:
```ruby
tiere = Array.new(["Ziege","Pferd"])

auto = %w(vw porsche mercedes)
auto << "opel"
```
auto
=> [
  [0] "vw",
  [1] "porsche",
  [2] "mercedes",
  [3] "opel"
]
```ruby
auto << ["bmw","tesla"]
```
--> fügt direkt als ein objekt ein

```ruby
auto.concat(["bmw","tesla"])
```
--> fügt als einzelnen objekte ein

```ruby
auto.flatten
```
--> flache hierachie

```ruby
auto.flatten!
```

```ruby
auto.collect{|auto| auto.upcase}
```

--> Schleife

```ruby
ri Array.collect
```
--> ruby interactive/info
--> quasi offline manpage

```ruby
auto.reverse
```

Unterschied each & collect
--------------------------

* each geht nur über die elemente drüber, macht nur das was im each block steht
* collect liefert ein array zurück

```ruby
auto.collect{|auto| auto.upcase}.each{ |auto| puts auto }

auto.map{ |auto| auto.upcase }

name = "Peter "
name.strip
```
--> "Peter"
```ruby
name.strip.upcase
```
--> "PETER"

```ruby
name = " Peter Schön "

name.strip.gsub("Schön", "Hässlich").upcase

gesubt = name.strip.gsub("Schön", "Hässlich").upcase

```

Assoziative Arrays - Hashs
------------------

```ruby
paare = { peter: "Toni",hansi:"Vroni",karsten: "Maxim"}

self.class

```

Symbole:
```ruby
paare[:hansi]
```
--> Vroni

```ruby
h  = {"eins" => "zwei"}
h["eins"]
h = {:eins => "zwei"}

h = {eins: "zwei"}
```

```ruby
paare.each{ |key,val| puts "#{key}: #{val}"}
```

peter: Toni
hansi: Vroni
karsten: Maxim
=> {
    :hansi => "Vroni",
  :karsten => "Maxim",
    :peter => "Toni"
}

```ruby
Hash.collect

paare.collect { |key, val| val }

paare.collect do |key, val|
key.upcase
end
```

Strichpunkt ";" für mehr als ein Befehl in einer Zeile
```ruby
paare.inject({}){|hsh, (key,val)| hsh[key.upcase] = val.upcase; hsh}

paare,inject({}) do |new_hash, (key, val)|
new_hash[key.upcase] = val.upcase
new_hash
end
```

Klassen
-------

* werden Groß geschrieben
```ruby
class Klassenname
	def self.welcome
		puts "guten Morgen"
	end
end
```

1.9.3 (main):0 > Greeter.welcome
guten Morgen
=> nil

Greeter.rb

```ruby
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
```


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
```


# Direkt auf der Klasse aufgerufen
Greeter.welcome

# mit Insatz und Instanzmethoden
g = Greeter.new("Herr")
g.hello("Denis")

g = Greeter.new("Frau")

g.hello(10)


