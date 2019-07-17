---
title: filesystem_error — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: c3dbfc080f0a1494950016f42189d932be05b0f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240743"
---
# <a name="filesystemerror-class"></a>filesystem_error — klasa

Klasa bazowa dla wszystkich wyjątków, które są zgłaszane do zgłaszania przepełnienie system niskiego poziomu.

## <a name="syntax"></a>Składnia

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Uwagi

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych zgłosić błąd w \<filesystem > funkcji. Przechowuje obiekt typu `string`, co jest nazywane `mymesg` tutaj na potrzeby specyfikacji. Przechowuje dwa obiekty typu `path`, co jest nazywane `mypval1` i `mypval2`.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[filesystem_error](#filesystem_error)|Konstruuje `filesystem_error` wiadomości.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[path1](#path1)|Zwraca `mypval1`|
|[path2](#path2)|Zwraca `mypval2`|
|[Co to](#what)|Zwraca wskaźnik do `NTBS`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error

Pierwszy Konstruktor konstruuje komunikat z *what_arg* i *we*. Drugi Konstruktor tworzy komunikat z *pval1*, którą przechowuje w `mypval1`. Trzeci Konstruktor konstruuje również komunikat z *pval1*, przechowywanego w `mypval1`i z *pval2*, którą przechowuje w `mypval2`.

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

### <a name="parameters"></a>Parametry

*what_arg*\
Określony komunikat.

*we*\
Określony kod błędu.

*mypval1*\
Dodatkowo parametr określony komunikat.

*mypval2*\
Dodatkowo komunikat określony parametr.

## <a name="path1"></a> ścieżka1

Funkcja elementu członkowskiego zwraca `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> ścieżka2

Funkcja elementu członkowskiego zwraca `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> Co to

Element członkowski funkcji zwraca wskaźnik do `NTBS`, najlepiej jest złożone z `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, i `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
