---
title: propput (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: c9853b38675abfa0a94a319ac752eb2ef61a48e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407526"
---
# <a name="propput"></a>propput

Określa funkcję ustawienie właściwości.

## <a name="syntax"></a>Składnia

```cpp
[propput]
```

## <a name="remarks"></a>Uwagi

**Propput** atrybut C++ ma taką samą funkcjonalność jak [propput](/windows/desktop/Midl/propput) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) do użytku przykładowe **propput**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`propget`, `propputref`|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)