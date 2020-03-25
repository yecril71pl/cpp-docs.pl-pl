---
title: HelpFile (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 1f928fa281c99630ad52ce1fde184c44e9387263
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166981"
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

Atrybut **HelpFile** C++ ma takie same funkcje, jak atrybut [HelpFile](/windows/win32/Midl/helpfile) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [modułu](module-cpp.md) , aby zapoznać się z przykładem sposobu korzystania z usługi **HelpFile**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **typedef**, **Klasa**, metoda, **Właściwość**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
