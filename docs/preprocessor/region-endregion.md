---
title: region, endregion
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: efc5f9c09449ff2fefff41261fe8b0eb0be80278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512813"
---
# <a name="region-endregion"></a>region, endregion

`#pragma region` Pozwala określić bloku kodu, który można rozwinąć lub zwinąć, korzystając z [konspekt funkcji](/visualstudio/ide/outlining) Edytor kodu programu Visual Studio.

## <a name="syntax"></a>Składnia

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>Parametry

*Komentarz*<br/>
(Opcjonalnie) Komentarz, która będzie wyświetlana w edytorze kodu.

*Nazwa*<br/>
(Opcjonalnie) Nazwa regionu.  Ta nazwa będzie wyświetlana w edytorze kodu.

## <a name="remarks"></a>Uwagi

`#pragma endregion` oznacza koniec `#pragma region` bloku.

A `#region` musi się kończyć bloku `#pragma endregion`.

## <a name="example"></a>Przykład

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)