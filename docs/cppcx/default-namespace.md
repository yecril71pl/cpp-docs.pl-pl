---
title: Domyślna przestrzeń nazw
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: ffea9e1132b4c66f38661392cbafb94635b318e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558729"
---
# <a name="default-namespace"></a>Domyślna przestrzeń nazw

`default` Przestrzeni nazw zakresów wbudowanych typów, które są obsługiwane przez C + +/ CX.

## <a name="syntax"></a>Składnia

```
namespace default;
```

### <a name="members"></a>Elementy członkowskie

Wszystkie typy wbudowane dziedziczyć następujące elementy członkowskie.

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Zwraca kod skrótu dla tego wystąpienia.|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Zwraca ciąg reprezentujący bieżącego typu.|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Zwraca ciąg reprezentujący bieżącego typu.|

### <a name="built-in-types"></a>Typy wbudowane

|Nazwa|Opis|
|----------|-----------------|
|`char16`|16-bitową liczbą wartość reprezentuje punkt kodu Unicode (UTF-16).|
|`float32`|Liczba zmiennoprzecinkowa IEEE 754 32-bitowych.|
|`float64`|Liczba zmiennoprzecinkowa IEEE 754 64-bitowych.|
|`int16`|Całkowita 16-bitowych.|
|`int32`|Całkowita 32-bitowych.|
|`int64`|Całkowita 64-bitowych.|
|`int8`|8-bitowe podpisane wartość liczbowa.|
|`uint16`|16-bitowa liczba całkowita bez znaku.|
|`uint32`|32-bitowa liczba całkowita bez znaku.|
|`uint64`|64-bitowej nieoznaczonej liczby całkowitej.|
|`uint8`|8-bitową wartością numeryczną bez znaku.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** vccorlib.h

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)