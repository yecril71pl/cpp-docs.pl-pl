---
title: region, endregion, pragmy
ms.date: 08/29/2019
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
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222375"
---
# <a name="region-endregion-pragmas"></a>region, endregion, pragmy

`#pragma region`umożliwia określenie bloku kodu, który można rozwijać lub zwijać podczas korzystania z funkcji tworzenia [konspektu](/visualstudio/ide/outlining) edytora Visual Studio Code.

## <a name="syntax"></a>Składnia

> **region #pragma** *Nazwa*\
> **#pragma endregion** *komentarz*

### <a name="parameters"></a>Parametry

*komentować*\
Obowiązkowe Komentarz, który ma być wyświetlany w edytorze kodu.

*Nazwij*\
Obowiązkowe Nazwa regionu. Ta nazwa jest wyświetlana w edytorze kodu.

## <a name="remarks"></a>Uwagi

`#pragma endregion`oznacza koniec `#pragma region` bloku.

Blok musi być zakończony `#pragma endregion` przez dyrektywę. `#region`

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

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
