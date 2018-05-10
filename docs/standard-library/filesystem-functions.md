---
title: '&lt;System plików&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: bfe07904a8eec87fb18441b92096d8ba6b72e4e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltfilesystemgt-functions"></a>&lt;System plików&gt; funkcji

Bez tych funkcji w [ \<filesystem >](../standard-library/filesystem.md) nagłówka wykonywanie operacji modyfikacji i zapytań na ścieżki, plików, łączy symbolicznych, katalogów i woluminów. Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).
||||
|-|-|-|
|[absolute](#absolute)|[begin](#begin)|[Canonical](#canonical)|
|[Kopiuj](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories —](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[Koniec](#end)|[equivalent](#equivalent)|[istnieje](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[Uprawnienia](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[Zmień nazwę](#rename)|
|[resize_file](#resize_file)|[Miejsca](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name=""></a>  <a name="absolute"></a> Bezwzględne

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkcja zwraca nazwę ścieżki bezwzględne odpowiadający `pval` względem nazwy ścieżki `base`:

1. Jeśli pval.has_root_name() & & pval.has_root_directory() funkcja zwraca pval.

1. Jeśli pval.has_root_name() & &! pval.has_root_directory() funkcja zwraca pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path().

1. Jeśli! pval.has_root_name() & & pval.has_root_directory() funkcja zwraca absolute(base).root_name() / pval.

1. Jeśli! pval.has_root_name() & &! pval.has_root_directory() funkcja zwraca absolute(base) / pval.

## <a name="begin"></a>  Rozpocznij

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obie funkcje zwracają `iter`.

## <a name="canonical"></a>  Canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Wszystkie funkcje stanowią pabs ścieżki = bezwzględną (pval, podstawowe) (lub pabs = absolute(pval) dla przeciążenia z żadnego parametru podstawowej), następnie zmniejszyć forma kanoniczna kolejno następujące czynności:

1. Każdy składnik ścieżki X dla których is_symlink(X) ma wartość true został zastąpiony przez read_symlink(X).

1. Każdy składnik ścieżki. (kropka jest bieżącym katalogiem wyznaczane przez poprzednie składniki ścieżki) zostaną usunięte.

1. Wszystkie pary składników ścieżki X /... (kropka kropka jest wyznaczane przez poprzednie składniki ścieżka katalogu nadrzędnego) zostaną usunięte.

Następnie funkcja zwraca pabs.

## <a name="copy"></a>  Kopiuj

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkcje wszystkie prawdopodobnie skopiować lub połączyć jednego lub więcej plików w `from` do `to` pod kontrolą `opts`, która jest traktowana jako copy_options::none dla przeciążenia bez `opts` parametru. `opts` zawiera co najmniej jeden z:

- skip_existing, overwrite_existing lub update_existing

- copy_symlinks lub skip_symlinks

- directories_only, create_symlinks lub create_hard_links

Funkcje najpierw ustalić f wartości file_status — `from` i t dla `to`:

- Jeśli zdecyduje & (copy_options::create_symlinks &#124; copy_options::skip_symlinks), przez wywołanie symlink_status —

- w przeciwnym razie, wywołując stanu

- W przeciwnym razie Zgłoś błąd.

Jeśli! exists(f) &#124; &#124; równoważne (f, t) &#124; &#124; is_other(f) &#124; &#124; is_other(t) &#124; &#124; is_directory(f) & & is_regular_file(t), następnie zgłaszały błąd (i nic nie rób else).

W przeciwnym razie, jeśli następnie is_symlink(f):

- Jeśli opcje & copy_options::skip_symlinks następnie nic nie rób.

- W przeciwnym razie, jeśli! exists(t) & & Opcje & copy_options::copy_symlinks następnie copy_symlink — (, aby, zdecyduje).

- W przeciwnym razie Zgłoś błąd.

W przeciwnym razie, jeśli następnie is_regular_file(f):

- Jeśli zdecyduje & copy_options::directories_only następnie nic nie rób.

- W przeciwnym razie, jeśli zdecyduje & copy_options::create_symlinks następnie create_symlink(to, from).

- W przeciwnym razie, jeśli zdecyduje & copy_options::create_hard_links następnie create_hard_link(to, from).

- W przeciwnym razie, jeśli is_directory(f), a następnie copy_file — (od pozycji/zdecyduje from.filename(),).

- Copy_file — w przeciwnym razie (, aby, zdecyduje).

W przeciwnym razie, jeśli is_directory(f) & & (zdecyduje & copy_options::recursive &#124; &#124; ! zdecyduje) następnie:

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

## <a name="opy_file"></a>  copy_file —

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkcje wszystkie prawdopodobnie skopiuj plik na `from` do `to` pod kontrolą `opts`, która jest traktowana jako copy_options::none dla przeciążenia bez `opts` parametru. `opts` zawiera co najmniej jeden skip_existing, overwrite_existing lub update_existing.

Jeśli istnieje\(do\) && \!\(zdecyduje & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\) \) następnie raportu, ponieważ wystąpił błąd, że plik już istnieje.

W przeciwnym razie, jeśli \!istnieje\(do\) &#124; &#124; zdecyduje & copy_options::overwrite_existing &#124; &#124; zdecyduje & copy_options::update_existing & & last_write_time —\(do \) \< last_write_time —\(z\) &#124; &#124; \! \(zdecyduje & \(copy_options::skip_existing &#124; copy_options::o verwrite_existing &#124; copy_options:update_existing\) \) następnie próba skopiowania zawartości i atrybuty pliku do pliku. Raport jako błąd, jeśli próba skopiowania nie powiedzie się.

Funkcje zwraca wartość true Jeśli kopia zostanie podjęta i zakończy się powodzeniem, w przeciwnym razie wartość false.

## <a name="copy_symlink "></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Jeśli is_directory\(z\) create_directory_symlink — wywołuje funkcję\(z pozycji\). W przeciwnym razie wywołuje create_symlink —\(z pozycji\).

## <a name="create_directories"></a>  create_directories —

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Dla pathname, takich jak\/b\/c funkcja ta umożliwia tworzenie katalogów i\/b, który można utworzyć katalogu\/b\/c zgodnie z potrzebami. Zwraca wartość true, tylko jeśli faktycznie tworzy katalog `pval`.

## <a name="create_directory"></a>  create_directory —

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkcja tworzy katalog `pval` zgodnie z potrzebami. Zwraca wartość true, tylko jeśli faktycznie tworzy katalog `pval`, w którym to przypadku uprawnienia są kopiowane z istniejącego pliku `attr`, lub używa perms::all przeciążenia bez `attr` parametru.

## <a name="create_directory_symlink "></a>  create_directory_symlink —

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy łącze jako łącza symbolicznego do katalogu `to`.

## <a name="create_hard_link"></a>  create_hard_link —

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja tworzy łącze jako twarde łącze do pliku lub katalogu `to`.

## <a name="create_symlink "></a>  create_symlink —

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkcja ta umożliwia tworzenie `link` jako łącza symbolicznego do pliku `to`.

## <a name="current_path"></a>  current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkcje z żadnego parametru `pval` zwraca nazwę ścieżki dla bieżącego katalogu. Pozostałe funkcje ustawić bieżącego katalogu `pval`.

## <a name="end"></a>  Koniec

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Directory_iterator — zwraca pierwszej funkcji\( \) i drugi funkcja zwraca recursive_directory_iterator —\(\)

## <a name="equivalent"></a>  Odpowiednik

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkcje zwracają wartość true tylko wtedy, gdy `left` i `right` wyznaczenia tego samego obiektu systemu plików.

## <a name="exists"></a>  istnieje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Status_known — zwraca pierwszej funkcji & & stat.type\( \) \! \= file_not_found. Drugi i trzeci zwracają istnieje\(stan\(pval\)\).

## <a name="file_size"></a>  file_size —

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Zwracają rozmiar w bajtach pliku określonego przez `pval`, jeśli istnieje\(pval\) & & is_regular_file\(pval\) i można ustalić rozmiaru pliku. W przeciwnym razie zgłaszają uintmax_t błąd i przywracać\(\-1\).

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca liczbę twarde linki dla `pval`, lub \-1 w przypadku wystąpienia błędu.

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkcja zwraca wartość skrótu dla pval.native\(\).

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::block. Pozostałe zwracają is_block_file\(stan\(pval\)\).

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::character. Pozostałe zwracają is_character_file\(stan\(pval\)\).

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::directory. Pozostałe zwracają is_directory_file\(stan\(pval\)\).

## <a name="is_empty"></a>  is_empty —

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Jeśli is_directory\(pval\) , a następnie funkcja zwraca directory_iterator —\(pval\) \= \= directory_iterator —\(\); w przeciwnym razie zwraca wartość file_ rozmiar\(pval\) \= \= 0.

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::fifo. Pozostałe zwracają is_fifo\(stan\(pval\)\).

## <a name="is_other"></a>  is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::other. Pozostałe zwracają is_other\(stan\(pval\)\).

## <a name="s_regular_file"></a>  is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::regular. Pozostałe zwracają is_regular_file\(stan\(pval\)\).

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::socket. Pozostałe zwracają is_socket\(stan\(pval\)\).

## <a name="is_symlink"></a>  is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Pierwsza funkcja zwraca stat.type\( \) \= \= file_type::symlink. Pozostałe zwracają is_symlink\(stan\(pval\)\).

## <a name="last_write_time"></a>  last_write_time —

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Pierwsze dwie funkcje zwracają czas ostatniej modyfikacji danych `pval`, lub file_time_type\(\-1\) w przypadku wystąpienia błędu. Ostatnie dwa funkcje ustawić czas ostatniej modyfikacji danych `pval` do new_time.

## <a name="permissions"></a>  Uprawnienia

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkcje ustawić uprawnień dla nazwy ścieżki wskazywany przez `pval` maska & perms::mask pod kontrolą perms & \(perms::add_perms &#124; perms::remove_perms\). Maska zawiera co najmniej jeden perms::add_perms i perms::remove_perms.

Jeśli maska & perms::add_perms funkcji Ustaw uprawnienia do stanu\(pval\).permissions\( \) &#124; maska & perms::mask. W przeciwnym razie, jeśli maski & perms::remove_perms funkcji Ustaw uprawnienia do stanu\(pval\).permissions\( \) & ~\(maska & perms::mask\). W przeciwnym razie funkcje Ustaw uprawnienia do maski & perms::mask.

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Funkcje Zgłoś błąd i zwrot ścieżkę\( \) Jeśli \!is_symlink\(pval\). W przeciwnym razie zwracają obiekt typu `path` zawierający łącza symbolicznego.

## <a name="remove"></a>  Usuń

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Zwracają wartość true tylko wtedy, gdy istnieje\(symlink_status —\(pval\) \) i plik został pomyślnie usunięty. Utwórz Link symboliczny jest usunięty, nie pliku, który wyznacza go.

## <a name="remove_all"></a>  remove_all —

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Jeśli `pval` jest katalogiem, rekursywnie funkcje usunąć wszystkich wpisów w katalogu, a następnie się wpis. Funkcje wywołania w przeciwnym razie Usuń. Zwracają liczbę wszystkie elementy usunięte pomyślnie.

## <a name="rename"></a>  Zmień nazwę

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

Zmień nazwę funkcji `from` do `to`. Utwórz Link symboliczny jest zmieniona jego nazwa, nie pliku, który wyznacza go.

## <a name="resize_file"></a>  resize_file —

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkcji zmiany rozmiaru pliku takie tego file_size —\(pval\) \= \= rozmiaru

## <a name="space"></a>  Miejsca

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkcja zwraca informacje na temat woluminu wskazywany przez `pval`, w strukturze typu `space_info`. Struktura zawiera uintmax_t\(\-1\) dla żadnej wartości, która nie może być określony.

## <a name="status"></a>  Stan

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Zwracają stan pathname, typu pliku i uprawnienia związane z `pval`. Łącza symbolicznego jest nie przetestowane, ale plik wyznacza.

## <a name="status_known"></a>  status_known —

```cpp
bool status_known(file_status stat) noexcept;
```

Funkcja zwraca stat.type\( \) \! \= file_type::none

## <a name="swap"></a>  Swap

```cpp
void swap(path& left, path& right) noexcept;
```

Funkcja wymiany zawartość `left` i `right`.

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Zwracają pathname stan łącza symbolicznego, typu pliku i uprawnienia związane z `pval`. Funkcje działają tak samo jak stan\(pval\) z tą różnicą, że łącza symbolicznego jest przetestowane, nie pliku ustanowi.

## <a name="system_complete"></a>  system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Zwracają która uwzględnia odpowiednio do potrzeb bieżący katalog skojarzony z jego nazwę głównej ścieżki. \(Dla Posix, funkcje zwracają wartość bezwzględna\(pval\).\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkcje zwraca nazwę ścieżki dla katalogu odpowiednie do przechowywania plików tymczasowych.

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Pierwsza funkcja działa tak samo jak path(source) i drugi funkcja działa tak samo jak ścieżka (imię, nazwisko) z tą różnicą, że wyznaczonego źródła w każdym przypadku jest traktowana jako sekwencję elementów char zakodowane jako UTF-8, niezależnie od tego, w systemie plików.


