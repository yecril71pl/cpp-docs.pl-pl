---
title: Klasa wartości Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816592"
---
# <a name="platformguid-value-class"></a>Klasa wartości Platform::Guid

Reprezentuje typ [identyfikatora GUID](/previous-versions/cc317743(v%3dmsdn.10)) w systemie środowisko wykonawcze systemu Windows typu.

## <a name="syntax"></a>Składnia

```cpp
public value struct Guid
```

### <a name="members"></a>Elementy członkowskie

`Platform::Guid` ma metody `Equals()`, `GetHashCode()` i `ToString()` pochodne od [klasy platform:: Object](../cppcx/platform-object-class.md)i `GetTypeCode()` metody pochodnej od [klasy platform:: Type](../cppcx/platform-type-class.md). `Platform::Guid` również ma następujących członków.

|Element członkowski|Opis|
|------------|-----------------|
|[Ident](#ctor)|Inicjuje nowe wystąpienie `Platform::Guid`.|
|[operator = =](#operator-equality)|Equals — operator.|
|[operator!=](#operator-inequality)|Operator not Equals.|
|[operator @ no__t-1](#operator-less)|Operator mniejszości.|
|[operator ()](#operator-call)|Konwertuje `Platform::Guid` na `GUID`.|

### <a name="remarks"></a>Uwagi

Aby wygenerować nowy `Platform::Guid`, użyj metody statycznej [Windows:: Foundation:: GuidHelper:: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) .

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd

## <a name="ctor"></a>GUID:: GUID — konstruktory

Inicjuje nowe wystąpienie `Platform::Guid`.

### <a name="syntax"></a>Składnia

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>Parametry

*z*<br/>
Pierwsze 4 bajty `GUID`.

*b*<br/>
Następne 2 bajty `GUID`.

*s*<br/>
Następne 2 bajty `GUID`.

*Wykres*<br/>
Następny bajt `GUID`.

*e*<br/>
Następny bajt `GUID`.

*n*<br/>
Następny bajt `GUID`.

*g*<br/>
Następny bajt `GUID`.

*c*<br/>
Następny bajt `GUID`.

*i*<br/>
Następny bajt `GUID`.

*j*<br/>
Następny bajt `GUID`.

*k*<br/>
Następny bajt `GUID`.

*m*<br/>
@No__t-0 w formie [struktury identyfikatora GUID](/previous-versions/cc317743(v%3dmsdn.10)).

*Azotan*<br/>
Pozostałe 8 bajtów `GUID`.

## <a name="operator-equality"></a>GUID:: operator = = — operator

Porównuje dwa wystąpienia `Platform::Guid` dla równości.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Druga `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Ma wartość true, jeśli dwa wystąpienia `Platform::Guid` są równe.

### <a name="remarks"></a>Uwagi

Preferuj użycie operatora `==` zamiast metody statycznej [Windows:: Foundation:: GuidHelper:: Equals](/uwp/api/windows.foundation.guidhelper.equals) .

## <a name="operator-inequality"></a>GUID:: operator! = — operator

Porównuje dwa wystąpienia `Platform::Guid` pod kątem nierówności.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Druga `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Ma wartość true, jeśli dwa wystąpienia `Platform::Guid` nie są równe.

## <a name="operator-less"></a>GUID:: operator @ no__t-1 — operator

Porównuje dwa wystąpienia `Platform::Guid` na potrzeby porządkowania.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Druga `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli *guid1* jest uporządkowana przed *guid2*. Porządkowanie jest leksykograficznych po przeprowadzeniu każdej `Platform::Guid`, tak jakby była tablicą 4 32-bitowych wartości bez znaku. Nie jest to kolejność używana przez SQL Server lub .NET Framework, ani nie jest taka sama jak lexicographical porządkowanie według ciągu.

Ten operator jest dostarczany tak, aby obiekty `Guid` mogły być łatwiej wykorzystane przez bibliotekę C++ standardową.

## <a name="operator-call"></a>GUID:: operator () — operator

Niejawnie konwertuje `Platform::Guid` na [strukturę GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="syntax"></a>Składnia

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Wartość zwracana

[Struktura identyfikatora GUID](/previous-versions/cc317743(v%3dmsdn.10)).

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
