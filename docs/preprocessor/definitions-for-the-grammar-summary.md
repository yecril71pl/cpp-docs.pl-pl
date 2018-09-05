---
title: Definicje dla podsumowania dotyczącego gramatyki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c11f2f839ef806d74eae65c9fc8fe3a71cd2e9c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760822"
---
# <a name="definitions-for-the-grammar-summary"></a>Definicje dla podsumowania dotyczącego gramatyki

Terminale to punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zbiór słów zastrzeżonych oraz identyfikatorów zdefiniowanych przez użytkownika.

Symboli nieterminalnych symboli zastępczych w składni. Większość są definiowane w innych miejscach w tej składni podsumowania. Definicje mogą być cykliczne. Następujące symboli nieterminalnych są zdefiniowane w [konwencje leksykalne](../cpp/lexical-conventions.md) części *C++ Language Reference*:

`constant`, *wyrażenie_stałe*, *identyfikator*, *— słowo kluczowe*, `operator`, `punctuator`

Opcjonalny składnik jest wskazywany przez indeksem <sub>zoptymalizowany pod kątem</sub>. Na przykład następujące określa opcjonalne wyrażenie ujęte w nawiasy klamrowe:

**{** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **}**

## <a name="see-also"></a>Zobacz też

[Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)