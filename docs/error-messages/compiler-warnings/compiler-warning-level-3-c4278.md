---
title: Kompilator ostrzeżenie (poziom 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627633"
---
# <a name="compiler-warning-level-3-c4278"></a>Kompilator ostrzeżenie (poziom 3) C4278

> "*identyfikator*": identyfikator w bibliotece typów "*tlb*" jest już makrem; Użyj kwalifikatora "rename"

Korzystając z [#import](../../preprocessor/hash-import-directive-cpp.md), identyfikator w bibliotece typów importujesz próbuje zadeklarować identyfikatora *identyfikator*. Jest to jednak już prawidłowy symbol.

Użyj `#import` **Zmień nazwę** atrybutu, aby przypisać aliasu do symbolu w bibliotece typów.