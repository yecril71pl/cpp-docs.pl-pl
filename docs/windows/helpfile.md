---
title: HelpFile — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c2714c1418c5c9828322561ae1d7ca86dc6130a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647739"
---
# <a name="helpfile"></a>helpfile
Określa nazwę pliku pomocy dla biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ helpfile(  
   "filename"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Nazwa pliku*  
 Nazwa pliku który zawiera tematy Pomocy.  
  
## <a name="remarks"></a>Uwagi  
 **Helpfile** atrybut C++ ma taką samą funkcjonalność jak [helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [modułu](../windows/module-cpp.md) przykład sposobu użycia **helpfile**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**interfejs**, **typedef**, **klasy**, metody, **właściwości**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty metody](../windows/method-attributes.md)   
 [Element TypeDef, Enum, Union i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpcontext —](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   