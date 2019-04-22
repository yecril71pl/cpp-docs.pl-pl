---
title: Gramatyka preprocesora
ms.date: 09/04/2018
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: 6177cf5fddba549e410842ef3f270edcc13d4782
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032417"
---
# <a name="preprocessor-grammar"></a>Gramatyka preprocesora

*control-line*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identyfikator* *ciąg tokenu*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identyfikator</em>**(** *identyfikator*<sub>zoptymalizowany pod kątem</sub> **,** ... **,** *identyfikator*<sub>zoptymalizowany pod kątem</sub> **)** *ciąg tokenu*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *path-spec* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *path-spec* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *digit-sequence*  **"** *filename* **"**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *ciąg tokenu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *ciąg tokenu*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zdefiniowany (** *identyfikator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**definicja** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Dowolne wyrażenie stałej

*warunkowe* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*część IF* *części elif*<sub>zoptymalizowany pod kątem</sub> *część else*<sub>zoptymalizowany pod kątem</sub> *linia endif*

*część IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wiersz z operatorem IF* *tekstu*

*wiersz z operatorem IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *wyrażenia stałego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identyfikator*

*części elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Linia elif* *tekstu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*części elif* *linii elif* *tekstu*

*Linia elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *constant-expression*

*część else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*else linii* *tekstu*

*else linii* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*Linia ENDIF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*sekwencja cyfr* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*cyfra* : jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token ciągu* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ciąg tokenów

*Token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stałe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*znak interpunkcyjny*

*Nazwa pliku* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;System operacyjny prawne, nazwa_pliku

*PATH-spec* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ścieżka pliku prawne

*tekst* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Dowolną sekwencją tekstu

> [!NOTE]
> Następujące symboli nieterminalnych są rozwijane w [konwencje leksykalne](../cpp/lexical-conventions.md) części *C++ Language Reference*: *stałej*, *wyrażenia stałego* , *identyfikator*, *— słowo kluczowe*, *operator*, i *znak interpunkcyjny*.

## <a name="see-also"></a>Zobacz także

[Podsumowanie gramatyki (C/C++)](../preprocessor/grammar-summary-c-cpp.md)