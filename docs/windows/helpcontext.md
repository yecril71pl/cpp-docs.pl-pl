---
title: helpcontext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 317e204c7292c4a7cccb1f81f6bc9d2a2fbfd407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877218"
---
# <a name="helpcontext"></a>helpcontext
Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator kontekstu tematu Pomocy. Zobacz [Pomoc HTML: Context-Sensitive Pomoc dla programów Your](../mfc/html-help-context-sensitive-help-for-your-programs.md) uzyskać więcej informacji o kontekście identyfikatorów.  
  
## <a name="remarks"></a>Uwagi  
 **Helpcontext** atrybut C++ ma te same funkcje co [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [defaultvalue](../windows/defaultvalue.md) przykład sposobu użycia **helpcontext**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|`interface`, `typedef`, **klasy**, metody, właściwości|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Atrybuty — metoda](../windows/method-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpFile](../windows/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
