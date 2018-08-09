---
title: v1_enum — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.v1_enum
dev_langs:
- C++
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15e51719e1daecc440dc5945a54443e4bc5079ec
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644368"
---
# <a name="v1enum"></a>v1_enum
Określa, że przekazywane określonego typu wyliczenia jako jednostki 32-bitowych, a nie domyślnej 16-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
[v1_enum]  
```  
  
## <a name="remarks"></a>Uwagi  
 **V1_enum —** atrybut C++ ma taką samą funkcjonalność jak [v1_enum —](http://msdn.microsoft.com/library/windows/desktop/aa367303) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje wykorzystanie **v1_enum —**:  
  
```cpp  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Typy wyliczeniowe|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   