---
title: directory_entry — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458956"
---
# <a name="directoryentry-class"></a>directory_entry — klasa

Opisuje obiekt, który jest zwracany przez `*X`, gdzie *X* to [directory_iterator](../standard-library/directory-iterator-class.md) lub [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_entry;
```

## <a name="remarks"></a>Uwagi

Klasa przechowuje obiekt typu [Path](../standard-library/path-class.md). Składowa `path` może być wystąpieniem [klasy Path](../standard-library/path-class.md) lub typu, który pochodzi od `path`. Przechowuje również dwie wartości [file_type](../standard-library/filesystem-enumerations.md#file_type) ; taki, który reprezentuje informacje o stanie przechowywanej nazwy pliku, oraz drugi, który reprezentuje informacje o stanie łącza symbolicznego nazwy pliku.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[directory_entry](#directory_entry)|Konstruktory domyślne zachowują się zgodnie z oczekiwaniami. Czwarty Konstruktor inicjuje `mypath` się *Pval*, `mystat` *stat_arg*i `mysymstat` *symstat_arg*.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ponownie](#assign)|Funkcja członkowska przypisuje *Pval* `mypath`do, *stat* do `mystat`i *symstat* do `mysymstat`.|
|[Ścieżka](#path)|Funkcja członkowska zwraca `mypath`wartość.|
|[replace_filename](#replace_filename)|Funkcja członkowska zastępuje `mypath` atrybutem  /  `mystat`  `mysymstat`   Pval, with stat_arg i with symstat_arg `mypath.parent_path()`|
|[status](#status)|Obie funkcje członkowskie zwracają `mystat` prawdopodobnie najpierw zmienione.|
|[symlink_status](#symlink_status)|Obie funkcje członkowskie zwracają `mysymstat` prawdopodobnie najpierw zmienione.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zamienia elementy listy na kopię innej listy.|
|[operator=](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca `mypath == right.mypath`wartość.|
|[< operatora](#op_lt)|Zwraca `mypath < right.mypath`wartość.|
|[< operatora =](#op_lteq)|Zwraca `!(right < *this)`wartość.|
|[operator>](#op_gt)|Zwraca `right < *this`wartość.|
|[operator>=](#op_gteq)|Zwraca `!(*this < right)`wartość.|
|[operator const path_type &](#path_type)|Zwraca `mypath`wartość.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalny/system plików&gt;

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="assign"></a>ponownie

Funkcja członkowska przypisuje *Pval* `mypath`do, *stat_arg* do `mystat`i *symstat_arg* do `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka nazwy przechowywanego pliku.

*stat_arg*\
Stan nazwy przechowywanego pliku.

*symstat_arg*\
Stan linku symbolicznego nazwy przechowywanego pliku.

## <a name="directory_entry"></a>directory_entry

Konstruktory domyślne zachowują się zgodnie z oczekiwaniami. Czwarty Konstruktor inicjuje `mypath` się *Pval*, `mystat` *stat_arg*i `mysymstat` *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka nazwy przechowywanego pliku.

*stat_arg*\
Stan nazwy przechowywanego pliku.

*symstat_arg*\
Stan linku symbolicznego nazwy przechowywanego pliku.

## <a name="op_neq"></a>operator! =

Funkcja członkowska zwraca `!(*this == right)`wartość.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="op_as"></a>operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) kopiowany do `directory_entry`.

## <a name="op_eq"></a>operator = =

Funkcja członkowska zwraca `mypath == right.mypath`wartość.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="op_lt"></a>zakład&lt;

Funkcja członkowska zwraca `mypath < right.mypath`wartość.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="op_lteq"></a>zakład&lt;=

Funkcja członkowska zwraca `!(right < *this)`wartość.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="op_gt"></a>zakład&gt;

Funkcja członkowska zwraca `right < *this`wartość.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="op_gteq"></a>zakład&gt;=

Funkcja członkowska zwraca `!(*this < right)`wartość.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_entry](../standard-library/directory-entry-class.md) jest porównywany `directory_entry`z.

## <a name="path_type"></a>operator const path_type &

Operator elementu członkowskiego `mypath`zwraca.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>ścieżka

Funkcja członkowska zwraca `mypath`wartość.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

Funkcja członkowska zastępuje `mypath` atrybutem  /  `mystat`  `mysymstat`   Pval, with stat_arg i with symstat_arg `mypath.parent_path()`

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka nazwy przechowywanego pliku.

*stat_arg*\
Stan nazwy przechowywanego pliku.

*symstat_arg*\
Stan linku symbolicznego nazwy przechowywanego pliku.

## <a name="status"></a>Stany

Obie funkcje członkowskie zwracają `mystat` prawdopodobnie najpierw zmienione w następujący sposób:

1. Jeśli `status_known(mystat)` nie, nic nie rób.

1. `!status_known(mysymstat) && !is_symlink(mysymstat)` W`mystat = mysymstat`przeciwnym razie.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*udziela*\
Kod błędu stanu.

## <a name="symlink_status"></a>symlink_status

Obie funkcje członkowskie zwracają `mysymstat` prawdopodobnie najpierw zmienione w następujący sposób: Jeśli `status_known(mysymstat)` nie, nic nie rób. W przeciwnym razie. `mysymstat = symlink_status(mypval)`

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*udziela*\
Kod błędu stanu.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
