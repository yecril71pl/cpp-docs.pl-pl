---
title: filesystem_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
dev_langs:
- C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1acf34f8478bc075b53780f1e48df125c22608b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845495"
---
# <a name="filesystemerror-class"></a>filesystem_error — klasa

Klasa podstawowa dla wszystkich wyjątków, które są zgłaszane do zgłaszania przepełnienie niskiego poziomu systemu.

## <a name="syntax"></a>Składnia

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Uwagi

Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych na zgłaszanie błędu w \<filesystem > funkcje. Przechowuje obiekt typu String, nazywany mymesg tutaj na potrzeby specyfikacji. Przechowuje także dwa obiekty typu ścieżki, nazywanych mypval1 i mypval2.

## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error —

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

Pierwszy konstruktora tworzy komunikatu z what_arg i WE. Drugi Konstruktor tworzy komunikatu z pval1, które są przechowywane w mypval1. Trzeci konstruktora tworzy komunikatu z pval1, który jest przechowywany w mypval1, i pval2, które są przechowywane w mypval2.

## <a name="filesystemerrorpath1"></a>filesystem_error::path1

```cpp
const path& path1() const noexcept;
```

Funkcja członkowska zwraca mypval1

## <a name="filesystemerrorpath2"></a>filesystem_error::path2

```cpp
const path& path2() const noexcept;
```

Funkcja członkowska zwraca mypval2

## <a name="filesystemerrorwhat"></a>filesystem_error::What

```cpp
const char *what() const noexcept;
```

Funkcja członkowska zwraca wskaźnik do NTBS najlepiej składa się z runtime_error::what(), system_error::what() mymesg, mypval1.native_string() i mypval2.native_string().

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error, klasa](../standard-library/system-error-class.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[\<wyjątku >](../standard-library/exception.md)<br/>
