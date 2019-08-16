---
title: length_is (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 4f4bfe233e3228c50aee734de4ad979c38a55fda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514528"
---
# <a name="length_is"></a>length_is

Określa liczbę elementów tablicy do przesłania.

## <a name="syntax"></a>Składnia

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>Parametry

*expression*<br/>
Co najmniej jedno wyrażenie języka C. Puste gniazda argumentów są dozwolone.

## <a name="remarks"></a>Uwagi

Atrybut **length_is** C++ ma takie same funkcje jak atrybut [length_is](/windows/win32/Midl/length-is) MIDL.

## <a name="example"></a>Przykład

Zobacz [first_is](first-is.md) , aby zapoznać się z przykładem, jak określić sekcję tablicy.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Pole w **strukturze** lub **Unii**, parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[last_is](last-is.md)<br/>
[size_is](size-is.md)