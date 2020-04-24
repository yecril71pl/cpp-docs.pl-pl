---
title: Klasa wartości Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 7c3b89ff238b1cb5ee9fbb71e83d20f571e656a3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031540"
---
# <a name="platformguid-value-class"></a>Klasa wartości Platform::Guid

Reprezentuje typ [GUID](/windows/win32/api/guiddef/ns-guiddef-guid w systemie typu Środowiska wykonawczego systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
public value struct Guid
```

### <a name="members"></a>Elementy członkowskie

`Platform::Guid`ma `Equals()`, `GetHashCode()`i `ToString()` metody pochodzące z [Platform::Object](../cppcx/platform-object-class.md) `GetTypeCode()` Class , a metoda pochodząca z [Platform::Type Class](../cppcx/platform-type-class.md). `Platform::Guid`ma również następujących członków.

|Członek|Opis|
|------------|-----------------|
|[Identyfikator guid](#ctor)|Inicjuje nowe wystąpienie `Platform::Guid`pliku .|
|[operator==](#operator-equality)|Równa się operatorowi.|
|[operator!=](#operator-inequality)|Nie jest równa operatorowi.|
|[Operator&lt;](#operator-less)|Mniej niż operator.|
|[Operator()](#operator-call)|Konwertuje `Platform::Guid` a `GUID`do .|

### <a name="remarks"></a>Uwagi

Aby wygenerować nowy `Platform::Guid`, użyj [windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid) metody statycznej.

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Metadane:** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>Guid::Konstruktory Guid

Inicjuje nowe wystąpienie `Platform::Guid`pliku .

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

*A*<br/>
Pierwsze 4 bajty `GUID`.

*B*<br/>
Następne 2 bajty `GUID`.

*C*<br/>
Następne 2 bajty `GUID`.

*D*<br/>
Następny bajt `GUID`.

*E*<br/>
Następny bajt `GUID`.

*F*<br/>
Następny bajt `GUID`.

*G*<br/>
Następny bajt `GUID`.

*H*<br/>
Następny bajt `GUID`.

*I*<br/>
Następny bajt `GUID`.

*J*<br/>
Następny bajt `GUID`.

*K*<br/>
Następny bajt `GUID`.

*M*<br/>
A `GUID` w formie [struktury GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

*N*<br/>
Pozostałe 8 bajtów `GUID`.

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>Guid::operator== Operator

Porównuje dwa `Platform::Guid` wystąpienia dla równości.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2 ( guid2 )*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

True, jeśli `Platform::Guid` dwa wystąpienia są równe.

### <a name="remarks"></a>Uwagi

Preferuj `==` użycie operatora zamiast [metody windows::Foundation::GuidHelper::Równa się metodzie](/uwp/api/windows.foundation.guidhelper.equals) statycznej.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>Guid::operator!= Operator

Porównuje dwa `Platform::Guid` wystąpienia nierówności.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2 ( guid2 )*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

True, jeśli `Platform::Guid` dwa wystąpienia nie są równe.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>Guid::operator&lt; Operator

Porównuje dwa `Platform::Guid` wystąpienia do zamawiania.

### <a name="syntax"></a>Składnia

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parametry

*guid1*<br/>
Pierwszy `Platform::Guid` do porównania.

*guid2 ( guid2 )*<br/>
Drugi `Platform::Guid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Prawda, jeśli *guid1* jest uporządkowany przed *guid2*. Kolejność jest leksykograficzna `Platform::Guid` po traktowaniu każdego tak, jakby była tablicą czterech 32-bitowych niepodpisanych wartości. Nie jest to kolejność używana przez program SQL Server lub .NET Framework ani nie jest taka sama jak kolejność leksykograficzna według reprezentacji ciągów.

Ten operator jest `Guid` dostarczany, dzięki czemu obiekty mogą być łatwiej używane przez standardową bibliotekę języka C++.

## <a name="guidoperator-operator"></a><a name="operator-call"></a>Guid::operator() Operator

Niejawnie konwertuje a `Platform::Guid` do struktury [GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Składnia

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Wartość zwracana

[Struktura guid](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
