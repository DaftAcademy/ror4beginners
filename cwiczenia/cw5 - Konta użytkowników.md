Co się działo:

- Kontroler
  - `before_action :method_name` wywołuje metodę przed każdą akcją
  - można limitować przez `only: [...]` lub `except: [...]`
  - można przerwać "flow" w `before_action` korszystając z np. `redirect_to somewhere if invalid`
  - `helper_method :method_name` udostępnia tę metodę w widoku
- Asocjacje
  - tworzymy nowy rekord w relacji z aktualnie zalogowanym użytkownikiem korzystając z asocjacji, np. `current_user.links.new`
  - możemy w taki sposób zawężyć obszar wyszukiwań - `Link.all` zwróci więcej niż `current_user.links`
- Widok
  - korzystanie z `if/else` by wyświetlać np. header w odpowiednim kontekście
  - helper metoda z kontrolera jest tu dostępna, np. `current_user`
- Ogólne
  - `&` broni przed `nil` zwracając `nil` zamiast `NoMethodError`, np. `nil&.email #=> nil`
  - `puts` wypluwa "sformatowane" dane, `p` wypluwa je tak surowo jak potrafi
  - `lib/tasks/` jest folderem na taski - skrypty wywoływane "on demand", korzystając z `rake namespace:name`
  - `db/seeds.rb` jest wyjątkowym przykładem takiego taska, tam zazwyczaj sie prepopuluje bazę danych - `rake db:seed`
