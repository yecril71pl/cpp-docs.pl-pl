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
ms.openlocfilehash: c1b68aefd44d8f0ac60c36307dee93333d801bb9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342975"
---
# <a name="directoryentry-class"></a>directory_entry — klasa

Opisuje obiekt, który jest zwracany przez `*X`, gdzie *X* jest [directory_iterator](../standard-library/directory-iterator-class.md) lub [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_entry;
```

## <a name="remarks"></a>Uwagi

Klasa przechowuje obiekt typu [ścieżki](../standard-library/path-class.md). Przechowywany `path` może być wystąpieniem elementu [path — klasa](../standard-library/path-class.md) lub typu, który jest tworzony na podstawie `path`. Przechowuje także dwa [typ_pliku](../standard-library/filesystem-enumerations.md#file_type) wartości; taki, który reprezentuje, co jest znane o stanie nazwy pliku przechowywanego, a druga reprezentujący, co jest znane o stanie łącza symbolicznego, nazwy pliku.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[directory_entry](#directory_entry)|Domyślne konstruktory zachowują się zgodnie z oczekiwaniami. Czwarty Konstruktor inicjuje `mypath` do *pval*, `mystat` do *stat_arg*, i `mysymstat` do *symstat_arg*.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Funkcja elementu członkowskiego przypisuje *pval* do `mypath`, *stat* do `mystat`, i *symstat* do `mysymstat`.|
|[Ścieżka](#path)|Funkcja elementu członkowskiego zwraca `mypath`.|
|[replace_filename](#replace_filename)|Funkcji składowej zastępuje `mypath` z `mypath.parent_path()`  /  *pval*, `mystat` z *stat_arg*, i `mysymstat` z *symstat_arg*|
|[status](#status)|Obie funkcje Członkowskie zwracają `mystat` prawdopodobnie najpierw zmienić.|
|[symlink_status](#symlink_status)|Obie funkcje Członkowskie zwracają `mysymstat` prawdopodobnie najpierw zmienić.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zamienia elementy listy kopię innej listy.|
|[operator=](#op_as)|Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca `mypath == right.mypath`.|
|[Operator <](#op_lt)|Zwraca `mypath < right.mypath`.|
|[Operator < =](#op_lteq)|Zwraca `!(right < *this)`.|
|[operator>](#op_gt)|Zwraca `right < *this`.|
|[operator>=](#op_gteq)|Zwraca `!(*this < right)`.|
|[Operator const path_type &](#path_type)|Zwraca `mypath`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalne/systemu plików&gt;

**Namespace:** std::experimental::filesystem

## <a name="assign"></a> Przypisz

Funkcja elementu członkowskiego przypisuje *pval* do `mypath`, *stat_arg* do `mystat`, i *symstat_arg* do `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka Nazwa pliku przechowywanego.

*stat_arg*<br/>
Stan nazwy pliku przechowywanego.

*symstat_arg*<br/>
Stan łącza symbolicznego nazwy pliku przechowywanego.

## <a name="directory_entry"></a> directory_entry

Domyślne konstruktory zachowują się zgodnie z oczekiwaniami. Czwarty Konstruktor inicjuje `mypath` do *pval*, `mystat` do *stat_arg*, i `mysymstat` do *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka Nazwa pliku przechowywanego.

*stat_arg*<br/>
Stan nazwy pliku przechowywanego.

*symstat_arg*<br/>
Stan łącza symbolicznego nazwy pliku przechowywanego.

## <a name="op_neq"></a> operator! =

Funkcja elementu członkowskiego zwraca `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="op_as"></a> operator =

Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) są kopiowane do `directory_entry`.

## <a name="op_eq"></a> operator ==

Funkcja elementu członkowskiego zwraca `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="op_lt"></a> Operator&lt;

Funkcja elementu członkowskiego zwraca `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="op_lteq"></a> Operator&lt;=

Funkcja elementu członkowskiego zwraca `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="op_gt"></a> Operator&gt;

Funkcja elementu członkowskiego zwraca `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="op_gteq"></a> Operator&gt;=

Funkcja elementu członkowskiego zwraca `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md) którą jest porównywany `directory_entry`.

## <a name="path_type"></a> Operator const path_type &

Operator elementu członkowskiego zwraca `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> Ścieżka

Funkcja elementu członkowskiego zwraca `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

Funkcji składowej zastępuje `mypath` z `mypath.parent_path()`  /  *pval*, `mystat` z *stat_arg*, i `mysymstat` z *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Ścieżka Nazwa pliku przechowywanego.

*stat_arg*<br/>
Stan nazwy pliku przechowywanego.

*symstat_arg*<br/>
Stan łącza symbolicznego nazwy pliku przechowywanego.

## <a name="status"></a> Stan

Obie funkcje Członkowskie zwracają `mystat` prawdopodobnie najpierw zmienić w następujący sposób:

1. Jeśli `status_known(mystat)` nic nie rób.

1. W przeciwnym razie, jeśli `!status_known(mysymstat) && !is_symlink(mysymstat)` następnie `mystat = mysymstat`.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*ec*<br/>
Kod stanu błędu.

## <a name="symlink_status"></a> symlink_status —

Obie funkcje Członkowskie zwracają `mysymstat` prawdopodobnie najpierw zmienić w następujący sposób: Jeśli `status_known(mysymstat)` nic nie rób. W przeciwnym razie `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*ec*<br/>
Kod stanu błędu.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
