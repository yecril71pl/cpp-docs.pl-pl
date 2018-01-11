---
title: Interfejs platform::IBox | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs: C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a86eca75bb5470585ba68fe3b7fcdb55c861434
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformibox-interface"></a>Interfejs platform::IBox
[Platform::IBox](../cppcx/platform-ibox-interface.md) interfejsu jest nazwą C++ `Windows::Foundation::IReference` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wartości spakowanej.  
  
### <a name="remarks"></a>Uwagi  
 `IBox<T>` Interfejsu jest głównie używana wewnętrznie w celu reprezentowania typów wartości null, zgodnie z opisem w [wartość klas i struktur (C + +/ CX)](../cppcx/value-classes-and-structs-c-cx.md). Interfejs służy również do typów wartości pola, które są przekazywane do metody C++, które przyjmują parametrów typu `Object^`. Można jawnie deklarować jako parametr wejściowy `IBox<SomeValueType>`. Na przykład zobacz [Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="requirements"></a>Wymagania  
  
### <a name="members"></a>Elementy członkowskie  
 `Platform::IBox` Dziedziczy interfejs [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) interfejsu. `IBox`ma tych elementów członkowskich:  
  
 **Właściwości**  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Wartość](#value)|Zwraca wartość rozpakowany, które wcześniej były przechowywane w tym `IBox` wystąpienia.|  

## <a name="value"></a>Właściwość IBox::Value
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
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)