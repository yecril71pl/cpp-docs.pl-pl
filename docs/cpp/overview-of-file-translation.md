---
title: "Przegląd tłumaczenia pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a088d2da30aa77f477f3f6e5064b6b98170e953b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-file-translation"></a>Przegląd tłumaczenia pliku
Programy napisane w języku C++ (podobnie jak programy napisane w języku C), składają się z co najmniej jednego pliku. Każdy z tych plików jest tłumaczony w następującej, koncepcyjnej kolejności (rzeczywista kolejność postępuje zgodnie z regułą „jak gdyby”: tłumaczenie musi wystąpić, jak gdyby wykonano następujące kroki):  
  
1.  Tokenizowanie leksykalne. W tej fazie tłumaczenia wykonywane jest mapowanie znaków i przetwarzanie trójznaków, łączenie wierszy i tokenizowanie.  
  
2.  Przetwarzanie wstępne. Przełącza tej fazy tłumaczenia w plikach źródłowych pomocniczych odwołuje się `#include` dyrektywy, obsługuje "tworzenia ciągów" i "konwersji na znaki" dyrektywy i wykonuje tokenu rozszerzenia wklejanie i makra (zobacz [dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) w *odwołania preprocesora* Aby uzyskać więcej informacji). Wynikiem fazy przetwarzania wstępnego jest sekwencja tokenów, które razem definiują „jednostkę translacji”.  
  
     Dyrektywy preprocesora zawsze zaczynać się od znaku numeru (**#**) znaków (to znaczy pierwszego znaku niebiałym znakiem w wierszu musi być znak liczby). Tylko jedna dyrektywa preprocesora może pojawić się w danym wierszu. Na przykład:  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  Generowanie kodu. Ta faza tłumaczenia używa tokenów wygenerowanych w fazie przetwarzania wstępnego, aby wygenerować kod obiektu.  
  
     Podczas tej fazy wykonywana jest syntaktyczna i semantyczna kontrola kodu źródłowego.  
  
 Zobacz [fazy tłumaczenia](../preprocessor/phases-of-translation.md) w *odwołania preprocesora* Aby uzyskać więcej informacji.  
  
 Preprocesor języka C++ jest ścisłym rozszerzeniem preprocesora standardu ANSI C, jednak różni się on w kilku przypadkach. Poniższa lista opisuje kilka różnic między preprocesorami standardów ANSI C i C++:  
  
-   Obsługiwane są komentarze jednowierszowe. Zobacz [komentarze](../cpp/comments-cpp.md) Aby uzyskać więcej informacji.  
  
-   Jeden wstępnie zdefiniowanego makra, **__cplusplus —**, jest zdefiniowana tylko dla języka C++. Zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md) w *odwołania preprocesora* Aby uzyskać więcej informacji.  
  
-   Preprocesora C nie rozpoznaje operatory C++: **.\*** ,  **-> \*** , i `::`. Zobacz [operatory](../cpp/cpp-built-in-operators-precedence-and-associativity.md) i [wyrażenia](../cpp/expressions-cpp.md), aby uzyskać więcej informacji na temat operatorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)