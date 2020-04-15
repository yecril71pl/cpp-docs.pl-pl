---
title: Platform::Type, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322093"
---
# <a name="platformtype-class"></a>Platform::Type, klasa

Zawiera informacje o czasie wykonywania typu — w szczególności nazwę ciągu i kod typu. Uzyskane przez [wywołanie Object::GetType](../cppcx/platform-object-class.md#gettype) na dowolnym obiekcie lub przy użyciu operatora [typeid](../extensions/typeid-cpp-component-extensions.md) na nazwę klasy lub struktury.

## <a name="syntax"></a>Składnia

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Uwagi

Klasa `Type` jest przydatna w aplikacjach, które `if` `switch` muszą bezpośrednio przetwarzania przy użyciu lub instrukcji, która oddziałów na podstawie typu wykonywania obiektu. Kod typu opisujący kategorię typu jest pobierany przy użyciu funkcji elementu członkowskiego [Type::GetTypeCode.](#gettypecode)

## <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[Typ::Metoda GetTypeCode](#gettypecode)|Zwraca [wartość wyliczenia platformy::TypeCode](../cppcx/platform-typecode-enumeration.md) dla obiektu.|
|[Typ::Metoda ToString](#tostring)|Zwraca nazwę typu określonego w jego metadanych.|

## <a name="public-properties"></a>Właściwości publiczne

|||
|-|-|
|[Typ::Pełna nazwa](#fullname)|Zwraca [platformę::String Class](../cppcx/platform-string-class.md)^ reprezentującą w pełni kwalifikowaną nazwę typu i używa . (kropka) jako separator, a nie :: (dwukropek) — na przykład `MyNamespace.MyClass`.|

## <a name="conversion-operators"></a>Operatory konwersji

|||
|-|-|
|[typ operatora^](../cppcx/operator-type-hat.md)|Umożliwia konwersję z `Windows::UI::Xaml::Interop::TypeName` do `Platform::Type`.|
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Umożliwia konwersję z `Platform::Type` do `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Metadane:** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Typ::Właściwość FullName

Pobiera w pełni kwalifikowaną nazwę bieżącego `Namespace.Type`typu w formularzu .

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

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Typ::Metoda GetTypeCode

Pobiera wbudowaną kategorię typów numerycznych.

### <a name="syntax"></a>Składnia

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczonych przez platformę::TypeCode.

### <a name="remarks"></a>Uwagi

Odpowiednik getTypeCode() metoda elementu członkowskiego `typeid` jest właściwość.

## <a name="typetostring-method"></a><a name="tostring"></a>Typ::Metoda ToString

Pobiera nazwę typu.

### <a name="syntax"></a>Składnia

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu określonego w jego metadanych.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
