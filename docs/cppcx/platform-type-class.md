---
title: Platform::type, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs:
- C++
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea0723d1dfa3c278ab385e393cd0f3b0d9f633f0
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109061"
---
# <a name="platformtype-class"></a>Platform::type, klasa

Zawiera informacje środowiska wykonawczego o typie — w szczególności ciągu nazwy i elementu typecode. Można uzyskać przez wywołanie [Object::gettype —](../cppcx/platform-object-class.md#gettype) dowolnego obiektu lub za pomocą [typeid](../windows/typeid-cpp-component-extensions.md) operatora na nazwę klasy lub struktury.

## <a name="syntax"></a>Składnia

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Uwagi

`Type` Klasy jest przydatne w aplikacjach, które musi kierować przetwarzania przy użyciu `if` lub `switch` instrukcję, która gałęzi na podstawie czasu wykonywania typu obiektu. Kod typu, który opisuje kategorii typu jest pobierany za pomocą [Type::GetTypeCode](#gettypecode) funkcja elementu członkowskiego.

## <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[Metoda type::GetTypeCode](#gettypecode)|Zwraca [Platform::TypeCode, wyliczenie](../cppcx/platform-typecode-enumeration.md) dla tego obiektu.|
|[Metoda type::toString](#tostring)|Zwraca nazwę typu, jak to określono w jego metadanych.|

## <a name="public-properties"></a>Właściwości publiczne

|||
|-|-|
|[Type::FullName](#fullname)|Zwraca [Platform::String, klasa](../cppcx/platform-string-class.md)^ reprezentuje w pełni kwalifikowaną nazwę typu i używa. (kropka) jako separatora, nie:: (podwójny dwukropek) — na przykład `MyNamespace.MyClass`.|

## <a name="conversion-operators"></a>Operatory konwersji

|||
|-|-|
|[Typ operatora ^](../cppcx/operator-type-hat.md)|Umożliwia konwersję z `Windows::UI::Xaml::Interop::TypeName` do `Platform::Type`.|
|[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Umożliwia konwersję z `Platform::Type` do `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd

## <a name="fullname"></a> Właściwość Type::FullName

Pobiera w pełni kwalifikowaną nazwę bieżącego typu w formularzu `Namespace.Type`.

### <a name="syntax"></a>Składnia

```cpp
String^ FullName();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu.
### <a name="example"></a>Przykład

```

//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="gettypecode"></a> Metoda type::GetTypeCode

Pobiera kategorię typu liczbowego wbudowanych typów.

### <a name="syntax"></a>Składnia

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Wartość zwracana

Jedną z Platform::TypeCode wyliczonych wartości.

### <a name="remarks"></a>Uwagi

Odpowiednik metody elementu członkowskiego GetTypeCode() to `typeid` właściwości.

## <a name="tostring"></a> Metoda type::toString

Pobiera nazwę typu.

### <a name="syntax"></a>Składnia

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Nazwa typu, jak to określono w jego metadanych.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)