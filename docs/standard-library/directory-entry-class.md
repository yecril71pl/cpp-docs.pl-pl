---
title: directory_entry — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.workload:
- cplusplus
ms.openlocfilehash: ba3dc5588cb035cb754ba43a6eeccb37b7ec0b79
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="directoryentry-class"></a>directory_entry — klasa

Opisuje obiekt, który jest zwracany przez `*X`, gdzie *X* jest [directory_iterator —](../standard-library/directory-iterator-class.md) lub [recursive_directory_iterator —](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_entry;
```

## <a name="remarks"></a>Uwagi

Klasa przechowuje obiekt typu [ścieżki](../standard-library/path-class.md). Zapisana `path` można instancji [ścieżki klasy](../standard-library/path-class.md) lub typu, który jest pochodną `path`. Przechowuje także dwa [typ_pliku](../standard-library/filesystem-enumerations.md#file_type) wartości; odpowiadającą określane o stanie nazwę zapisanego pliku, a druga reprezentuje, co będzie wiadomo o stan łącza symbolicznego nazwy pliku.

Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="assign"></a>Przypisz

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

Funkcja członkowska przypisuje pval mypath, stat do mystat i symstat do mysymstat.

## <a name="directoryentry"></a>directory_entry —

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

Konstruktory domyślne działają zgodnie z oczekiwaniami. Czwarty Konstruktor inicjuje mypath do pval, mystat do stat_arg i mysymstat do symstat_arg.

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca! (* to == prawej strony).

## <a name="operator"></a>operator=

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

Operatory przypisania domyślnego elementu członkowskiego działają zgodnie z oczekiwaniami.

## <a name="operator"></a>operator==

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca mypath == right.mypath.

## <a name="operatorlt"></a>Operator&lt;

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca mypath &lt; right.mypath.

## <a name="operatorlt"></a>Operator&lt;=

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca! (prawo \< * to).

## <a name="operatorgt"></a>Operator&gt;

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca prawo \< * to.

## <a name="operatorgt"></a>Operator&gt;=

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

Funkcja członkowska zwraca! (* to \< prawo).

## <a name="operator-const-pathtype"></a>Operator const path_type &

```cpp
operator const std::experimental::filesystem::path&() const;
```

Operator członkowski zwraca mypath.

## <a name="path"></a>ścieżka

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

Funkcja członkowska zwraca mypath.

## <a name="replacefilename"></a>replace_filename

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

Funkcja członkowska zastępuje mypath mypath.parent_path() / pval, mystat z stat_arg i mysymstat z symstat_arg

## <a name="status"></a>stan

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

Zarówno członek zwracają mystat prawdopodobnie najpierw zmienić w następujący sposób:

1. Jeśli status_known(mystat) następnie nic nie rób.

1. W przeciwnym razie, jeśli! status_known(mysymstat) & &! is_symlink(mysymstat), a następnie mystat = mysymstat.

## <a name="symlinkstatus"></a>symlink_status

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

Obie funkcje Członkowskie zwracać mysymstat prawdopodobnie najpierw zmienić jako status_known(mysymstat) w następujący sposób: Jeśli, a następnie nic nie rób. W przeciwnym razie mysymstat = symlink_status(mypval).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalne/systemu plików&gt;

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
