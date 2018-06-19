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
ms.openlocfilehash: db90390be5313ddbea1103105f47b55fe9e23d62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872318"
---
# <a name="entry"></a>entry
Określa wyeksportowanej funkcji lub stała w module, określając punkt wejścia w bibliotece DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator punktu wejścia.  
  
## <a name="remarks"></a>Uwagi  
 **Wpis** atrybut C++ ma te same funkcje co [wpis](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [idl_module](../windows/idl-module.md) na przykład użyj programu **wpis**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`idl_module` Atrybut|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
