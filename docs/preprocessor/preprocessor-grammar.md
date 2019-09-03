---
title: Gramatyka preprocesora
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222259"
---
# <a name="preprocessor-grammar"></a>Gramatyka preprocesora

*wiersz kontrolny*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *Identyfikator* *token — ciąg* <sub>wybór</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *Identyfikator* **(** &#x2800;&#x200B;<sub>wybór</sub> identyfikatora **,** ... **,** *Identyfikator* &#x200B;&#x2800; <sub>opt</sub>—<sub>wybór</sub> *ciągu tokenu*\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _ścieżka — Specyfikacja_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** _ścieżka — Specyfikacja_ **\<** **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *sekwencja cyfr* **"** _Nazwa pliku_ **"** &#x200B; <sub>wybór</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token — ciąg*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token — ciąg*

*wyrażenie stałe*: \
&nbsp;&nbsp;&nbsp;&nbsp;**zdefiniowane (** &#x2800;*Identyfikator*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**zdefiniowane** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp;dowolne inne wyrażenie stałe

*warunkowo*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-Part* *elif — części* <sub>wybór</sub> *else-część* <sub>wybór</sub> *endif-line*

*if-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-line* *tekst*

*if-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *wyrażenie stałe*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *Identyfikator*

*elif — części*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif-line* *tekst*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif — części* *elif-line* *tekst*

*elif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *wyrażenie stałe*

*else-część*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else — wiersz* *tekst*

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*sekwencja cyfr*: \
&nbsp;&nbsp;&nbsp;&nbsp;*kontrol*\
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *cyfra*

*cyfra*: jeden z \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-String*: \
&nbsp;&nbsp;&nbsp;&nbsp;Ciąg tokenów

*token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*kodu*\
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*\
&nbsp;&nbsp;&nbsp;&nbsp;*stałego*\
&nbsp;&nbsp;&nbsp;&nbsp;*zakład*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*Nazwa pliku*: \
&nbsp;&nbsp;&nbsp;&nbsp;Nazwa pliku legalnego systemu operacyjnego

*ścieżka — Specyfikacja*: \
&nbsp;&nbsp;&nbsp;&nbsp;Legalna ścieżka pliku

*tekst*: \
&nbsp;&nbsp;&nbsp;&nbsp;Dowolna sekwencja tekstu

> [!NOTE]
> Następujące elementy niebędące terminalami są rozwinięte w sekcji [konwencje leksykalne](../cpp/lexical-conventions.md) w  *C++ dokumentacji języka*: *stała*, *stała — wyrażenie*, *Identyfikator*, *słowo kluczowe*, *operator*i  *punctuator*.

## <a name="see-also"></a>Zobacz także

[Podsumowanie gramatyki (CC++/)](../preprocessor/grammar-summary-c-cpp.md)
