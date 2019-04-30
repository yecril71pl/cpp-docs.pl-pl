---
title: Platform::IBoxArray, interfejs
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: ea2517ad64cfd6742ef072d24e94a9b3899cea2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392079"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray, interfejs

`IBoxArray` jest otoką dla tablic typów wartości, które są przekazywane między interfejsem binarnym aplikacji (ABI) lub przechowywane w kolekcjach `Platform::Object^` elementów, takich jak te w kontrolkach XAML.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wartości spakowanej w każdym elemencie tablicy.

### <a name="remarks"></a>Uwagi

`IBoxArray` jest C++nazwę /CX `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Elementy członkowskie

`IBoxArray` Interfejs dziedziczy z `IValueType` interfejsu. `IBoxArray` ma również te elementy członkowskie:

|Metoda|Opis|
|------------|-----------------|
|[Wartość](#value)|Zwraca tablicę rozpakowany, które wcześniej były przechowywane w tym `IBoxArray` wystąpienia.|

## <a name="value"></a> Właściwość IBoxArray::Value

Zwraca wartość, która pierwotnie została zapisana w tym obiekcie.

### <a name="syntax"></a>Składnia

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ wartości spakowanej.

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Zwraca wartość, która pierwotnie została zapisana w tym obiekcie.

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład, zobacz [pakowania](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Zobacz także

[Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
