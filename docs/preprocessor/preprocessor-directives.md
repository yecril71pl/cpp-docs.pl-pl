---
title: Dyrektywy preprocesora
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: ac765d33aec4795e94866c097d6c453dbd0e4a08
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845331"
---
# <a name="preprocessor-directives"></a>Dyrektywy preprocesora

Dyrektywy preprocesora, takie jak `#define` i `#ifdef` , są zwykle używane do łatwego zmieniania i łatwego kompilowania programów źródłowych w różnych środowiskach wykonawczych. Dyrektywy w pliku źródłowym umożliwiają preprocesorowi podjęcie określonych działań. Na przykład preprocesor może zastąpić tokeny w tekście, wstawić zawartość innych plików do pliku źródłowego lub pominąć kompilację części pliku, usuwając sekcje tekstu. Wiersze preprocesora są rozpoznawane i przeprowadzane przed rozwinięciem makra. W związku z tym, jeśli makro zostanie rozwinięte do elementu, który wygląda jak polecenie preprocesora, nie jest rozpoznawane przez preprocesor.

Instrukcje preprocesora używają tego samego zestawu znaków jako instrukcji pliku źródłowego, z wyjątkiem tego, że sekwencje unikowe nie są obsługiwane. Zestaw znaków używany w instrukcjach preprocesora jest taki sam jak zestaw znaków wykonania. Preprocesor rozpoznaje również wartości ujemnych znaków.

Preprocesor rozpoznaje następujące dyrektywy:

:::row:::
   :::column span="":::
      [`#define`](../preprocessor/hash-define-directive-c-cpp.md)\
      [`#elif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#else`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#endif`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#error`](../preprocessor/hash-error-directive-c-cpp.md)\
      [`#if`](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)\
      [`#ifdef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)\
      [`#ifndef`](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#import`](../preprocessor/hash-import-directive-cpp.md)\
      [`#include`](../preprocessor/hash-include-directive-c-cpp.md)\
      [`#line`](../preprocessor/hash-line-directive-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`#pragma`](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
      [`#undef`](../preprocessor/hash-undef-directive-c-cpp.md)\
      [`#using`](../preprocessor/hash-using-directive-cpp.md)
   :::column-end:::
:::row-end:::

Numer ( `#` ) musi być pierwszym znakiem niebiałym w wierszu zawierającym dyrektywę. Znaki odstępu mogą występować między znakiem numeru a pierwszą literą dyrektywy. Niektóre dyrektywy zawierają argumenty lub wartości. Każdy tekst, który następuje po dyrektywie (z wyjątkiem argumentu lub wartości będącej częścią dyrektywy) musi być poprzedzony przez ogranicznik komentarza jednowierszowego ( `//` ) lub ujęty w ograniczniki komentarza ( `/* */` ). Wiersze zawierające dyrektywy preprocesora można kontynuować, bezpośrednio poprzedzając znacznik końca wiersza z ukośnikiem odwrotnym ( `\` ).

Dyrektywy preprocesora mogą znajdować się w dowolnym miejscu w pliku źródłowym, ale mają zastosowanie tylko do reszty pliku źródłowego.

## <a name="see-also"></a>Zobacz też

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)\
[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)\
[Dokumentacja preprocesora języka c/c++](../preprocessor/c-cpp-preprocessor-reference.md)
