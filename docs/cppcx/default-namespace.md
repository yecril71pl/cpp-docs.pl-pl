---
title: domyślna przestrzeń nazw
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: 5696730bcef08ad11be4a2b689e95eb3c13e11eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845708"
---
# <a name="default-namespace"></a>domyślna przestrzeń nazw

`default`Przestrzeń nazw ma wbudowane typy, które są obsługiwane przez C++/CX.

## <a name="syntax"></a>Składnia

```
namespace default;
```

### <a name="members"></a>Elementy członkowskie

Wszystkie typy wbudowane dziedziczą następujące elementy członkowskie.

| Nazwa | Opis |
|--|--|
| [default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md) | Określa, czy dany obiekt jest taki sam, jak bieżący obiekt. |
| [default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md) | Zwraca wartość skrótu dla tego wystąpienia. |
| [default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md) | Zwraca ciąg, który reprezentuje bieżący typ. |
| [default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md) | Zwraca ciąg, który reprezentuje bieżący typ. |

### <a name="built-in-types"></a>Typy wbudowane

|Nazwa|Opis|
|----------|-----------------|
|`char16`|16-bitowa wartość nieliczbowa, która reprezentuje punkt kodowy w formacie Unicode (UTF-16).|
|`float32`|32-bitowa liczba zmiennoprzecinkowa IEEE 754.|
|`float64`|64-bitowa liczba zmiennoprzecinkowa IEEE 754.|
|`int16`|16-bitowa liczba całkowita ze znakiem.|
|`int32`|32-bitowa liczba całkowita ze znakiem.|
|`int64`|64-bitowa liczba całkowita ze znakiem.|
|`int8`|8-bitowa podpisana wartość numeryczna.|
|`uint16`|16-bitowa liczba całkowita bez znaku.|
|`uint32`|32-bitowa liczba całkowita bez znaku.|
|`uint64`|64-bitowa liczba całkowita bez znaku.|
|`uint8`|8-bitowa wartość liczbowa bez znaku.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib. h

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
