---
title: '&lt;System plików&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc53bff438830cfb8a7b0414c4e5cfb111f8f31
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691500"
---
# <a name="ltfilesystemgt-functions"></a>&lt;System plików&gt; funkcji

Bezpłatne funkcje w [ \<filesystem >](../standard-library/filesystem.md) nagłówka wykonać operacje modyfikowania i zapytania na ścieżkach, plików, łączy symbolicznych, katalogów i woluminów. Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).
||||
|-|-|-|
|[absolute](#absolute)|[begin](#begin)|[Canonical](#canonical)|
|[Kopiuj](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories —](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[koniec](#end)|[equivalent](#equivalent)|[Istnieje](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[Uprawnienia](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[Zmień nazwę](#rename)|
|[resize_file](#resize_file)|[miejsce](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name="absolute"></a> Bezwzględna

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkcja zwraca ścieżki odpowiadające *pval* względną nazwę ścieżki `base`:

1. Jeśli `pval.has_root_name() && pval.has_root_directory()` funkcja zwraca *pval*.

1. Jeśli `pval.has_root_name() && !pval.has_root_directory()` funkcja zwraca `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`.

1. Jeśli `!pval.has_root_name() && pval.has_root_directory()` funkcja zwraca `absolute(base).root_name()`  /  *pval*.

1. Jeśli `!pval.has_root_name() && !pval.has_root_directory()` funkcja zwraca `absolute(base)`  /  *pval*.

## <a name="begin"></a>  Rozpocznij

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obie funkcje zwracają *iter*.

## <a name="canonical"></a>  Canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Wszystkie funkcje tworzą ścieżki `pabs = absolute(pval, base)` (lub `pabs = absolute(pval)` dla przeciążenia z nie parametru base), następnie ograniczyć do forma kanoniczna po kolei następujące czynności:

1. Każdy składnik path `X` dla którego `is_symlink(X)` jest **true** zastępuje `read_symlink(X)`.

1. Każdy składnik path `.` (kropka jest bieżący katalog ustanowione przez poprzednie składników ścieżki) zostanie usunięta.

1. Każdej pary składników ścieżki `X` / `..` (kropka kropka jest ustanowione przez poprzednie składników ścieżki katalogu nadrzędnego) zostanie usunięta.

Następnie funkcja zwraca `pabs`.

## <a name="copy"></a>  Kopiuj

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkcje wszystkie możliwie skopiować lub połączyć jeden lub więcej plików w *z* do *do* pod kontrolą *zdecyduje*, która jest traktowana jako `copy_options::none` dla przeciążeń z nie *zdecyduje* parametru. *zdecyduje* zawierają co najwyżej jedno z:

- `skip_existing`, `overwrite_existing`, lub `update_existing`

- `copy_symlinks` lub `skip_symlinks`

- `directories_only`, `create_symlinks`, lub `create_hard_links`

Funkcje najpierw określić wartości file_status `f` dla *z* i `t` dla *do*:

- Jeśli `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, wywołując `symlink_status`

- w przeciwnym razie przez wywołanie metody `status`

- W przeciwnym razie Zgłoś błąd.

Jeśli `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, są następnie Zgłoś błąd (i nic innego).

W przeciwnym razie, jeśli `is_symlink(f)` następnie:

- Jeśli `options & copy_options::skip_symlinks` nic nie rób.

- W przeciwnym razie, jeśli `!exists(t)&& options & copy_options::copy_symlinks` następnie `copy_symlink(from, to, opts)`.

- W przeciwnym razie Zgłoś błąd.

W przeciwnym razie, jeśli `is_regular_file(f)` następnie:

- Jeśli `opts & copy_options::directories_only` nic nie rób.

- W przeciwnym razie, jeśli `opts & copy_options::create_symlinks` następnie `create_symlink(to, from)`.

- W przeciwnym razie, jeśli `opts & copy_options::create_hard_links` następnie `create_hard_link(to, from)`.

- W przeciwnym razie, jeśli `is_directory(f)` następnie `copy_file(from, to`  /  `from.filename(), opts)`.

- W przeciwnym razie `copy_file(from, to, opts)`.

W przeciwnym razie, jeśli `is_directory(f) && (opts & copy_options::recursive || !opts)` następnie:

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

## <a name="copy_file"></a>  copy_file —

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkcje wszystkie możliwie skopiuj plik na *z* do *do* pod kontrolą *zdecyduje*, która jest traktowana jako `copy_options::none` dla przeciążeń, bez *zdecyduje*  parametru. *zdecyduje* zawierają co najwyżej jedno z `skip_existing`, `overwrite_existing`, lub `update_existing`.

Jeśli `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))` następnie raport jako błąd, który plik już istnieje.

W przeciwnym razie, jeśli `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))` następnie podjąć próbę kopiowania, zawartość i atrybuty pliku *z* do pliku *do*. Raport jako błąd, jeśli próba skopiowania zakończy się niepowodzeniem.

Te funkcje zwracają **true** Jeśli kopii jest podejmowana próba zakończy się powodzeniem, w przeciwnym razie **false**.

## <a name="copy_symlink "></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Jeśli `is_directory(from)` wywołania funkcji `create_directory_symlink(from, to)`. W przeciwnym razie wywoływanych przez nią `create_symlink(from, to)`.

## <a name="create_directories"></a>  create_directories —

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Dla nazwy ścieżki, takie jak\/b\/tworzy funkcję c, katalogów i\/b, który może utworzyć katalogu\/b\/c, zgodnie z potrzebami. Zwraca **true** tylko wtedy, gdy rzeczywiście tworzy katalog *pval*.

## <a name="create_directory"></a>  create_directory —

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkcja tworzy katalog *pval* zgodnie z potrzebami. Zwraca wartość true, tylko jeśli faktycznie tworzy katalog *pval*, w którym to przypadku kopiuje uprawnienia z istniejącego pliku *attr*, natomiast przy użyciu `perms::all` dla przeciążeń, bez *attr*  parametru.

## <a name="create_directory_symlink "></a>  create_directory_symlink —

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy link jako Link symboliczny w katalogu *do*.

## <a name="create_hard_link"></a>  create_hard_link —

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy link jako twarde łącze do katalogu lub pliku *do*.

## <a name="create_symlink "></a>  create_symlink —

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy *łącze* jako Link symboliczny do pliku *do*.

## <a name="current_path"></a>  current_path —

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkcje w przypadku braku parametrów *pval* zwraca nazwę ścieżki dla bieżącego katalogu. Pozostałe funkcje ustawiają bieżący katalog *pval*.

## <a name="end"></a>  koniec

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Pierwsza funkcja zwraca `directory_iterator()` i druga funkcja zwraca `recursive_directory_iterator()`

## <a name="equivalent"></a>  równoważne

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Te funkcje zwracają **true** tylko wtedy, gdy *po lewej stronie* i *prawo* wyznaczenia tego samego obiektu systemu plików.

## <a name="exists"></a>  Istnieje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `status_known && stat.type() != file_not_found`. Drugi i trzeci funkcje zwracają `exists(status(pval))`.

## <a name="file_size"></a>  file_size —

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Te funkcje zwracają rozmiar w bajtach pliku określonego przez *pval*, jeśli `exists(pval) && is_regular_file(pval)` i można określić rozmiar pliku. W przeciwnym razie Zgłoś błąd i zwracają `uintmax_t(-1)`.

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca liczbę twardych łączy dla *pval*, lub \-1, jeśli wystąpi błąd.

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkcja zwraca wartość skrótu dla `pval.native()`.

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::block`. Pozostałe funkcje zwracają `is_block_file(status(pval))`.

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::character`. Pozostałe funkcje zwracają `is_character_file(status(pval))`.

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::directory`. Pozostałe funkcje zwracają `is_directory_file(status(pval))`.

## <a name="is_empty"></a>  is_empty —

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Jeśli `is_directory(pval)` wówczas funkcja zwraca `directory_iterator(pval) == directory_iterator()`; w przeciwnym razie zwraca `file_size(pval) == 0`.

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::fifo`. Pozostałe funkcje zwracają `is_fifo(status(pval))`.

## <a name="is_other"></a>  is_other —

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::other`. Pozostałe funkcje zwracają `is_other(status(pval))`.

## <a name="s_regular_file"></a>  is_regular_file —

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::regular`. Pozostałe funkcje zwracają `is_regular_file(status(pval))`.

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::socket`. Pozostałe funkcje zwracają `is_socket(status(pval))`.

## <a name="is_symlink"></a>  is_symlink —

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca `stat.type() == file_type::symlink`. Pozostałe funkcje zwracają `is_symlink(status(pval))`.

## <a name="last_write_time"></a>  last_write_time —

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Pierwsze dwie funkcje zwracają czas ostatniej modyfikacji danych *pval*, lub `file_time_type(-1)` w przypadku wystąpienia błędu. Ostatnie dwie funkcje ustawiają czas ostatniej modyfikacji danych *pval* do *new_time*.

## <a name="permissions"></a>  Uprawnienia

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkcje ustawiają uprawnienia do wyznaczonego przez nazwę ścieżki *pval* do `mask & perms::mask` pod kontrolą `perms & (perms::add_perms | perms::remove_perms)`. *Maska* zawierają co najwyżej jedno z `perms::add_perms` i `perms::remove_perms`.

Jeśli `mask & perms::add_perms` funkcje ustawiają uprawnienia, `status(pval).permissions() | mask & perms::mask`. W przeciwnym razie, jeśli `mask & perms::remove_perms` funkcje ustawiają uprawnienia, `status(pval).permissions() & ~(mask & perms::mask)`. W przeciwnym razie, funkcje ustawiają uprawnienia `mask & perms::mask`.

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Funkcje zgłosić błąd i zwraca `path()` Jeśli `!is_symlink(pval)`. W przeciwnym wypadku te funkcje zwracają obiekt typu `path` zawierającą łącze symboliczne.

## <a name="remove"></a>  Usuń

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Te funkcje zwracają **true** tylko wtedy, gdy `exists(symlink_status(pval))` i plik został pomyślnie usunięty. Link symboliczny jest usunięty, nie pliku, który ją określa.

## <a name="remove_all"></a>  remove_all —

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Jeśli *pval* jest katalogiem, rekursywnie funkcji Usuń wszystkie wpisy w katalogu, a następnie sam wpis. W przeciwnym razie wywołanie funkcji `remove`. Zwracają liczbę wszystkich elementów został pomyślnie usunięty.

## <a name="rename"></a>  Zmień nazwę

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

Zmiana nazwy funkcji *z* do *do*. Link symboliczny jest zmieniona, nie pliku, który ją określa.

## <a name="resize_file"></a>  resize_file —

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkcji zmienia rozmiar pliku tak, aby `file_size(pval) == size`

## <a name="space"></a>  miejsce

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca informacje na temat woluminu wyznaczonym przez *pval*, w strukturze typu `space_info`. Struktura zawiera `uintmax_t(-1)` dla nie można określić dowolną wartość.

## <a name="status"></a>  Stan

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Te funkcje zwracają pathname stan, typ pliku i skojarzone uprawnienia *pval*. Link symboliczny sama nie jest testowana jest, ale wskazuje plik.

## <a name="status_known"></a>  status_known —

```cpp
bool status_known(file_status stat) noexcept;
```

Funkcja zwraca `stat.type() != file_type::none`

## <a name="swap"></a>  swap

```cpp
void swap(path& left, path& right) noexcept;
```

Funkcja wymienia zawartość *po lewej stronie* i *prawo*.

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Te funkcje zwracają pathname stan łącza symbolicznego, typu pliku i skojarzone uprawnienia *pval*. Funkcje zachowują się taka sama jak `status(pval)` z tą różnicą, że Link symboliczny jest testowany, nie plik ustanowi.

## <a name="system_complete"></a>  system_complete —

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Te funkcje zwracają ścieżki, która uwzględnia w razie potrzeby, bieżącego katalogu, które są skojarzone z jego nazwą katalogu głównego. \(Posix, te funkcje zwracają `absolute(pval)`.\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Te funkcje zwracają odpowiednie do przechowywania plików tymczasowych pathname dla katalogu.

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Pierwsza funkcja działa w taki sam jak `path(source)` i drugą funkcję zachowuje się taka sama jak `path(first, last)` z tą różnicą, że wyznaczonego źródła w każdym przypadku jest traktowana jako sekwencję elementów char zakodowanymi w formacie UTF-8, niezależnie od tego, w systemie plików.
