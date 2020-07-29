---
title: '&lt;funkcje systemu plików &gt;'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: c637c4893a13df577fd6c083c8a4f2380c9c4cad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219160"
---
# <a name="ltfilesystemgt-functions"></a>&lt;funkcje systemu plików &gt;

Te bezpłatne funkcje w [\<filesystem>](../standard-library/filesystem.md) nagłówku modyfikują i wykonują zapytania dotyczące operacji na ścieżkach, plikach, linków symbolicznych, katalogach i woluminach. Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>pozycjonowa

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkcja zwraca bezwzględną nazwę ścieżki odpowiadającą *Pval* względem nazwy ścieżki `base` :

1. Jeśli `pval.has_root_name() && pval.has_root_directory()` Funkcja zwraca *Pval*.

1. Jeśli `pval.has_root_name() && !pval.has_root_directory()` Funkcja zwraca wartość `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()` .

1. Jeśli `!pval.has_root_name() && pval.has_root_directory()` Funkcja zwraca `absolute(base).root_name()`  /  *Pval*.

1. Jeśli `!pval.has_root_name() && !pval.has_root_directory()` Funkcja zwraca `absolute(base)`  /  *Pval*.

## <a name="begin"></a><a name="begin"></a>zaczną

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obie funkcje zwracają *ITER*.

## <a name="canonical"></a><a name="canonical"></a>postaci

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Wszystkie funkcje tworzą bezwzględną nazwę ścieżki `pabs = absolute(pval, base)` (lub `pabs = absolute(pval)` dla przeciążenia bez parametru podstawowego), a następnie redukuje ją do postaci kanonicznej w następującej kolejności kroków:

1. Każdy składnik ścieżki `X` , dla którego jest `is_symlink(X)` **`true`** zastępowany przez `read_symlink(X)` .

1. Każdy składnik ścieżki `.` (kropka jest bieżącym katalogiem ustanowionym przez poprzednie składniki ścieżki) jest usuwany.

1. Każda para składników ścieżki `X` / `..` (kropka-kropka jest katalogiem nadrzędnym ustanowionym przez poprzednie składniki ścieżki) jest usuwana.

Funkcja zwraca wartość `pabs` .

## <a name="copy"></a><a name="copy"></a>kopiowane

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Wszystkie *funkcje, które*prawdopodobnie kopiują lub łączą jeden lub więcej plików *od* *do pod kontrolą opcji,* który jest traktowany jak `copy_options::none` dla przeciążenia bez żadnego *opts* parametru. takie *działania powinny zawierać* co najwyżej jeden z:

- `skip_existing`, `overwrite_existing` lub`update_existing`

- `copy_symlinks` lub `skip_symlinks`

- `directories_only`, `create_symlinks` lub`create_hard_links`

Funkcje najpierw określają wartości file_status `f` *from* dla `t` : *to*

- Jeśli `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)` , wywołując`symlink_status`

- w przeciwnym razie, wywołując`status`

- W przeciwnym razie Zgłoś błąd.

Jeśli `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)` następnie zgłosi błąd (i nic nie rób).

W przeciwnym razie `is_symlink(f)` :

- Jeśli `options & copy_options::skip_symlinks` nie, nic nie rób.

- W przeciwnym razie, jeśli `!exists(t)&& options & copy_options::copy_symlinks` , `copy_symlink(from, to, opts)` .

- W przeciwnym razie Zgłoś błąd.

W przeciwnym razie, jeśli `is_regular_file(f)` :

- Jeśli `opts & copy_options::directories_only` nie, nic nie rób.

- W przeciwnym razie, jeśli `opts & copy_options::create_symlinks` , `create_symlink(to, from)` .

- W przeciwnym razie, jeśli `opts & copy_options::create_hard_links` , `create_hard_link(to, from)` .

- W przeciwnym razie, jeśli `is_directory(f)` , `copy_file(from, to`  /  `from.filename(), opts)` .

