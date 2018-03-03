---
title: Wersja (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db6c31df932890799f68e2ae466b0a927f0f999f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="version-c"></a>version (C++)
Identyfikuje określoną wersją wśród wielu wersji klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Wersja*  
 Numer wersji klasy coclass. Jeśli nie zostanie określony, 1.0 zostaną umieszczone w pliku .idl.  
  
## <a name="remarks"></a>Uwagi  
 **Wersji** atrybut C++ ma te same funkcje co [wersji](http://msdn.microsoft.com/library/windows/desktop/aa367306) atrybutu MIDL i jest przekazywana do pliku .idl wygenerowany.  
  
## <a name="example"></a>Przykład  
 Zobacz [powiązania](../windows/bindable.md) przykład użycie próbki **wersji**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
