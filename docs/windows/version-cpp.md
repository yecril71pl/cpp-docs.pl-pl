---
title: Wersja (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.version
dev_langs: C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 757ab7a6d2c8b846a51da359c4b8dc5a72c6e9e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|**Wymaganych atrybutów**|**Klasa coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
