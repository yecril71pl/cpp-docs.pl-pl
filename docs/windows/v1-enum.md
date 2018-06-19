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
ms.openlocfilehash: b3156554f5d2b799a9e1ef5a067d1f2e8e600d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890664"
---
# <a name="v1enum"></a>v1_enum
Określa, że przekazywane na określony typ wyliczeniowy jako jednostki 32-bitowe zamiast domyślnego 16-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[v1_enum]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **V1_enum —** atrybut C++ ma te same funkcje co [v1_enum —](http://msdn.microsoft.com/library/windows/desktop/aa367303) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia korzystanie z **v1_enum —**:  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Typ wyliczeniowy|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
