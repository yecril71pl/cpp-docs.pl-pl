---
title: Preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb5a9740bab3f69ff66a51cd58e6e1378e178f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor"></a>Preprocesor
Preprocesora jest procesora tekstu, który operuje tekst pliku źródłowego w ramach pierwszej fazy tłumaczenia. Preprocesora nie analizuje tekst źródłowy, ale go Podziel je na tokeny na potrzeby lokalizowanie makro wywołania. Mimo że kompilator wywołuje zwykle preprocesora w jego pierwszym przebiegu, preprocesora również można wywołać oddzielnie przetwarzania tekstu bez kompilowania.  
  
 Materiałów referencyjnych na preprocesora zawiera następujące sekcje:  
  
-   [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)  
  
-   [Operatory preprocesora](../preprocessor/preprocessor-operators.md)  
  
-   [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)  
  
-   [Pragmy](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
  
 **Microsoft Specific**  
  
 Możesz uzyskać dostęp do listy kodu źródłowego po przetwarzania wstępnego za pomocą [/E](../build/reference/e-preprocess-to-stdout.md) lub [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) — opcja kompilatora. Obie te opcje preprocesora wywołania i wyjściowych tekst wynikowy na urządzeniu standardowe dane wyjściowe, które w większości przypadków jest konsola. Jest to różnica między dwie opcje /E uwzględnia `#line` dyrektywy i /EP usuwa te dyrektywy wychodzących.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
##  <a name="_predir_special_terminology"></a> Terminologię  
 W dokumentacji preprocesora termin "argument" odnosi się do jednostki, która została przekazana do funkcji. W niektórych przypadkach jest modyfikowany przez "rzeczywiste" lub "formalnych" opisującą wyrażenie argumentu określonych w wywołaniu funkcji i deklaracji argument odpowiednio określone w definicji funkcji.  
  
 Termin "zmiennej" oznacza prosty obiekt danych typu C. Termin "obiektu" odnosi się do obiektów C++ i zmiennych; to pojęcie włącznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania preprocesora C/C++](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Fazy tłumaczenia](../preprocessor/phases-of-translation.md)