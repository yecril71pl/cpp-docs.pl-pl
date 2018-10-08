---
title: Przegląd tłumaczenia pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0aa647f6f94d31f1a06bb09b143554dba51b68
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861749"
---
# <a name="overview-of-file-translation"></a>Przegląd tłumaczenia pliku

Programy napisane w języku C++ (podobnie jak programy napisane w języku C), składają się z co najmniej jednego pliku. Każdy z tych plików jest tłumaczony w następującej, koncepcyjnej kolejności (rzeczywista kolejność postępuje zgodnie z regułą „jak gdyby”: tłumaczenie musi wystąpić, jak gdyby wykonano następujące kroki):

1. Tokenizowanie leksykalne. W tej fazie tłumaczenia wykonywane jest mapowanie znaków i przetwarzanie trójznaków, łączenie wierszy i tokenizowanie.

1. Przetwarzanie wstępne. Ta faza tłumaczenia wprowadza pomocnicze pliki źródłowe odwołuje się `#include` dyrektyw, obsługuje "tworzenia ciągów" i "konwersji na znaki" dyrektywy i przeprowadza token wklejanie i rozwijanie makr (zobacz [dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) w *Preprocessor Reference* Aby uzyskać więcej informacji). Wynikiem fazy przetwarzania wstępnego jest sekwencja tokenów, które razem definiują „jednostkę translacji”.

   Dyrektywy preprocesora zawsze zaczynają się od znaku numeru (**#**) znak (oznacza to, że pierwszym niebiałym znakiem w wierszu musi być znakiem numeru). Tylko jedna dyrektywa preprocesora może pojawić się w danym wierszu. Na przykład:

    ```cpp
    #include <iostream>  // Include text of iostream in
                         //  translation unit.
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty
                         //  text string).
    ```

1. Generowanie kodu. Ta faza tłumaczenia używa tokenów wygenerowanych w fazie przetwarzania wstępnego, aby wygenerować kod obiektu.

   Podczas tej fazy wykonywana jest syntaktyczna i semantyczna kontrola kodu źródłowego.

Zobacz [etapy translacji](../preprocessor/phases-of-translation.md) w *Preprocessor Reference* Aby uzyskać więcej informacji.

Preprocesor języka C++ jest ścisłym rozszerzeniem preprocesora standardu ANSI C, jednak różni się on w kilku przypadkach. Poniższa lista opisuje kilka różnic między preprocesorami standardów ANSI C i C++:

- Obsługiwane są komentarze jednowierszowe. Zobacz [komentarze](../cpp/comments-cpp.md) Aby uzyskać więcej informacji.

- Jedno wstępnie zdefiniowane makro, `__cplusplus`, jest zdefiniowana tylko dla języka C++. Zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md) w *Preprocessor Reference* Aby uzyskać więcej informacji.

- Preprocesor języka C nie rozpoznaje operatorów języka C++: **.** <strong>\*</strong>, **->** <strong>\*</strong>, i **::**. Zobacz [operatory](../cpp/cpp-built-in-operators-precedence-and-associativity.md) i [wyrażeń](../cpp/expressions-cpp.md), aby uzyskać więcej informacji dotyczących operatorów.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)
