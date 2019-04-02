---
title: Operatory rzutowania
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: e2ac8e9079b1d30dca077363bbb6cef35960902e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768955"
---
# <a name="casting-operators"></a>Operatory rzutowania

Wiele operatorów rzutowania są specyficzne dla języka C++. Te operatory są przeznaczone do usunięcia części niejednoznaczności i zagrożenia związane z stare rzutowań języka C w stylu. Są to:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) używany na potrzeby konwersji polimorficzne typy.

- [static_cast](../cpp/static-cast-operator.md) używany na potrzeby konwersji typów niepolimorficznych.

- [Operator const_cast](../cpp/const-cast-operator.md) służy do usuwania **const**, **volatile**, i **__unaligned** atrybutów.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) używane dla prostych reinterpretation bitów.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) używany w języku C + +/ interfejsu wiersza polecenia, aby wygenerować podlegające weryfikacji MSIL.

Użyj **const_cast** i **reinterpret_cast** w ostateczności, ponieważ te operatory przedstawić same zagrożenia jako stary rzutowań w stylu. Jednak są nadal niezbędne w celu całkowitego zastąpienia starego rzutowań w stylu.

## <a name="see-also"></a>Zobacz także

[Rzutowanie](../cpp/casting.md)