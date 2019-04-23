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
ms.openlocfilehash: c73a90aa2be83d643b74dde4645081e89da3ff73
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037935"
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

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)