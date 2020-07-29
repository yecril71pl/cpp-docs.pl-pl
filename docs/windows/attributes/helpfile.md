---
title: HelpFile (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 641823779346bf5417ec0db26b83083fa949e960
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222124"
---
# <a name="helpfile"></a>helpfile

Ustawia nazwę pliku pomocy dla biblioteki typów.

## <a name="syntax"></a>Składnia

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku, który zawiera tematy pomocy.

## <a name="remarks"></a>Uwagi

Atrybut **HelpFile** języka C++ ma takie same funkcje, jak atrybut [HelpFile](/windows/win32/Midl/helpfile) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [modułu](module-cpp.md) , aby zapoznać się z przykładem sposobu korzystania z usługi **HelpFile**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **`typedef`** , **`class`** , metoda,**`property`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
