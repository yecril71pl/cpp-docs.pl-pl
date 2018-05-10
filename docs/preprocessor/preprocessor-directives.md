---
title: Dyrektywy preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b73f6ce579f94d38621820a63888dc0aa5a75863
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor-directives"></a>Dyrektywy preprocesora
Dyrektywy preprocesora, takich jak `#define` i **#ifdef**, zwykle służą do programy źródłowe łatwo zmienić i łatwa do kompilacji w środowiskach różnych wykonywania. Dyrektywy w pliku źródłowym Poinformuj preprocesora do wykonywania określonych akcji. Na przykład preprocesora można zastąpić tokenów w tekście, Wstaw zawartość innych plików do pliku źródłowego lub pominąć kompilacji części pliku przez usunięcie fragmentów tekstu. Rozpoznany i przeprowadzić przed rozwinięciu makra preprocesora wierszy. W związku z tym jeśli makra rozwija na rzecz, która wygląda jak polecenie preprocesora, to polecenie nie jest rozpoznawany przez preprocesora.  
  
 Instrukcje preprocesora używać tego samego znaku Ustaw jako instrukcje pliku źródłowego, z wyjątkiem sekwencji ucieczki nie są obsługiwane. Zestaw znaków używany w instrukcjach preprocesora jest taka sama jak [zestaw znaków wykonania](http://msdn.microsoft.com/en-us/a7901c61-524d-47c6-beb6-d9dacc2e72ed). Preprocesora również rozpoznaje wartości ujemnej znaków.  
  
 Preprocesora rozpoznaje następujące dyrektywy:  
  
|||||  
|-|-|-|-|  
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|  
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 Znak liczby (**#**) musi być pierwszym znakiem niebiałym znakiem w wierszu zawierających dyrektywy; między znak liczby i pierwszą literę dyrektywy może występować białe znaki. Niektóre dyrektywy obejmują argumentów lub wartości. Tekst, który wykonuje dyrektywy (z wyjątkiem argument lub wartość, która jest częścią dyrektywy) musi być poprzedzona ogranicznik jednowierszowego komentarza (**//**) lub w ograniczników do komentarzy ( **/ \* \*/**). Wierszy zawierających dyrektywy preprocesora może być kontynuowane przez bezpośrednio przed znakiem kreski ułamkowej odwróconej znacznika końca wiersza (**\\**).  
  
 Dyrektywy preprocesora może występować w dowolnym miejscu w pliku źródłowym, ale mają one zastosowanie tylko do pozostałej części pliku źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory preprocesora](../preprocessor/preprocessor-operators.md)   
 [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)   
 [Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)