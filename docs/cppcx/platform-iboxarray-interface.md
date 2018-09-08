---
title: Platform::IBoxArray, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66e3ff5a2daf0ddef41ea478b55ca2fc67298c01
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108451"
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

`IBoxArray` jest C + +/ CX nazwę `Windows::Foundation::IReferenceArray`.

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

## <a name="see-also"></a>Zobacz też

[Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)