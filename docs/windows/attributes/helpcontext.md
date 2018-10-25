---
title: helpcontext — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 831ca61f82eee913efd1ab2b1420fefb011d6c1a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062837"
---
# <a name="helpcontext"></a>helpcontext

Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w **pomocy** pliku.

## <a name="syntax"></a>Składnia

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
Identyfikator kontekstu tematu Pomocy. Zobacz [HTML Help: Context-Sensitive Help for Your Programs](../../mfc/html-help-context-sensitive-help-for-your-programs.md) więcej informacji na temat kontekstu identyfikatorów.

## <a name="remarks"></a>Uwagi

**Helpcontext —** atrybut C++ ma taką samą funkcjonalność jak [helpcontext —](/windows/desktop/Midl/helpcontext) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [defaultvalue](defaultvalue.md) przykład sposobu użycia **helpcontext —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **typedef**, **klasy**, metody, właściwości|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)