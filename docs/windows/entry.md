---
title: wpis | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.entry
dev_langs: C++
helpviewer_keywords: entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d586e2ceaeb922d5f9f96aaa175a5e33ad6ed64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|**Dotyczy**|`idl_module`atrybut|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
