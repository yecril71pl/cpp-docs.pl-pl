---
title: HelpString — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 928f4fe5200d9ea03541976664d472d9e99e1147
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575693"
---
# <a name="helpstring"></a>helpstring

Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.

## <a name="syntax"></a>Składnia

```cpp
[ helpstring(
   "string"
) ]
```

### <a name="parameters"></a>Parametry

*string*  
Tekst Ciąg pomocy.

## <a name="remarks"></a>Uwagi

**HelpString —** atrybut C++ ma taką samą funkcjonalność jak [HelpString —](http://msdn.microsoft.com/library/windows/desktop/aa366856) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [defaultvalue](../windows/defaultvalue.md) przykład sposobu użycia **HelpString —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **typedef**, **klasy**, metody, właściwości|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[helpfile](../windows/helpfile.md)  
[helpcontext](../windows/helpcontext.md)  