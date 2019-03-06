---
title: Definiowanie makro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 6eb7c2f7759bda21f1424cef91b1dc814ba8d8ba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424109"
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

## <a name="see-also"></a>Zobacz także

[Makra i NMAKE](../build/macros-and-nmake.md)