- W przeciwnym razie wartość `copy_file(from, to, opts)`.

W przeciwnym razie, jeśli `is_directory(f) && (opts & copy_options::recursive || !opts)` :

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

W przeciwnym razie nic nie rób.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Wszystkie funkcje, które prawdopodobnie kopiują plik *od* do *do* pod kontrolą opcji *, które*są wykonywane jak `copy_options::none` dla przeciążenia bez dołączania *opts* parametru. takie *działania powinny zawierać* co najwyżej jedną z `skip_existing` , `overwrite_existing` lub `update_existing` .

Jeśli `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))` , następnie Zgłoś błąd, że plik już istnieje.

W przeciwnym razie, w przypadku `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))` próby skopiowania zawartości i atrybutów pliku *z* do pliku *do*. Zgłoś jako błąd, jeśli próba kopiowania nie powiedzie się.

Funkcje zwracają **`true`** , jeśli kopia jest próbna i się powiedzie, w przeciwnym razie **`false`** .

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Jeśli `is_directory(from)` , funkcja wywołuje `create_directory_symlink(from, to)` . W przeciwnym razie wywołuje `create_symlink(from, to)` .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Dla nazwy ścieżki, takiej jak \/ b \/ c, funkcja tworzy katalogi a i a \/ b zgodnie z wymaganiami, aby można było utworzyć katalog a \/ b \/ c zgodnie z wymaganiami. Zwraca **`true`** tylko wtedy, gdy faktycznie tworzy katalog *Pval*.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkcja tworzy katalog *Pval* zgodnie z wymaganiami. Zwraca wartość true tylko wtedy, gdy faktycznie tworzy katalog *Pval*, w którym to przypadku kopiuje uprawnienia z istniejącego *atrybutu*pliku lub używa `perms::all` dla przeciążenia bez parametru *ATTR* .

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy link jako link symboliczny *do katalogu.*

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy łącze jako twarde łącze do katalogu lub pliku *do*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy *link* jako link symboliczny *do pliku.*

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkcje bez parametru *Pval* zwracają nazwę ścieżki dla bieżącego katalogu. Pozostałe funkcje ustawiają bieżący katalog na *Pval*.

## <a name="end"></a><a name="end"></a>punktów

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Pierwsza funkcja zwraca `directory_iterator()` , a druga funkcja zwraca`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>samą

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkcje zwracają **`true`** tylko wtedy, gdy *lewe* i *prawe* wybierz tę samą jednostkę systemu plików.

## <a name="exists"></a><a name="exists"></a>istniejący

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `status_known && stat.type() != file_not_found` . Druga i trzecia funkcja zwracają `exists(status(pval))` .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają rozmiar w bajtach pliku wybranego przez *Pval*, jeśli `exists(pval) && is_regular_file(pval)` rozmiar pliku można określić. W przeciwnym razie zgłasza błąd i zwraca `uintmax_t(-1)` .

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca liczbę twardych linków dla *Pval*lub \- 1 w przypadku wystąpienia błędu.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkcja zwraca wartość skrótu dla `pval.native()` .

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::block` . Pozostałe funkcje zwracają `is_block_file(status(pval))` .

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::character` . Pozostałe funkcje zwracają `is_character_file(status(pval))` .

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::directory` . Pozostałe funkcje zwracają `is_directory_file(status(pval))` .

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Jeśli `is_directory(pval)` , wówczas funkcja zwraca `directory_iterator(pval) == directory_iterator()` ; w przeciwnym razie zwraca `file_size(pval) == 0` .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::fifo` . Pozostałe funkcje zwracają `is_fifo(status(pval))` .

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::other` . Pozostałe funkcje zwracają `is_other(status(pval))` .

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::regular` . Pozostałe funkcje zwracają `is_regular_file(status(pval))` .

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::socket` . Pozostałe funkcje zwracają `is_socket(status(pval))` .

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca wartość `stat.type() == file_type::symlink` . Pozostałe funkcje zwracają `is_symlink(status(pval))` .

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Pierwsze dwie funkcje zwracają czas ostatniej modyfikacji danych dla *Pval*lub w `file_time_type(-1)` przypadku wystąpienia błędu. Ostatnie dwie funkcje ustawiają godzinę ostatniej modyfikacji danych *Pval* do *new_time*.

