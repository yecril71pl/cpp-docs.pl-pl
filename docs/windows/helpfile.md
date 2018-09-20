---
title: HelpFile — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66cd89c28ea01c3a75d0cb25aa6f96a234e379b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418206"
---
# <a name="helpfile"></a>helpfile

Określa nazwę pliku pomocy dla biblioteki typów.

## <a name="syntax"></a>Składnia

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku który zawiera tematy Pomocy.

## <a name="remarks"></a>Uwagi

**Helpfile** atrybut C++ ma taką samą funkcjonalność jak [helpfile](/windows/desktop/Midl/helpfile) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [modułu](../windows/module-cpp.md) przykład sposobu użycia **helpfile**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **typedef**, **klasy**, metody, **właściwości**|
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
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)  