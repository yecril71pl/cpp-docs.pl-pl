---
title: Operatory rzutowania
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 606e8b159bb7bdb7527d33a5211cb33a26913754
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221825"
---
# <a name="casting-operators"></a>Operatory rzutowania

Istnieje kilka operatorów rzutowania specyficznych dla języka C++. Te operatory są przeznaczone do usuwania niektórych niejednoznaczności i niebezpieczeństwa związanych ze starym stylem rzutowania języka C. Są to następujące operatory:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Używane do konwersji typów polimorficznych.

- [static_cast](../cpp/static-cast-operator.md) Używane do konwersji typów niepolimorficznych.

- [const_cast](../cpp/const-cast-operator.md) Służy do usuwania **`const`** atrybutów, **`volatile`** i **`__unaligned`** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Używane do prostej interpretacji bitów.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Używane w języku C++/CLI do tworzenia zweryfikowanych MSIL.

Użyj **`const_cast`** i **`reinterpret_cast`** jako ostatni z nich, ponieważ te operatory mają takie same zagrożenia, jak w przypadku starych stylów. Jednak nadal są one niezbędne w celu całkowitego zastąpienia starych stylów.

## <a name="see-also"></a>Zobacz także

[Rzutowanie](../cpp/casting.md)
