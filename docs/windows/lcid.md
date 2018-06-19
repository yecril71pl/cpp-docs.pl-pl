---
title: Identyfikator LCID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.lcid
dev_langs:
- C++
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c36c4a53dc627af10b6c768cdc9bc9353cbd4877
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877257"
---
# <a name="lcid"></a>lcid
Pozwala przekazać do funkcji identyfikator ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[lcid]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Lcid** atrybutu C++ implementuje funkcje [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) MIDL atrybutu. Jeśli chcesz wdrożyć ustawienia regionalne dla bloku biblioteki, użyj **lcid =** `lcid` parametr [modułu](../windows/module-cpp.md) atrybutu.  
  
## <a name="example"></a>Przykład  
  
```  
// cpp_attr_ref_lcid.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
typedef long HRESULT;  
  
[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]  
__interface IStatic {  
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Parametr — interfejs|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
