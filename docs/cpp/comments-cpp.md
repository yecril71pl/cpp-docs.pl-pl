---
title: Komentarze (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a819c435135d2ee9c310f8fd4a5628d2d9d0acb1
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466816"
---
# <a name="comments-c"></a>Komentarze (C++)
Komentarz to tekst, który Kompilator ignoruje, ale jest to przydatne dla programistów. Komentarze są zwykle używane do Dodawanie adnotacji do kodu do użytku w przyszłości. Kompilator traktuje je jako biały znak. Komentarze w zakresie testowania można użyć do dezaktywowania pewnych linii kodu; jednak `#if` / `#endif` dyrektywy preprocesora usprawnieniu to ponieważ można otoczyć kod, który zawiera komentarze, ale nie można zagnieździć komentarzy.  
  
Komentarz C++ są zapisywane w jednym z następujących sposobów:  
  
-   `/*` (Ukośnika, gwiazdka) znaki, po których dowolnej sekwencji znaków (łącznie z nowych wierszy), a następnie `*/` znaków. Ta składnia jest taka sama jak ANSI C.  
  
-   `//` Znaków (dwa ukośniki), a następnie przez dowolną sekwencję znaków. Ta forma komentarz kończy się znakiem nowego wiersza nie od razu poprzedzone znakiem ukośnika odwrotnego. W związku z tym często jest nazywane "komentarz jednowierszowy".  
  
 Znaki komentarza (`/*`, `*/`, i `//`) mają nie specjalne znaczenie w w obrębie stałej znaku literał ciągu lub Dodaj komentarz. Komentarze przy użyciu składni pierwszy, dlatego nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz także  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)