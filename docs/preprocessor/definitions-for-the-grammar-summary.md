---
title: Definicje dla podsumowania dotyczącego gramatyki
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 133000c0cc8ef636a3f9752d2f6fc7f1934bd831
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521129"
---
# <a name="definitions-for-the-grammar-summary"></a>Definicje dla podsumowania dotyczącego gramatyki

Terminale to punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zbiór słów zastrzeżonych oraz identyfikatorów zdefiniowanych przez użytkownika.

Symboli nieterminalnych symboli zastępczych w składni. Większość są definiowane w innych miejscach w tej składni podsumowania. Definicje mogą być cykliczne. Następujące symboli nieterminalnych są zdefiniowane w [konwencje leksykalne](../cpp/lexical-conventions.md) części *C++ Language Reference*:

`constant`, *wyrażenie_stałe*, *identyfikator*, *— słowo kluczowe*, `operator`, `punctuator`

Opcjonalny składnik jest wskazywany przez indeksem <sub>zoptymalizowany pod kątem</sub>. Na przykład następujące określa opcjonalne wyrażenie ujęte w nawiasy klamrowe:

**{** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **}**

## <a name="see-also"></a>Zobacz też

[Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)