---
title: 'Platform:: IBoxArray, interfejs'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444158"
---
# <a name="platformiboxarray-interface"></a>Platform:: IBoxArray, interfejs

`IBoxArray` jest otoką dla tablic typów wartości, które są przesyłane przez interfejs binarny aplikacji (ABI) lub przechowywane w kolekcjach elementów `Platform::Object^`, takich jak te w kontrolkach XAML.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Typ wartości opakowanej w każdym elemencie tablicy.

### <a name="remarks"></a>Uwagi

`IBoxArray` to nazwa C++/CX dla `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Elementy członkowskie

Interfejs `IBoxArray` dziedziczy po interfejsie `IValueType`. `IBoxArray` ma również następujące elementy członkowskie:

|Metoda|Opis|
|------------|-----------------|
|[Wartość](#value)|Zwraca tablicę nieopakowaną, która była wcześniej przechowywana w tym wystąpieniu `IBoxArray`.|

## <a name="value"></a>IBoxArray:: Value — właściwość

Zwraca wartość oryginalnie przechowywaną w tym obiekcie.

### <a name="syntax"></a>Składnia

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ wartości opakowanej.

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Zwraca wartość oryginalnie przechowywaną w tym obiekcie.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem, zobacz [opakowanie](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
