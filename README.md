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

```ruby
# Direkt auf der Klasse aufgerufen
Greeter.welcome

# mit Insatz und Instanzmethoden
g = Greeter.new("Herr")
g.hello("Denis")

g = Greeter.new("Frau")

g.hello(10)

```

Rails
-----

-r --> remote
-a --> all

gem search rails -r -a

rails

-d --> Database

rails new greeter

rails new greeter -d mysql

gvim 

rails-Projekt
-------------

im app-Ordner

MVC

Model --> 
View --> Optik/GUI
Controller --> 

config-Ordner
* Datenbank in database.yml

Environments:
* Development
* Test
* Production

(vorher passwort anpassen (in VM=="vagrant")

//rake db:drop

rake db:create

später migration:
rake db:migrate


Server starten mit:
rails s

// generatoren/ ?boiled code?
rails generate

home controller anlegen:
rails generate controller home

Es wird angelegt:
* Controller
* Unit Tests
* CSS/JS

render text: "Hello World"

Route
Mapping der URLs

//sidenote
sudo update-alternatives --config editor

//route:
get 'home' => 'home#index'


index.html.erb:
<span>Hello World!</span>

// in app/views/layouts/application können die Templates angepasst werden

im controlle rkann das layout mit:
layout 'home' definiert werden, dann würde er aus dem views /layouts entsprechend das dazugehörige layout verwenden


class HomeController < ApplicationController


  def index
    @user_name = "Peter"
  end

end


<span>Hello World, <%=@user_name %>!</span>


Debuggen mit Pry
----------------

im Gemfile:
gem 'pry-rails'
gem 'pry-full'

danach gems updaten
bundle

in Gemfile.lock finden sich alle Gems sowie die Gems welche durch Abhängigkeiten verwendet werden.

binding.pry
an entsprechender Stelle im Quellcod eeinfügen, der rails server bleibt entsprechend stehen.

 GNU nano 2.2.6           Datei: index.html.erb                              

<span>Hello World, <%=@user_name %>!</span>
<span><% if @gender == :male %>
Mr!
<% else %>
Mrs!
<% end %>

Assets - CSS
------------


in index.html.erb:
```ruby
<h1>Begrüßung</h1>
<div>Hello World, <span class="username"><%=@user_name %>!</span></div>
<span><% if @gender == :male %>
Mr!
<% else %>
Mrs!
<% end %>
<a id='click_me' href='#'>Klick Mich</a>
```

in assets/stylesheets/home.css.scss:
```scss
.username { 
font-weight: bold;
}
```

in assets/javascripts/home.js.coffee:
```coffescript
$ ->
	$('#click_me').click ->
		alert('test')
```


wenn man in der Config das Environment von Dev auf Prod setzt, dann werden die Assets optimiert bzw. z.B. zusammengepackt

```bash
RAILS_ENV=production rake assets:precompile
```

?bitte ergänzen?

Ein Model anlegen
-----------------

```bash
rails g model person name gender
```

Generiert ein model (Samt Migrationsdatei in db/migrate für die Datenbank) namens person mit den Feldern name und gender.

```bash
rake db:migrate
```

Legt die Tabelle entsprechend an

Daten anlegen über die Rails console
---------------

```bash
rails c
```



```ruby
Person.all #Ausgabe aller Personen (durch das Model angelegt), gibt erstmal keine

p = Person.new
p.class # zeigt alle Daten am Objekt an
p.name = "Matze"
p.gender = "female"
p.save #Speichert das Objekt in der Datenbank
Person.all # liefert jetzt was zurück
Person.first

torben = Person.new(name:"Torben",gender:"male") # Kurzform
torben.save

peter = Person.create(name: "Peter", gender:"male") # Kurzform + save
```

Nettere Formatierung von Person.all

```ruby
Person.all.to_a
```

Eintrag löschen
```ruby
herbert = Person.last
herbert.destroy

Person.count
```

Suchen nach Objekten:

```ruby
maike = Person.find_by_name('Maike')

# find_by liefert nur ein Objekt, find_all_by alle

Person.find_all_by_name('Maike')

Person.where('name like "M%"')

Person.where('name like "%M"').order('name ASC')

# find_by kann kombiniert werden
Person.find_by_name_and_gender('Maike','male')

# where kann auch kombiniert werden
Person.where('name = "Maike"').where('gender = "female')

stefan = Person.new(name:"Stefan")
stefan.new_record? # => true
stefan.save
stefan.new_record? # => false
```

Nette Seite für Dokus
---------------------

http://guides.rubyonrails.org

Index-Action soll Liste aller Benutzer ausgeben
----------------------------

home_controller.rb
```ruby
def index
	@people = Person.all
end
```

index.html.erb
```html
<h1>Personen</h1>
<ul>
	<% @people.each do |person| %>
		<li><%= person.gender == "male" ? "Mr." : "Mrs." %> <%= person.name %></li>	
	<% end %>
</ul>
```

führt zu

Personen
* Mrs. Matze
* Mr. Björn
* Mr. Torben
* Mr. Peter
* Mrs. Maike
* Mrs. Stefan

Refactoring von index.html.erb
-----------------------------

Um Logik aus einem View zu nehmen verlagert man sie in Funktionen in einem Helper.

app/helpes/home/helper

```ruby
module HomeHelper
	def determine_salutation(gender)
		if gender == "male"
			"Mr."
		elsif gender == "female"
			"Mrs."
		else
			"Trs."
		end
	end
end
```

app/views/home/index.html.erb

```html
<h1>Personen</h1>
<ul>
	<% @people.each do |person| %>
		<li><%= determine_salutation(person.gender) %> <%= person.name %></li>	
	<% end %>
</ul>
```

Namensliste aus dem Internet importieren
----------------------------

```bash
rails g controller import
```

app/controllers/import_controller.rb

```ruby
require 'open-uri'

class ImportController < ApplicationController

	def import_men
		html = open("http://www.ta7.de/txt/listen/list0014.htm")
	end

	def import_women
		html = open("http://www.ta7.de/txt/listen/list0013.htm")
	end

end

```

config/routes.rb

```ruby
	get 'import/women' => 'import#import_women'
	get 'import/men' => 'import#import_men'
```


app/controllers/import_controller.rb

cont[(cont.index("<p>")+"<p>".length)..(cont.index("</p>")-1)]

REST in Controllern und Formulare
-------------------

```bash
rails g controller people
```
app/controllers/people_controller

```ruby
class PeopleController < ApplicationController
	def index
		@people = Person.all
	end

	def new
		@person = Person.new
	end

	def create
		@person = Person.create(params[:person])
		redirect_to people_path
	end

	def edit
		
	end

	def update
		
	end

	def show
		
	end

	def destroy
		
	end
end

```

app/views/person/new.html.erb

```html
<%= form_for @person do |f| %>
	<%= f.text_field :name %>
	<%= f.submit 'Speichern' %>
<% end %>
```

Erzeugen aller REST-Routen auf einmal in config/routes.rb:

```ruby
resources :people
```