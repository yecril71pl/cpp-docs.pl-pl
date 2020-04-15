---
title: '&lt;funkcje&gt; systemu plików'
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
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332047"
---
# <a name="ltfilesystemgt-functions"></a>&lt;funkcje&gt; systemu plików

Te bezpłatne funkcje w [ \<>nagłówka systemu plików](../standard-library/filesystem.md) modyfikują i pytają o operacje na ścieżkach, plikach, dowiązaniach symbolicznych, katalogach i woluminach. Aby uzyskać więcej informacji i przykłady kodu, zobacz [Nawigacja po systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>Bezwzględne

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkcja zwraca bezwzględną nazwa ścieżki odpowiadającą *pval* względem `base`nazwy ścieżki:

1. Jeśli `pval.has_root_name() && pval.has_root_directory()` funkcja zwraca *pval*.

1. Jeśli `pval.has_root_name() && !pval.has_root_directory()` funkcja `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`zwraca  /  `pval.relative_path()`.

1. Jeśli `!pval.has_root_name() && pval.has_root_directory()` funkcja `absolute(base).root_name()`  / zwraca *pval*.

1. Jeśli `!pval.has_root_name() && !pval.has_root_directory()` funkcja `absolute(base)`  / zwraca *pval*.

## <a name="begin"></a><a name="begin"></a>Rozpocząć

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obie funkcje zwracają *iter*.

## <a name="canonical"></a><a name="canonical"></a>Kanoniczna

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Wszystkie funkcje tworzą bezwzględną `pabs = absolute(pval, base)` nazwa `pabs = absolute(pval)` ścieżki (lub dla przeciążenia bez parametru podstawowego), a następnie zmniejszają ją do postaci kanonicznej w następującej kolejności kroków:

1. Każdy składnik `X` ścieżki, dla `is_symlink(X)` którego `read_symlink(X)`jest **spełniony,** jest zastępowany przez .

1. Każdy składnik `.` ścieżki (kropka jest bieżącym katalogiem ustanowionym przez poprzednie składniki ścieżki) jest usuwany.

1. Każda para składników `X` / `..` ścieżki (kropka jest katalogiem nadrzędnym ustanowionym przez poprzednie składniki ścieżki) jest usuwana.

Następnie funkcja `pabs`zwraca .

## <a name="copy"></a><a name="copy"></a>Kopii

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkcje wszystkie ewentualnie skopiować lub połączyć jeden lub więcej plików *od* `copy_options::none` *do* pod kontrolą opts , który jest *traktowany*jak dla przeciążenia bez *parametru opts.* *decyduje,* że zawiera co najwyżej jeden z:

- `skip_existing`, `overwrite_existing`, lub`update_existing`

- `copy_symlinks` lub `skip_symlinks`

- `directories_only`, `create_symlinks`, lub`create_hard_links`

Funkcje najpierw określają wartości `f` file_status dla `t` *od* i *do:*

- jeśli `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, dzwoniąc`symlink_status`

- w przeciwnym razie, dzwoniąc`status`

- W przeciwnym razie zgłoś błąd.

Jeśli `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, następnie zgłosić błąd (i nic więcej).

W przeciwnym `is_symlink(f)` razie, jeśli następnie:

- Jeśli `options & copy_options::skip_symlinks`, to nic nie rób.

- W przeciwnym `!exists(t)&& options & copy_options::copy_symlinks`razie, jeśli , a następnie `copy_symlink(from, to, opts)`.

- W przeciwnym razie zgłoś błąd.

W przeciwnym `is_regular_file(f)`razie, jeśli , następnie:

- Jeśli `opts & copy_options::directories_only`, to nic nie rób.

- W przeciwnym `opts & copy_options::create_symlinks`razie, jeśli , a następnie `create_symlink(to, from)`.

- W przeciwnym `opts & copy_options::create_hard_links`razie, jeśli , a następnie `create_hard_link(to, from)`.

- W przeciwnym `is_directory(f)`razie, jeśli , a następnie `copy_file(from, to`  /  `from.filename(), opts)`.

- W przeciwnym razie wartość `copy_file(from, to, opts)`.

W przeciwnym `is_directory(f) && (opts & copy_options::recursive || !opts)`razie, jeśli , następnie:

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

Wszystkie funkcje ewentualnie skopiować plik *od* *do* pod kontrolą *opts*, który jest traktowany jak `copy_options::none` dla przeciążeń bez *parametru opts.* *decyduje,* że zawiera co `skip_existing` `overwrite_existing`najwyżej `update_existing`jeden z , lub .

Jeśli `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, zgłoś jako błąd, że plik już istnieje.

W przeciwnym `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`razie, jeśli , a następnie spróbuj skopiować zawartość i atrybuty pliku *z* pliku do pliku *do*. Zgłoś jako błąd, jeśli próba kopiowania nie powiedzie się.

Funkcje zwracają **wartość true,** jeśli kopia jest podejmowana i powiedzie się, w przeciwnym razie **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Jeśli `is_directory(from)`funkcja wywołuje `create_directory_symlink(from, to)`. W przeciwnym `create_symlink(from, to)`razie wywołuje .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Dla nazwy ścieżki, takich\/\/jak b c, funkcja tworzy\/katalogi a i b w\/razie\/potrzeby, dzięki czemu można utworzyć katalog b c w razie potrzeby. Zwraca **true** tylko wtedy, gdy faktycznie tworzy *pval*katalogu .

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkcja tworzy *pval* katalogu w razie potrzeby. Zwraca true tylko wtedy, gdy faktycznie tworzy *pval*katalogu , w którym to przypadku kopiuje uprawnienia z istniejącego pliku *attr*, lub używa `perms::all` dla przeciążenia bez *attr* parametru.

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy łącze jako dowiązanie symboliczne do katalogu *do*.

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

Funkcja tworzy *łącze* jako odłączenie do pliku *do*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkcje bez *parametru pval* zwracają nazwa ścieżki dla bieżącego katalogu. Pozostałe funkcje ustawiją bieżący katalog *na pval*.

## <a name="end"></a><a name="end"></a>Końcu

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Zwraca pierwszą `directory_iterator()` funkcję, a druga funkcja zwraca`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Równoważne

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkcje zwracają **wartość true** tylko *wtedy, gdy lewa* i *prawa* wybierze tę samą encję systemu plików.

## <a name="exists"></a><a name="exists"></a>Istnieje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `status_known && stat.type() != file_not_found`funkcję . Powrót drugiej i `exists(status(pval))`trzeciej funkcji .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają rozmiar w bajtach pliku wybranego przez `exists(pval) && is_regular_file(pval)` *pval*, jeśli i można określić rozmiar pliku. W przeciwnym razie zgłaszają `uintmax_t(-1)`błąd i zwracają .

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca liczbę twardych łączy dla \- *pval*lub 1, jeśli wystąpi błąd.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkcja zwraca wartość mieszania `pval.native()`dla .

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::block`funkcję . Pozostałe funkcje `is_block_file(status(pval))`zwracają .

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::character`funkcję . Pozostałe funkcje `is_character_file(status(pval))`zwracają .

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::directory`funkcję . Pozostałe funkcje `is_directory_file(status(pval))`zwracają .

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Jeśli `is_directory(pval)`funkcja zwraca `directory_iterator(pval) == directory_iterator()`; w przeciwnym `file_size(pval) == 0`razie zwraca .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::fifo`funkcję . Pozostałe funkcje `is_fifo(status(pval))`zwracają .

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::other`funkcję . Pozostałe funkcje `is_other(status(pval))`zwracają .

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::regular`funkcję . Pozostałe funkcje `is_regular_file(status(pval))`zwracają .

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::socket`funkcję . Pozostałe funkcje `is_socket(status(pval))`zwracają .

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Zwraca pierwszą `stat.type() == file_type::symlink`funkcję . Pozostałe funkcje `is_symlink(status(pval))`zwracają .

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Pierwsze dwie funkcje zwracają czas ostatniej modyfikacji `file_time_type(-1)` danych dla *pval*lub jeśli wystąpi błąd. Dwie ostatnie funkcje ustawiają czas ostatniej modyfikacji danych dla *pval* na *new_time*.

## <a name="permissions"></a><a name="permissions"></a>Uprawnienia

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkcje ustawiają uprawnienia dla nazwy ścieżki wybranej `mask & perms::mask` przez `perms & (perms::add_perms | perms::remove_perms)` *pval* na pod kontrolą . *maska* zawiera co `perms::add_perms` najwyżej `perms::remove_perms`jedną z

Jeśli `mask & perms::add_perms`, funkcje ustawić `status(pval).permissions() | mask & perms::mask`uprawnienia do . W przeciwnym `mask & perms::remove_perms`razie, jeśli , `status(pval).permissions() & ~(mask & perms::mask)`funkcje ustawić uprawnienia do . W przeciwnym razie funkcje `mask & perms::mask`ustawiają uprawnienia na .

## <a name="proximate"></a><a name="proximate"></a>bliższy

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

Funkcje zgłaszają błąd `path()` i `!is_symlink(pval)`zwracają, jeśli . W przeciwnym razie funkcje `path` zwracają obiekt typu zawierający dowiązanie symboliczne.

## <a name="relative"></a><a name="relative"></a>Względne

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>Usunąć

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Funkcje **true** zwracają true `exists(symlink_status(pval))` tylko wtedy, gdy plik zostanie pomyślnie usunięty. Samo dowiązanie symboliczne jest usuwane, a nie plik, który wybierze.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Jeśli *pval* jest katalogiem, funkcje cyklicznie usuwają wszystkie wpisy katalogu, a następnie sam wpis. W przeciwnym razie `remove`funkcje wywołają . Zwracają liczbę wszystkich elementów pomyślnie usunięte.

## <a name="rename"></a><a name="rename"></a>Zmienić nazwę

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Nazwy funkcji *od* do *.* Sama nazwa dowiązka symboliczna jest zmieniana, a nie plik, który wybierze.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkcje zmieniają rozmiar pliku w taki sposób, że`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Miejsca

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca informacje o woluminie *wybranym*przez pval `space_info`, w strukturze typu . Struktura zawiera `uintmax_t(-1)` dla każdej wartości, która nie może być określona.

## <a name="status"></a><a name="status"></a>Stan

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Funkcje zwracają stan nazwy ścieżki, typ pliku i uprawnienia skojarzone z *pval*. Samo dowiązanie symboliczne nie jest testowane, ale wybiera plik.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Funkcja zwraca`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Wymiany

```cpp
void swap(path& left, path& right) noexcept;
```

Funkcja wymienia zawartość *lewej* i *prawej strony*.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Funkcje zwracają stan dołączenia symbolicznego nazwy ścieżki, typ pliku i uprawnienia skojarzone z *pval*. Funkcje zachowują się `status(pval)` tak samo, jak z tą różnicą, że samo dowiązanie symboliczne jest testowane, a nie plik, który wybierze.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Funkcje zwracają bezwzględną nazwę ścieżki, która uwzględnia, w razie potrzeby, bieżący katalog skojarzony z jego nazwą główną. \(W przypadku POSIX `absolute(pval)`funkcje zwracają .\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkcje zwracają nazwa ścieżki dla katalogu odpowiedniego do przechowywania plików tymczasowych.

## <a name="u8path"></a><a name="u8path"></a>u8path (ścieżka u8path)

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Pierwsza funkcja zachowuje się `path(source)` tak samo, a druga `path(first, last)` funkcja zachowuje się tak samo, z tą różnicą, że wybrane źródło w każdym przypadku jest traktowane jako sekwencja char elementów zakodowanych jako UTF-8, niezależnie od systemu plików.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
