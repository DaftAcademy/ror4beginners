Co się działo:

- Asocjacje
  - `belongs_to`, `has_one` i `has_many`
  - migracja na modelu `t.belongs_to :model, :constraints`
- Kontrola dostępu
  - gem do szyfrowania - `bcrypt`
  - hasło trzymane w polu `password_digest`, które trzeba dodać przez migrację
  - hasło zawsze jest trzymane jako szyfr, autentykacja polega na szyfrowaniu podanego hasła i porównaniu szyfrów
  - w modelu `User` należy dodać `has_secure_password`
  - autentykacja metodą `user.authenticate(:given_password)`
- Sesja
  - kilka wariantów m.in. server-side session lub ciastka
  - można łatwo zmienić, domyślnie korzystamy z ciastek
  - usuwanie sesji (wylogowanie) korzystając z `reset_session`
- Użycie
  - `sessions_controller` do logowania/wylogowywania
  - zapisujemy zalogowanego usera w `session[:identifier]`
  - możemy go później znaleźć przez np. `User.find_by(identifier: session[:identifier])`