## <a name="permissions"></a><a name="permissions"></a>uprawnienia

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkcje ustawiają uprawnienia dla nazwy ścieżki wybranej przez *Pval* `mask & perms::mask` pod kontrolą `perms & (perms::add_perms | perms::remove_perms)` . *maska* powinna zawierać co najwyżej jeden z `perms::add_perms` i `perms::remove_perms` .

Jeśli `mask & perms::add_perms` funkcje te ustawili uprawnienia na `status(pval).permissions() | mask & perms::mask` . W przeciwnym razie, jeśli `mask & perms::remove_perms` funkcje te ustawią uprawnienia na `status(pval).permissions() & ~(mask & perms::mask)` . W przeciwnym razie funkcje te ustawią uprawnienia na `mask & perms::mask` .

## <a name="proximate"></a><a name="proximate"></a>znajdującym

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Funkcje raportują błąd i zwracają `path()` Jeśli `!is_symlink(pval)` . W przeciwnym razie funkcje zwracają obiekt typu `path` zawierający link symboliczny.

## <a name="relative"></a><a name="relative"></a>rodziny

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>usuwa

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają **`true`** tylko wtedy `exists(symlink_status(pval))` , gdy plik zostanie pomyślnie usunięty. Link symboliczny jest usuwany, a nie do pliku, który wybiera.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Jeśli *Pval* jest katalogiem, funkcja cyklicznie usuwa wszystkie wpisy katalogu, a następnie sam wpis. W przeciwnym razie wywołania funkcji `remove` . Zwracają one liczbę pomyślnie usuniętych elementów.

## <a name="rename"></a><a name="rename"></a>ZmieńNazwę

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Funkcje Zmień nazwę *z* na *na.* Link symboliczny jest sama nazwana, a nie do pliku, który wybiera.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkcje zmieniają rozmiar pliku w taki sposób, aby`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>odstęp

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca informacje o woluminie wybranym przez *Pval*w strukturze typu `space_info` . Struktura zawiera `uintmax_t(-1)` dla każdej wartości, której nie można określić.

## <a name="status"></a><a name="status"></a>Stany

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają stan ścieżki, typ pliku i uprawnienia skojarzone z *Pval*. Link symboliczny nie jest przetestowany, ale plik wybiera.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Funkcja zwraca`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>wymiany

```cpp
void swap(path& left, path& right) noexcept;
```

Funkcja wymienia zawartość z *lewej* i *prawej*strony.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają nazwę ścieżki link symboliczny stan, typ pliku i uprawnienia skojarzone z *Pval*. Funkcje zachowują się tak samo, jak `status(pval)` z tą różnicą, że link symboliczny jest przetestowany, a nie z wybranym przez niego plikiem.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Funkcje zwracają bezwzględną nazwę ścieżki, która w razie potrzeby bierze pod uwagę bieżący katalog skojarzony z jego nazwą główną. \(W przypadku modelu POSIX funkcje zwracają `absolute(pval)` .\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkcje zwracają nazwę ścieżki dla katalogu odpowiednie dla plików tymczasowych.

## <a name="u8path"></a><a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Pierwsza funkcja zachowuje się tak samo, jak `path(source)` i druga funkcja zachowuje się tak samo, jak `path(first, last)` z tą różnicą, że wybrane źródło w każdym przypadku jest wykonywane jako sekwencja elementów char zakodowanych jako UTF-8, niezależnie od systemu plików.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
