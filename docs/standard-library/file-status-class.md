---
title: file_status — Klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 81ce4ecc1673087db8e985f94e297798dd712a6e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160020"
---
# <a name="filestatus-class"></a>file_status — Klasa

Opakowuje [typ_pliku](../standard-library/filesystem-enumerations.md#file_type) i plik [perms](../standard-library/filesystem-enumerations.md#perms).

## <a name="syntax"></a>Składnia

```cpp
class file_status;
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[file_status](#file_status)|Tworzy otokę dla [typ_pliku](../standard-library/filesystem-enumerations.md#file_type) i plik [perms](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[type](#type)|Pobiera lub ustawia `file_type`.|
|[uprawnienia](#permissions)|Pobiera lub ustawia uprawnienia do pliku.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_as)|Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem, std::experimental::filesystem

## <a name="file_status"></a> file_status::file_status —

Tworzy otokę dla [typ_pliku](../standard-library/filesystem-enumerations.md#file_type) i plik [perms](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Parametry

*ftype*<br/>
Określony `file_type`, wartość domyślna to `file_type::none`.

*Maska*<br/>
Określony plik `perms`, wartość domyślna to `perms::unknown`.

*file_status*<br/>
Przechowywany obiekt.

## <a name="op_as"></a> file_status::operator =

Operatory przypisania domyślne elementów członkowskich zachowują się zgodnie z oczekiwaniami.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Parametry

*file_status*<br/>
[File_status](../standard-library/file-status-class.md) są kopiowane do `file_status`.

## <a name="type"></a> Typ

Pobiera lub ustawia `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Parametry

*ftype*<br/>
Określony `file_type`.

## <a name="permissions"></a> Uprawnienia

Pobiera lub ustawia uprawnienia do pliku.

Użyj metody ustawiającej, aby wyświetlić plik `readonly` lub usuń `readonly` atrybutu.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Parametry

*Maska*<br/>
Określony `perms`.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[path, klasa](../standard-library/path-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
