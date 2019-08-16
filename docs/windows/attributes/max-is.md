---
title: max_is (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: f2e6db997891817620c1b2c1f70cb310818dd346
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514428"
---
# <a name="max_is"></a>max_is

Określa maksymalną wartość prawidłowego indeksu tablicy.

## <a name="syntax"></a>Składnia

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Co najmniej jedno wyrażenie języka C. Puste gniazda argumentów są dozwolone.

## <a name="remarks"></a>Uwagi

Atrybut **max_is** C++ ma takie same funkcje jak atrybut [max_is](/windows/win32/Midl/max-is) MIDL.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole w **strukturze** lub **Unii**, parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|**size_is**|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Przykład

Zobacz [first_is](first-is.md) , aby zapoznać się z przykładem, jak określić sekcję tablicy.

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)