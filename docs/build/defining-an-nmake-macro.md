---
title: Definiowanie makro NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c266a0be1c5ff16b719e9055f79b377d13ffbf3c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715717"
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