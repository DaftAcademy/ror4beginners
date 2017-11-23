Co się działo:
- Walidacje
  - `validates :attribute, helper: 'helper_value'`, na przykład `validates :email, presence: true`
  - lista helperów: http://guides.rubyonrails.org/active_record_validations.html
  - `validate :my_custom_method`, wymaga zdefiniowania własnej metody
- Błędy
  - modele przed zapisaniem wykonują walidacje i uzupełniają `my_object.errors`
  - wyświetlenie błędów walidacji `my_object.errors.messages`
  - dodanie nowego błędu np. w customowej walidacji `errors.add(:attribute, :message)` - `errors.add(:photo, 'is ugly')`
- Dodatkowo
  - w controllerze render w akcji `create` przy błędzie zapisu - `render :new`
  - zmiana parametru indentyfikacyjnego w routingu korzystając z `param: :param_name`
  - enumerator - integer w bazie mapowany na stringi po stronie aplikacji `enum attribute: [:s1, :s2, :s3]`

Zadania:
1. W akcji `show` kontrolera `links` mamy potencjalny błąd. Metoda `find_by` zwróci `nil`, gdy nie znajdzie odpowiedniego linka.
Następnie w interpolacji spróbuje wywołać `scheme` i `target_url` na `nil` zamiast na obiekcie klasy `Link`.
Oczywiście nie ma takich metod na `nil`. Obsłuż ten przypadek przekierowując użytkownika na listę linków.
2. W akcji `create` kontrolera `links` zawsze jest renderowany widok `:new`.
Zmodyfikuj ją tak, by przy poprawnym zapisaniu użytkownik został przekierowany na listę linków.
Skorzystaj z metody `new_record?`.
3. Dodaj walidację na modelu `Link` upewniającą się, że `source_url` jest unikalny. Skorzystaj z odpowiedniego helpera.
4. W akcji new wygeneruj dla użytkownika propozycję `source_url`, od razu ustawiając to pole:
  - skorzystaj z `SecureRandom.urlsafe_base64(2)`
  - (*) stwórz metodę klasową dla `Link` z której skorzystasz zamiast `new`
  - (**) upewnij się, że proponowany link nie jest już zajęty
5. (*) Dodaj możliwość ustawienia `scheme` przy tworzeniu linka. Podpowiedzi:
  - `f.select :field, options`
  - mozliwe scheme: `Link.schemes.to_a`
  - strong parameters
6. (**) Skorzystaj z modułu `URI`, by przed zapisaniem linka zmodyfikować tak `target_url` by był poprawnym adresem i korzystał z wybranego `scheme`.
  - zdefiniuj metodę instancyjną w modelu `Link`
  - popraw akcję `show` by kierowała już na `target_url`
