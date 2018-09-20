---
title: Dyrektywy preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 3835d3c3d2900b97c16bc82963df2d08f35a879d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416295"
---
# <a name="preprocessor-directives"></a>Dyrektywy preprocesora

Dyrektywy preprocesora, takich jak `#define` i `#ifdef`, są zazwyczaj używane do ułatwienia wprowadzania programach źródłowych zmian oraz prowadzenia łatwej kompilacji w różnych środowiskach wykonawczych. Dyrektywy w pliku źródłowym każą preprocesorowi wykonać określone czynności. Na przykład preprocesor można zamienić tokeny w tekście, wstawić zawartość innych plików do pliku źródłowego lub pomijanie kompilacji części pliku poprzez usunięcie fragmentów tekstu. Linie preprocesora są rozpoznawane i przeprowadzane przed rozwinięciem makra. W związku z tym Jeżeli makro rozszerzy się na coś, co przypomina polecenie preprocesora, to polecenie nie jest rozpoznawane przez preprocesor.

Instrukcje preprocesora używają ten sam zestaw znaków jak instrukcje pliku źródłowego, z wyjątkiem, że sekwencje ucieczki nie są obsługiwane. Zestaw znaków używanych w instrukcjach preprocesora jest taki sam jak zestaw znaków wykonania. Preprocesor rozpoznaje również ujemne wartości.

Preprocesor rozpoznaje poniższe dyrektywy:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

Znak numeru (**#**) musi być pierwszym niebiałym znakiem w wierszu zawierającym dyrektywę; białe znaki mogą występować między znakiem liczby i pierwszą literą dyrektywy. Niektóre dyrektywy zawierają argumenty lub wartości. Dowolny tekst, który następuje po dyrektywie (chyba że argument lub wartość, która jest częścią dyrektywy) musi być poprzedzona ogranicznikiem komentaraz jednowierszowego (**//**) lub ujęta w ograniczniki komentarza ( __/ \*\*/__). Wiersze zawierające dyrektywy preprocesora mogą być kontynuowane, bezpośrednio poprzedzających znacznika końca wiersza znakiem kreski ułamkowej odwróconej (**\\**).

Dyrektywy preprocesora mogą występować w dowolnym miejscu w pliku źródłowym, ale mają zastosowanie tylko do pozostałej części pliku źródłowego.

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)<br/>
[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)<br/>
[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)  
