Co się działo:
- Model
  - generacja przez `rails generate model name`
  - migracja - uzupełnia odpowiadającą modelowi tabelę
  - constrainty na polu w bazie danych np. `null: false`
  - skrypt wywołania migracji `rake db:migrate`
  - `db/schema.rb` jest plikiem odpowiadającym za stan bazy
  - konfiguracja bazy znajduje się w `config/database.yml`
  
- Metody
  - `form_for @object do |f|` - inteligentny helper do generacji formularza dla obiektu
  - `f.label`, `f.text_field` itp - helpery do generacji elementów formularza
  - strong parameters - z założenia wszystkie parametry są niedozwolone, więc np. `params.require(:user).permit(:email)`
  - `redirect_to PREFIX_path` - przekierowanie w kontrolerze, nie do każdej akcji potrzebujemy widoku

- REST - REpresentational State Transfer
  - konwencja konstrukcji kontrolerów i akcji oraz odpowiadający im routing
  - metoda `resources` do generacji RESTowych ścieżek

- Zestawienie <metoda akcja | ścieżka | opis> na przykładzie zasobu `user` (`users_controller`)
  - GET index | `/users` | kolekcja np. `User.all`
  - GET show | `/users/:id` | pojedyńczy np. `User.find(params[:id])`
  - GET new | `/users/new` | formularz nowego np. `User.new`
  - POST create | `/users` | tworzenie np. `User.create(user_params)`
  - GET edit | `/users/:id/edit` | formularz edycji np. `User.find(params[:id])`
  - PUT/PATCH update | `/users/:id` | aktualizacja np. `user.update(user_params)`
  - DELETE destroy | `/users/:id` | usunięcie np. `user.destroy`
 
 Zadania:
 1. Dodaj do modelu `User` pole `admin` (boolean - true/false)
  - stwórz migrację korzystając z `rails g migration name`, gdzie name to np. `AddAdminToUsers`
  - w nowo stworzonym pliku dodaj kolumnę korzystając z metody
  
    `add_column table, column_name, column_type, constraints`
  - dodanie np. pola email wyglądałoby tak
  
    `add_column :users, :email, :string, null: false`
  - wystarczy skorzystanie z metody `change`, Rails sam zrozumie odwrotność metody `add_column` w przypadku rollbacku
  - upewnij się, że domyślnie `admin` jest ustawione na `false` korzystając z constraintu `default`
  2. Wypisz wartość pola `admin` na widokach `index` i `show`
  3. Pozwól na modyfikację pola `admin` przy edycji, ale nie przy tworzeniu
  - dodaj `f.check_box` na formularzu edycji
  - upewnij się, że pole `admin` może być zmienione tylko w akcji `update` (strong parameters!)
  4. (*) Dodaj do modelu `User` metodę instancyjną, która zastąpi `user.name`
  - metoda ma zwracać albo pole `name` usera, albo gdy nie jest sprecyzowane, część emaila przed `@`
  - w `index` i `show` zamiast korzystać z `name`, korzystaj z tej metody
  
