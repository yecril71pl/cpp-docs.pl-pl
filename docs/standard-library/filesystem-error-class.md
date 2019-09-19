---
title: filesystem_error — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127199"
---
# <a name="filesystem_error-class"></a>filesystem_error — klasa

Klasa bazowa dla wszystkich wyjątków, które są zgłaszane do zgłaszania przepełnienia systemu niskiego poziomu.

## <a name="syntax"></a>Składnia

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Uwagi

Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych w celu zgłaszania błędu w \<funkcjach > systemu plików. Zapisuje obiekt typu `string`, o nazwie `mymesg` w tym miejscu do celów specyfikacji. Przechowuje również dwa obiekty typu `path`, nazywane `mypval1` i `mypval2`.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[filesystem_error](#filesystem_error)|`filesystem_error` Tworzy komunikat.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[path1](#path1)|Typu`mypval1`|
|[path2](#path2)|Typu`mypval2`|
|[Whatman](#what)|Zwraca wskaźnik do elementu `NTBS`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="filesystem_error"></a>filesystem_error

Pierwszy Konstruktor konstruuje swój komunikat z *what_arg* i *we*. Drugi Konstruktor konstruuje również swój komunikat z *Pval1*, który przechowuje w `mypval1`. Trzeci Konstruktor konstruuje również swój komunikat z *Pval1*, który jest przechowywany w `mypval1`, i z *Pval2*, który przechowuje w `mypval2`.

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

*udziela*\
Określony kod błędu.

*mypval1*\
Dokładniejszy określony parametr komunikatu.

*mypval2*\
Dokładniejszy określony parametr komunikatu.

## <a name="path1"></a>path1

Funkcja członkowska zwraca`mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>path2

Funkcja członkowska zwraca`mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>Whatman

Funkcja członkowska zwraca `NTBS`wskaźnik do, najlepiej składający się z `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, i. `mypval2.native_string()`

```cpp
const char *what() const noexcept;
```
