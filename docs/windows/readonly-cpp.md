---
title: tylko do odczytu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b4f4e6d7c3941b1e90e0c49d113afe02dfcd491
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604427"
---
# <a name="readonly-c"></a>readonly (C++)
Zabrania przypisania element członkowski danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
[readonly]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Tylko do odczytu** atrybut C++ ma taką samą funkcjonalność jak [tylko do odczytu](http://msdn.microsoft.com/library/windows/desktop/aa367152) atrybutów w MIDL.  
  
 Jeśli chcesz uniemożliwiają modyfikację parametru metody, należy użyć [w](../windows/in-cpp.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje wykorzystanie **tylko do odczytu** atrybutu:  
  
```cpp  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty składowych danych](../windows/data-member-attributes.md)   