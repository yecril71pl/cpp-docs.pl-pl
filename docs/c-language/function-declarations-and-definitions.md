---
title: Deklaracje i definicje funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
ms.openlocfilehash: 1f533bad308a9bc892bfe928b581c4b7197cf6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624036"
---
# <a name="function-declarations-and-definitions"></a>Deklaracje i definicje funkcji

Prototypy funkcji ustanowić nazwę funkcji, jego typ zwracany i typ i liczbę jej parametrów formalnych. Definicja funkcji zawiera treści funkcji.

## <a name="remarks"></a>Uwagi

Deklaracje funkcji i zmiennej może znajdować się wewnątrz lub na zewnątrz definicji funkcji. Każde oświadczenie, w ramach definicji funkcji jest nazywany pojawiają się na poziomie "internal" lub "local". Deklaracja poza wszystkie definicje funkcji jest nazywany pojawiają się na poziomie "file zakresu" lub "zewnętrzne" "globalne,". Definicje zmiennych, takich jak deklaracje, mogą być wyświetlane na poziomie wewnętrznym (w ramach definicji funkcji) lub na poziomie zewnętrznym (poza wszystkie definicje funkcji). Definicje funkcji są zawsze wykonywane na poziomie zewnętrznym. Definicje funkcji są omówione w dalszych [definicje funkcji](../c-language/c-function-definitions.md). Prototypy funkcji są objęte [prototypy funkcji](../c-language/function-prototypes.md).

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)