---
title: Operatory rzutowania
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: eac274a0207be675b8d13532c3110c6e71bd55c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190106"
---
# <a name="casting-operators"></a>Operatory rzutowania

Istnieje kilka operatorów rzutowania specyficznych dla C++ języka. Te operatory są przeznaczone do usuwania niektórych niejednoznaczności i niebezpieczeństwa związanych ze starym stylem rzutowania języka C. Są to następujące operatory:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Używane do konwersji typów polimorficznych.

- [static_cast](../cpp/static-cast-operator.md) Używane do konwersji typów niepolimorficznych.

- [const_cast](../cpp/const-cast-operator.md) Służy do usuwania atrybutów **const**, **volatile**i **__unaligned** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Używane do prostej interpretacji bitów.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Używane w C++/CLI do tworzenia zweryfikowanych MSIL.

Użyj **const_cast** i **reinterpret_cast** jako ostatni z nich, ponieważ te operatory są takie same, jak w przypadku starych stylów. Jednak nadal są one niezbędne w celu całkowitego zastąpienia starych stylów.

## <a name="see-also"></a>Zobacz też

[Rzutowanie](../cpp/casting.md)
