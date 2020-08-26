---
title: atrybut HelpContext (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 60e6bf66e088872a357751e4a7b7e043cd9b4dfc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845253"
---
# <a name="helpcontext"></a>helpcontext

Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku **pomocy** .

## <a name="syntax"></a>Składnia

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
Identyfikator kontekstu tematu pomocy. Zobacz [Pomoc HTML: Pomoc kontekstową dla programów](../../mfc/html-help-context-sensitive-help-for-your-programs.md) , aby uzyskać więcej informacji na temat identyfikatorów kontekstu.

## <a name="remarks"></a>Uwagi

Atrybut **atrybut HelpContext** C++ ma takie same funkcje jak atrybut [atrybut HelpContext](/windows/win32/Midl/helpcontext) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla elementu [DefaultValue](defaultvalue.md) , aby zapoznać się z przykładem korzystania z **atrybut HelpContext**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**interfejs**, **`typedef`** , **`class`** , metoda, właściwość|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
