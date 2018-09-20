---
title: helpstringcontext — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47afe841a2a8e4a1c41baf68dfd139a70b320c7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394468"
---
# <a name="helpstringcontext"></a>helpstringcontext

Określa identyfikator tematu pomocy w pliku hlp lub chm.

## <a name="syntax"></a>Składnia

```cpp
[ helpstringcontext(
   contextID
) ]
```

### <a name="parameters"></a>Parametry

*Identyfikator kontekstu*<br/>
Identyfikator kontekstu pomocy w 32-bitowych w **pomocy** pliku.

## <a name="remarks"></a>Uwagi

**Helpstringcontext —** atrybut C++ ma taką samą funkcjonalność jak [helpstringcontext —](/windows/desktop/Midl/helpstringcontext) odl — atrybut.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object,
   helpstring("help string"),
   helpstringcontext(1),
   uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **interfejsu**, interfejs — metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty interfejsu](../windows/interface-attributes.md)<br/>
[Atrybuty klasy](../windows/class-attributes.md)<br/>
[Atrybuty metody](../windows/method-attributes.md)<br/>
[Moduł](../windows/module-cpp.md)  