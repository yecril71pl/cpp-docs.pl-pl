---
title: Komentarze (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 828d02ddd02c7484e142333bdb87453f8fb922e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comments-c"></a>Komentarze (C++)
Komentarz jest tekst, który ignoruje kompilator, ale jest to przydatny dla programistów. Komentarze są zwykle używane do adnotacji kodu do użytku w przyszłości. Kompilator traktowane jako biały znak. Komentarze podczas testowania można użyć do dezaktywowania niektórych wierszy kodu; jednak `#if` / `#endif` dyrektywy preprocesora dostosowując to ponieważ można ująć kod, który zawiera komentarze, ale nie można zagnieżdżać komentarze.  
  
 Komentarz C++ są zapisywane w jednym z następujących sposobów:  
  
-   `/*` (Ukośnika, gwiazdka) znaki, po których każda sekwencja znaków (w tym nowe wiersze), następuje `*/` znaków. Ta składnia jest taka sama jak ANSI c  
  
-   `//` Znaki (dwa ukośniki), po których dowolnej sekwencji znaków. Nowy wiersz nie natychmiast poprzedzony ukośnikiem kończy ten formularz komentarza. W związku z tym jest często nazywana "komentarz jednowierszowy".  
  
 Znaki komentarza (`/*`, `*/`, i `//`) mają nie specjalne znaczenie w w stałej znakowej literał ciągu lub komentarz. Komentarze przy użyciu składni pierwszy, dlatego nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)