---
title: helpcontext — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d9c2efecf34e5d58f633bc21e62801157b1b8955
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388592"
---
# <a name="helpcontext"></a>helpcontext

Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.

## <a name="syntax"></a>Składnia

```cpp
[ helpcontext(
   id
) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
Identyfikator kontekstu tematu Pomocy. Zobacz [HTML Help: Context-Sensitive Help for Your Programs](../mfc/html-help-context-sensitive-help-for-your-programs.md) więcej informacji na temat kontekstu identyfikatorów.

## <a name="remarks"></a>Uwagi

**Helpcontext —** atrybut C++ ma taką samą funkcjonalność jak [helpcontext —](/windows/desktop/Midl/helpcontext) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [defaultvalue](../windows/defaultvalue.md) przykład sposobu użycia **helpcontext —**.

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

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty interfejsu](../windows/interface-attributes.md)<br/>
[Atrybuty klasy](../windows/class-attributes.md)<br/>
[Atrybuty metody](../windows/method-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](../windows/helpfile.md)<br/>
[helpstring](../windows/helpstring.md)  