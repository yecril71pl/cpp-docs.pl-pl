---
title: last_is (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: ad82a5a9688dfbc6c5eb59883be00e8dc39e1942
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840885"
---
# <a name="last_is"></a>last_is

Określa indeks ostatniego elementu tablicy, który ma zostać przesłany.

## <a name="syntax"></a>Składnia

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>Parametry

*wyrażenia*<br/>
Co najmniej jedno wyrażenie języka C. Puste gniazda argumentów są dozwolone.

## <a name="remarks"></a>Uwagi

Atrybut **last_is** C++ ma takie same funkcje jak atrybut [last_is](/windows/win32/Midl/last-is) MIDL.

## <a name="example"></a>Przykład

Zobacz [first_is](first-is.md) , aby zapoznać się z przykładem, jak określić sekcję tablicy.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Pole w **`struct`** lub **`union`** , parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
