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
ms.openlocfilehash: 803b4652d4a6482e9e7615121d3a85f0bee309f7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013668"
---
# <a name="lcid"></a>lcid
Służy do przekazywania identyfikator ustawień regionalnych do funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[lcid]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Lcid** atrybut C++ implementuje funkcje [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) atrybutów w MIDL. Jeśli chcesz wdrożyć ustawienia regionalne dla bloku biblioteki, użyj **lcid =** `lcid` parametr [modułu](../windows/module-cpp.md) atrybutu.  
  
## <a name="example"></a>Przykład  
  
```cpp  
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
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Parametr interfejsu|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   