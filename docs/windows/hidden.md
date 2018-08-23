---
title: ukryte | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9523fc63e36d9a2b93dc6df1a49627ac5fbebc9b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602158"
---
# <a name="hidden"></a>hidden

Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.

## <a name="syntax"></a>Składnia

```cpp
[hidden]
```

## <a name="remarks"></a>Uwagi

**Ukryte** atrybut C++ ma taką samą funkcjonalność jak [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](../windows/bindable.md) przykład sposobu użycia **ukryte**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **klasy**, **struktury**, metody, właściwości|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**Klasa coclass** (po zastosowaniu do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  