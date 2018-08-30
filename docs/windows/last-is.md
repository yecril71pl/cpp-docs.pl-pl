---
title: last_is — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7b699f5b6aa023473416b822a94d9b3a91c2b07
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221122"
---
# <a name="lastis"></a>last_is

Określa indeks ostatniego elementu tablicy mają być przekazywane.

## <a name="syntax"></a>Składnia

```cpp
[ last_is(
   "expression"
) ]
```

### <a name="parameters"></a>Parametry

*Wyrażenie*  
Co najmniej jednego wyrażenia języka C. Pusty argument miejsca są dozwolone.

## <a name="remarks"></a>Uwagi

**Last_is —** atrybut C++ ma taką samą funkcjonalność jak [last_is —](/windows/desktop/Midl/last-is) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [first_is —](../windows/first-is.md) przykład sposobu określania część tablicy.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole **struktury** lub **Unii**, interfejs parametrów, metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atrybuty parametru](../windows/parameter-attributes.md)  
[first_is](../windows/first-is.md)  
[max_is](../windows/max-is.md)  
[length_is](../windows/length-is.md)  
[size_is](../windows/size-is.md)  