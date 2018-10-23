---
title: region, endregion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e360009eb9126604d4466daed2445c7dfc582d4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808072"
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