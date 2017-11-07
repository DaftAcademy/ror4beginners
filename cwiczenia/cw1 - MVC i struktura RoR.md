Co się działo:
- MVC - Model View Controller
  - Model zajmuje się reprezentacją danych
  - View jest widokiem który użytkownik widzi
  - Controller wybiera co i jak pokazać użytkownikowi
- Najważniejsze pliki w Railsach
  - `Gemfile` - deklaracja bibliotek (instalacja przez `bundle install`)
  - `config/routes.rb` - ścieżki, konwertuje adres i metodę zapytania na odpowiednią akcję w kontrolerze
  - `app/assets` - obrazki, skrypty (css, js) i inne media
  - `app/(models|views|controllers)` - (modele|widoki|kontrolery)
  - lokalizacja i nazwa pliku ma znaczenie! (autoloading)
- Scaffolding - generacja podstawowych plików
  - generatory - `rails generate (controller|model) nazwa`
  - destruktory - `rails destroy (controller|model) nazwa`
- Kontroler i widok
  - podstawowa akcja
  - widok odpowiednio zagnieżdżony i nazwany
  - `.erb` umożliwia egzekucję kodu ruby
  - zmienna instancyjna `@name` umożliwia dostęp z poziomu widoku
- Routing
  - skierowanie domyślnej ścieżki na naszą akcję przez `root to: 'controller#action'`

Zadania:
1. Stwórz swój projekt jednym ze sposobów
  - stwórz nowy wybierając startowy template Ruby on Rails, uzupełnij to co robiliśmy na ćwiczeniach
  - sklonuj projekt `pkruczek/ror4beginners2017` w teamie `rorworkshops`
2. Dodaj podstronę `/about`
  - dodaj akcję do kontrolera `home`
  - stwórz odpowiedni widok w `views/home/`, wpisz tam cokolwiek
  - dodaj ścieżkę do tej akcji korzystając z `get '/about', to: 'controller#action'`
3. W widoku `home/welcome` dodaj odnośnik (`<a>`) do nowo stworzonej podstrony `/about`
  - skorzystaj z helpera `link_to <PREFIX>_path`
  - by dowiedzieć się jaki jest prefix `/about` skorzystaj z komendy `rake routes` (w nowym terminalu)
4. Dodaj header (`div`) do strony, z odnośnikiem (`a`) do strony głównej. Tekst dowolny.
  - skorzystaj z layoutu (`views/layouts/application.html.erb`)
  - do odnośnika skorzystaj z helpera railsowego
  - słowo kluczowe `yield` jest miejscem, gdzie "wstrzykiwany" jest określony widok
  - upewnij się, że header jest widoczny zarówno na `/` jak i `/about`
