---
title: Funkcja deklaracje i definicje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb5a6b1f184775b3e67a03b9544e609b33673ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106132"
---
# <a name="function-declarations-and-definitions"></a>Deklaracje i definicje funkcji

Prototypy funkcji ustanowić nazwę funkcji, jego typ zwracany i typ i liczbę jej parametrów formalnych. Definicja funkcji zawiera treści funkcji.

## <a name="remarks"></a>Uwagi

Deklaracje funkcji i zmiennej może znajdować się wewnątrz lub na zewnątrz definicji funkcji. Każde oświadczenie, w ramach definicji funkcji jest nazywany pojawiają się na poziomie "internal" lub "local". Deklaracja poza wszystkie definicje funkcji jest nazywany pojawiają się na poziomie "file zakresu" lub "zewnętrzne" "globalne,". Definicje zmiennych, takich jak deklaracje, mogą być wyświetlane na poziomie wewnętrznym (w ramach definicji funkcji) lub na poziomie zewnętrznym (poza wszystkie definicje funkcji). Definicje funkcji są zawsze wykonywane na poziomie zewnętrznym. Definicje funkcji są omówione w dalszych [definicje funkcji](../c-language/c-function-definitions.md). Prototypy funkcji są objęte [prototypy funkcji](../c-language/function-prototypes.md).

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)