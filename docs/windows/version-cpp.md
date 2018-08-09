---
title: Wersja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ef27e86ae356ddc67555390b7e053daa8d32a09
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013356"
---
# <a name="version-c"></a>version (C++)
Identyfikuje określoną wersję spośród wielu wersji klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[ version(  
   "version"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Wersja*  
 Numer wersji `coclass`. Jeśli nie zostanie określony, 1.0 zostanie umieszczona w pliku .idl.  
  
## <a name="remarks"></a>Uwagi  
 **Wersji** atrybut C++ ma taką samą funkcjonalność jak [wersji](http://msdn.microsoft.com/library/windows/desktop/aa367306) atrybutów w MIDL i jest przekazywana do pliku .idl wygenerowany.  
  
## <a name="example"></a>Przykład  
 Zobacz [możliwej do wiązania](../windows/bindable.md) przykład użycie próbki **wersji**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, **— struktura**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   