---
title: Definiowanie makro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 860a5766e0d766f7426cb6c1a7eaf5db02686aa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499021"
---
# <a name="defining-an-nmake-macro"></a>Definiowanie makro NMAKE

## <a name="syntax"></a>Składnia

```

macroname=string
```

## <a name="remarks"></a>Uwagi

*Makra* składa się z litery, cyfry i znaki podkreślenia (_), maksymalnie 1024 znaki i jest przypadek wielkość liter. *Makra* może zawierać makra wywołana. Jeśli *makra* składa się całkowicie wywoływane makro — makro wywoływanej nie może być wartość null lub jest niezdefiniowany.

`string` Może być dowolną sekwencją zero lub więcej znaków. Pusty ciąg zawiera zero znaków lub tylko tabulacji lub spacji. `string` Może zawierać wywołanie makra.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Znaki specjalne w makrach](../build/special-characters-in-macros.md)

[Makra zerowe i niezdefiniowane](../build/null-and-undefined-macros.md)

[Miejsce definiowania makr](../build/where-to-define-macros.md)

[Pierwszeństwo w definicjach makr](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>Zobacz też

[Makra i NMAKE](../build/macros-and-nmake.md)