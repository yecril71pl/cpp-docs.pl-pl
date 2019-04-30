---
title: Definicje dla podsumowania dotyczącego gramatyki
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 6e8671ba0d68b13f68db0f2b08dab4fe98f917e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389284"
---
# <a name="definitions-for-the-grammar-summary"></a>Definicje dla podsumowania dotyczącego gramatyki

Terminale to punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zbiór słów zastrzeżonych oraz identyfikatorów zdefiniowanych przez użytkownika.

Symboli nieterminalnych symboli zastępczych w składni. Większość są definiowane w innych miejscach w tej składni podsumowania. Definicje mogą być cykliczne. Następujące symboli nieterminalnych są zdefiniowane w [konwencje leksykalne](../cpp/lexical-conventions.md) części *C++ Language Reference*:

`constant`, *wyrażenie_stałe*, *identyfikator*, *— słowo kluczowe*, `operator`, `punctuator`

Opcjonalny składnik jest wskazywany przez indeksem <sub>zoptymalizowany pod kątem</sub>. Na przykład następujące określa opcjonalne wyrażenie ujęte w nawiasy klamrowe:

**{** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **}**

## <a name="see-also"></a>Zobacz także

[Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)