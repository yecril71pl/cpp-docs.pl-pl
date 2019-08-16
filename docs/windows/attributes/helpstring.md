---
title: HelpString (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 47a07ee94ad774bde46dce00ea46612fae3a4eca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490875"
---
# <a name="helpstring"></a>helpstring

Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie.

## <a name="syntax"></a>Składnia

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Tekst ciągu pomocy.

## <a name="remarks"></a>Uwagi

Atrybut **HelpString** C++ ma takie same funkcje jak atrybut [HelpString](/windows/win32/Midl/helpstring) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla elementu [DefaultValue](defaultvalue.md) , aby zapoznać się z przykładem korzystania z **HelpString**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **typedef**, **Klasa**, metoda, właściwość|
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
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)