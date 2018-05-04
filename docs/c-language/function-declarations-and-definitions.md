---
title: Deklaracje i definicje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 704e8defa8aac640ce5011e5789d4af36380b7a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="function-declarations-and-definitions"></a>Deklaracje i definicje funkcji
Prototypy funkcji ustanowić nazwę funkcji, jego typ zwracany i typ i numer jego parametrów formalnych. Definicja funkcji zawiera treść funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Deklaracje zarówno funkcja i zmienna może występować wewnątrz lub na zewnątrz definicji funkcji. Żadnych deklaracji w definicji funkcji jest nazywany pojawiają się na poziomie "internal" lub "local". Deklaracja poza wszystkie definicje funkcji jest nazywany pojawiają się na poziomie "plik zakresu" lub "zewnętrzne" "globalne". Definicje zmiennych, takich jak deklaracje, może występować na poziomie wewnętrznym (w ramach definicji funkcji) lub na poziomie zewnętrzne (poza wszystkie definicje funkcji). Definicje funkcji są zawsze wykonywane na poziomie zewnętrznych. Definicje funkcji są omówione w dalszych [definicje funkcji](../c-language/c-function-definitions.md). Prototypy funkcji są objęte [prototypy funkcji](../c-language/function-prototypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)