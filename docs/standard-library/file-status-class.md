---
title: file_status, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
dev_langs:
- C++
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc955aa615deadb6e99cfdbb8d72513cc93ced8
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314563"
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
|[Typ](#type)|Pobiera lub ustawia `file_type`.|
|[Uprawnienia](#permissions)|Pobiera lub ustawia uprawnienia do pliku.|

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
[\<FileSystem >](../standard-library/filesystem.md)<br/>
