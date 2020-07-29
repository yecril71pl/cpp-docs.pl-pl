---
title: 'Platform:: Type — Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 2c73967d287ade86e2657af70592845d2cc2085e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185037"
---
# <a name="platformtype-class"></a>Platform:: Type — Klasa

Zawiera informacje dotyczące typu w czasie wykonywania, w tym nazwę ciągu i element TypeCode. Uzyskany przez wywołujący [obiekt:: GetType](../cppcx/platform-object-class.md#gettype) dla dowolnego obiektu lub przy użyciu operatora [typeid](../extensions/typeid-cpp-component-extensions.md) dla nazwy klasy lub struktury.

## <a name="syntax"></a>Składnia

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Uwagi

`Type`Klasa jest przydatna w aplikacjach, które muszą bezpośrednio przetwarzać przy **`if`** użyciu **`switch`** instrukcji lub, która jest zależna od typu czasu wykonywania obiektu. Kod typu, który opisuje kategorię typu, jest pobierany przy użyciu funkcji składowej [typu:: GetTypeCode](#gettypecode) .

## <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[Type:: GetTypeCode — Metoda](#gettypecode)|Zwraca wartość [wyliczenia platform:: TypeCode](../cppcx/platform-typecode-enumeration.md) dla obiektu.|
|[Type:: ToString — Metoda](#tostring)|Zwraca nazwę typu, jak określono w jego metadanych.|

## <a name="public-properties"></a>Właściwości publiczne

|||
|-|-|
|[Typ:: FullName](#fullname)|Zwraca [klasę platform:: String](../cppcx/platform-string-class.md)^ reprezentującą w pełni kwalifikowaną nazwę typu i używa. (kropka) jako separator, nie:: (dwukropek) — na przykład `MyNamespace.MyClass` .|

## <a name="conversion-operators"></a>Operatory konwersji

|||
|-|-|
|[Typ operatora ^](../cppcx/operator-type-hat.md)|Włącza konwersję z `Windows::UI::Xaml::Interop::TypeName` do `Platform::Type` .|
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Włącza konwersję z `Platform::Type` do `Windows::UI::Xaml::Interop::TypeName` .|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Type:: FullName, właściwość

Pobiera w postaci w pełni kwalifikowaną nazwę bieżącego typu `Namespace.Type` .

### <a name="syntax"></a>Składnia

```cpp
String^ FullName();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu.

### <a name="example"></a>Przykład

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Type:: GetTypeCode — Metoda

Pobiera typy wbudowanej kategorii typu liczbowego.

### <a name="syntax"></a>Składnia

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia platform:: TypeCode.

### <a name="remarks"></a>Uwagi

Odpowiednikiem metody elementu członkowskiego GetTypeCode () jest **`typeid`** Właściwość.

## <a name="typetostring-method"></a><a name="tostring"></a>Type:: ToString — Metoda

Pobiera nazwę typu.

### <a name="syntax"></a>Składnia

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu określonego w metadanych.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
