---
title: propput | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c8d9038fc8ded02afe02169731692b290466df6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442815"
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

Zobacz przykład [możliwej do wiązania](../windows/bindable.md) do użytku przykładowe **propput**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`propget`, `propputref`|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty metody](../windows/method-attributes.md)<br/>
[propget](../windows/propget.md)<br/>
[propputref](../windows/propputref.md)