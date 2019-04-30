---
title: propget (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 8f60e8e8fc98ba3b75acefe80812069bfac78e6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407630"
---
# <a name="propget"></a>propget

Określa funkcję metody dostępu właściwości.

## <a name="syntax"></a>Składnia

```cpp
[propget]
```

## <a name="remarks"></a>Uwagi

**Propget** atrybut C++ ma taką samą funkcjonalność jak [propget](/windows/desktop/Midl/propget) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) do użytku przykładowe **propget**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`propput`, `propputref`|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)