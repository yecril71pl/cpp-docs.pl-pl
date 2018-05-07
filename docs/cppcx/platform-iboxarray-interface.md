---
title: Interfejs platform::IBoxArray | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 572724dcebbdb3921b26d6c688ff5d68d1392437
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformiboxarray-interface"></a>Interfejs platform::IBoxArray
`IBoxArray` Otoka dla tablic typów wartości, które są przekazywane przez interfejs binarne aplikacji (ABI) lub przechowywane w kolekcji jest `Platform::Object^` elementów, takich jak te w formantach XAML.  
  
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
 `IBoxArray` Dziedziczy interfejs `IValueType` interfejsu. `IBoxArray` ma również te elementy członkowskie:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Wartość](#value)|Zwraca tablicę rozpakowany, które wcześniej były przechowywane w tym `IBoxArray` wystąpienia.|  

## <a name="value"></a> Właściwość IBoxArray::Value
Zwraca wartość, która pierwotnie była przechowywana w tym obiekcie.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ wartości spakowanej.  
  
### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Zwraca wartość, która pierwotnie była przechowywana w tym obiekcie.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład zobacz [Boxing](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Zobacz też  
 [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)