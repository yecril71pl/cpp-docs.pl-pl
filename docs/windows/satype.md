---
title: satype — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a77021cbcf6622701a1025ef33000196ba7bb6d9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888685"
---
# <a name="satype"></a>satype
Określa typ danych **SAFEARRAY** struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ satype(  
   data_type  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *data_type*  
 Typ danych dla **SAFEARRAY** struktura danych, która jest przekazywana jako parametr do metody interfejsu.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Interfejs parametru metody interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
## <a name="remarks"></a>Uwagi  
 **Satype —** C++ atrybut określa typ danych **SAFEARRAY**.  
  
> [!NOTE]
>  Poziom pośredni jest usuwane ze **SAFEARRAY** wskaźnika w pliku .idl wygenerowany, w jaki sposób jest zadeklarowany w pliku .cpp.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [id](../windows/id.md)   
