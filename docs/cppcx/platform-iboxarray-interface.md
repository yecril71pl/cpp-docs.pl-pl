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
ms.openlocfilehash: 78815ed42833c48074abbb4b0c0fa0203f8c35a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597323"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray, interfejs
`IBoxArray` jest otoką dla tablic typów wartości, które są przekazywane między interfejsem binarnym aplikacji (ABI) lub przechowywane w kolekcjach `Platform::Object^` elementów, takich jak te w kontrolkach XAML.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
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
 `T`  
 Typ wartości spakowanej.  
  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Zwraca wartość, która pierwotnie została zapisana w tym obiekcie.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać przykład, zobacz [pakowania](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Zobacz też  
 [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)