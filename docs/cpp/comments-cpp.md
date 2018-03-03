---
title: Komentarze (C++) | Dokumentacja firmy Microsoft
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
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 482b9f2f3d9917466becff3f2c9bf9fea6f599f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comments-c"></a>Komentarze (C++)
Komentarz jest tekst, który ignoruje kompilator, ale jest to przydatny dla programistów. Komentarze są zwykle używane do adnotacji kodu do użytku w przyszłości. Kompilator traktowane jako biały znak. Komentarze podczas testowania można użyć do dezaktywowania niektórych wierszy kodu; jednak `#if` / `#endif` dyrektywy preprocesora dostosowując to ponieważ można ująć kod, który zawiera komentarze, ale nie można zagnieżdżać komentarze.  
  
 Komentarz C++ są zapisywane w jednym z następujących sposobów:  
  
-   `/*` (Ukośnika, gwiazdka) znaki, po których każda sekwencja znaków (w tym nowe wiersze), następuje `*/` znaków. Ta składnia jest taka sama jak ANSI c  
  
-   `//` Znaki (dwa ukośniki), po których dowolnej sekwencji znaków. Nowy wiersz nie natychmiast poprzedzony ukośnikiem kończy ten formularz komentarza. W związku z tym jest często nazywana "komentarz jednowierszowy".  
  
 Znaki komentarza (`/*`, `*/`, i `//`) mają nie specjalne znaczenie w w stałej znakowej literał ciągu lub komentarz. Komentarze przy użyciu składni pierwszy, dlatego nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)