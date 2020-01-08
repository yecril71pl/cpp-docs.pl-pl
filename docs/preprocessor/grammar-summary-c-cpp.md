---
title: Podsumowanie gramatyki preprocesora (C/C++)
description: Definiuje i opisuje składnię preprocesoraC++ języka Microsoft C/COMPILER (MSVC).
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 99e7e8218a80e28d67767392cadfb5c4918a3bfe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302188"
---
# <a name="preprocessor-grammar-summary-cc"></a>Podsumowanie gramatyki preprocesora (C/C++)

W tym artykule opisano formalną gramatykę języka C i C++ preprocesora. Obejmuje ona składnię dyrektyw i operatorów przetwarzania wstępnego. Aby uzyskać więcej informacji, zobacz [preprocesora](../preprocessor/preprocessor.md) i [dyrektywy pragma oraz słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="definitions"></a>Definicje dla podsumowania gramatyki

Terminale są punktami końcowymi w definicji składni. Inne rozwiązanie nie jest możliwe. Terminale obejmują zestaw słów zarezerwowanych i identyfikatorów zdefiniowanych przez użytkownika.

Nieterminale są symbolami zastępczymi w składni. Większość jest definiowana w innym miejscu w tym podsumowaniu składni. Definicje mogą być cykliczne. Następujące elementy niebędące terminalami są zdefiniowane w sekcji [konwencje leksykalne](../cpp/lexical-conventions.md) w  *C++ dokumentacji języka*:

*stała*, *stała — wyrażenie*, *Identyfikator*, *słowo kluczowe*, *operator*, *punctuator*

Opcjonalny składnik jest wskazywany przez <sub>wybór</sub>z indeksu. Na przykład następująca składnia wskazuje opcjonalne wyrażenie ujęte w nawiasy klamrowe:

*wyrażenie*{<sub>opt</sub> **}**

## <a name="conventions"></a>Konwencje dokumentów

Konwencje używają różnych atrybutów czcionki dla różnych składników składni. Symbole i czcionki są następujące:

| Atrybut | Opis |
|---------------|-----------------|
| *nieterminal* | Typ kursywy oznacza nieterminale. |
| **#include** | Terminale w pogrubieniu są literałami zarezerwowanymi i symbolami, które muszą zostać wprowadzone jako pokazane. Znaki w tym kontekście zawsze uwzględniają wielkość liter. |
| <sub>opt</sub> | Nieterminale, po których następuje <sub>wybór</sub> , są zawsze opcjonalne.|
| domyślny krój czcionki | Znaki w zestawie opisany lub wymieniony w tym kroju pisma mogą być używane jako terminale w instrukcjach. |

Jest to dwukropek ( **:** ) po wprowadzeniu definicji przez nieterminala. Definicje alternatywne są wymienione w osobnych wierszach.

W blokach składni kodu te symbole w domyślnym kroju czcionki mają specjalne znaczenie:

| Symbol | Opis |
|---|---|
| \[] | Nawiasy kwadratowe otaczają opcjonalny element. |
| {\|} | Nawiasy klamrowe otoczone alternatywnymi elementami oddzielonymi pionowymi paskami. |
| ... | Wskazuje, że poprzedni wzorzec elementu może być powtórzony. |

W blokach składni kodu przecinki (`,`), kropki (`.`), średnika (`;`), dwukropek (`:`), nawiasy (`( )`), podwójne cudzysłowy (`"`) i apostrofy (`'`) są literałami.

## <a name="grammar"></a>Gramatyka preprocesora

*wiersz kontrolny*: \
&nbsp;&nbsp;&nbsp;&nbsp; *Identyfikator* #define *token —* <sub>wybór</sub> ciągu\
&nbsp;&nbsp;&nbsp;&nbsp;**Identyfikator #define** **(** <sub>wybór</sub> identyfikatora: **..** . **,** <sub>wybór</sub> identyfikatora —<sub>wybór</sub> *ciągu token*\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _path-spec_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _path-spec_ **>\**
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *cyfr-sekwencja* **"** _filename" (nazwa pliku_<sub>)\</sub>
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token-String*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-String*

*wyrażenie stałe*: \
&nbsp;&nbsp;&nbsp;&nbsp;**zdefiniowane (** *Identyfikator* **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**zdefiniowany** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp;dowolnym innym wyrażeniem stałym

*warunkowo*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-część* *elif-Parts*<sub>opt</sub> *-* <sub></sub> *line*

*if-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*tekstu* *if-line*

*if-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *wyrażenie stałe*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp; *Identyfikator* #ifndef

*elif — części*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif* *tekstu*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-części* *elif —* *tekst* wiersza

*elif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *wyrażenie stałe*

*else-część*: \
&nbsp;&nbsp;&nbsp;&nbsp; *tekst* wiersza

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*sekwencja cyfr*: \
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra*\
&nbsp;&nbsp;&nbsp;&nbsp; *cyfry* sekwencji

*cyfra*: jeden z \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-String*: \
&nbsp;&nbsp;&nbsp;&nbsp;ciągu tokenów

*token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*słowo kluczowe*\
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp;*stała*\
&nbsp;&nbsp;&nbsp;&nbsp;*operator*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*Nazwa pliku*: \
&nbsp;&nbsp;&nbsp;&nbsp;nazwa pliku prawnego systemu operacyjnego

*ścieżka — Specyfikacja*: \
&nbsp;&nbsp;&nbsp;&nbsp;

*tekst*: \
&nbsp;&nbsp;&nbsp;&nbsp;dowolnej sekwencji tekstu

> [!NOTE]
> Następujące elementy niebędące terminalami są rozwinięte w sekcji *C++* [konwencje leksykalne](../cpp/lexical-conventions.md) : *stała*, *stała — wyrażenie*, *Identyfikator*, *słowo kluczowe*, *operator*i *punctuator*.


## <a name="see-also"></a>Zobacz także

[Dokumentacja językaC++ C/preprocesora](../preprocessor/c-cpp-preprocessor-reference.md)
