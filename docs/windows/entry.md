---
title: wpis | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f644df2969954187aa4506d2cc1d04d140f88de3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642890"
---
# <a name="entry"></a>entry
Określa eksportowanych funkcji lub stałą w module, określając punkt wejścia w DLL.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ entry(  
   id  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 Identyfikator punktu wejścia.  
  
## <a name="remarks"></a>Uwagi  
 **Wpis** atrybut C++ ma taką samą funkcjonalność jak [wpis](http://msdn.microsoft.com/library/windows/desktop/aa366815) atrybutów w MIDL.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [idl_module](../windows/idl-module.md) dla przykładowe **wpis**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|`idl_module` Atrybut|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   