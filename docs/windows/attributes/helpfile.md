---
title: HelpFile (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 538cdbb38ac525cfee03a641f3e62e22a69f8e2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501551"
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
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)