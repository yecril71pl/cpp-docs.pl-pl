---
title: Klasa wartości Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 8d6c71028e4f93064c7b4df978678b5f7c26d6bc
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504531"
---
# <a name="platformguid-value-class"></a>Klasa wartości Platform::Guid

Reprezentuje [GUID](/previous-versions/aa373931\(v=vs.80\)) typu w systemie typów środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```cpp
public value struct Guid
```

### <a name="members"></a>Elementy członkowskie

`Platform::Guid` ma `Equals()`, `GetHashCode()`, i `ToString()` metody pochodną [Platform::Object, klasa](../cppcx/platform-object-class.md)i `GetTypeCode()` metoda pochodną [Platform::Type, klasa](../cppcx/platform-type-class.md). `Platform::Guid` ma również następujące elementy członkowskie.

|Element członkowski|Opis|
|------------|-----------------|
|[Identyfikator GUID](#ctor)|Inicjuje nowe wystąpienie klasy `Platform::Guid`.|
|[operator==](#operator-equality)|Operator równości.|
|[operator!=](#operator-inequality)|Nie równa się operatora.|
|[Operator&lt;](#operator-less)|Operator mniejszości.|
|[operator()](#operator-call)|Konwertuje `Platform::Guid` do `GUID`.|

### <a name="remarks"></a>Uwagi

Aby wygenerować nowy `Platform::Guid`, użyj [Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) metody statycznej.

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="ctor"></a> Konstruktory GUID::GUID

Inicjuje nowe wystąpienie klasy `Platform::Guid`.

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

*a*<br/>
Pierwsze 4 bajty `GUID`.

*b*<br/>
Następne 2 bajty obiektu `GUID`.

*c*<br/>
Następne 2 bajty obiektu `GUID`.

*d*<br/>
Następny bajt obiektu `GUID`.

*e*<br/>
Następny bajt obiektu `GUID`.

*f*<br/>
Następny bajt obiektu `GUID`.

*g*<br/>
Następny bajt obiektu `GUID`.

*h*<br/>
Następny bajt obiektu `GUID`.

*i*<br/>
Następny bajt obiektu `GUID`.

*j*<br/>
Następny bajt obiektu `GUID`.

*k*<br/>
Następny bajt obiektu `GUID`.

*m*<br/>
A `GUID` w formie [identyfikator GUID struktury](/previous-versions/aa373931\(v=vs.80\)).

*n*<br/>
Pozostałe 8 bajtów `GUID`.

## <a name="operator-equality"></a> GUID::operator == — Operator

Porównuje dwa `Platform::Guid` wystąpienia pod kątem równości.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli dwa `Platform::Guid` wystąpień są takie same.

### <a name="remarks"></a>Uwagi

Preferuj przy użyciu `==` operator zamiast [Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals) metody statycznej.

## <a name="operator-inequality"></a> GUID::operator! = — Operator

Porównuje dwa `Platform::Guid` wystąpienia pod kątem nierówności.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli dwa `Platform::Guid` wystąpienia nie są takie same.

## <a name="operator-less"></a> GUID::operator&lt; — Operator

Porównuje dwa `Platform::Guid` wystąpień do ustalania kolejności.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli *guid1* był zamówiony przed *guid2*. Ustalanie kolejności jest leksykograficznych po każdym znaku `Platform::Guid` tak, jakby była tablicę czterech 32-bitowych wartości bez znaku. Nie jest w kolejności, używany przez program SQL Server lub programu .NET Framework nie jest taka sama jak lexicographical kolejność przez reprezentację w postaci ciągu.

Ten operator jest dostarczany, aby `Guid` obiektów, które mogą być łatwo używane przez standardowej biblioteki języka C++.

## <a name="operator-call"></a> GUID::operator() Operator

Niejawnie konwertuje `Platform::Guid` do [identyfikator GUID struktury](/previous-versions/aa373931\(v=vs.80\)).

### <a name="syntax"></a>Składnia

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Wartość zwracana

A [identyfikator GUID struktury](/previous-versions/aa373931\(v=vs.80\)).

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
