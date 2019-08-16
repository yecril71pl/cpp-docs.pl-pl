---
title: propputref (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 9dc21494886f80890bcfde7f29bb3d6c86b4a51b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514182"
---
# <a name="propputref"></a>propputref

Określa funkcję ustawienia właściwości, która używa odwołania zamiast wartości.

## <a name="syntax"></a>Składnia

```cpp
[propputref]
```

## <a name="remarks"></a>Uwagi

Atrybut **propputref** C++ ma takie same funkcje jak atrybut [propputref](/windows/win32/Midl/propputref) MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [powiązania](bindable.md) z przykładowym wykorzystaniem **propputref**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|`propget`, `propput`|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)