---
title: Identyfikatory w języku C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 910e5cb8686130a08976d63f4cc54512da2494a1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751647"
---
# <a name="c-identifiers"></a>Identyfikatory języka C
"Identyfikatory" lub "symbole" są nazwami których dostarczenie dla zmiennych, typów, funkcji i etykiety w programie. Nazwy identyfikatorów muszą różnić się w pisowni i wielkości liter z dowolnego słowa kluczowego. Słowa kluczowe (C lub Microsoft) nie można używać jako identyfikatorów; są one zarezerwowane do użytku specjalne. Możesz utworzyć identyfikatora, określając je w deklaracji zmiennej, typu lub funkcji. W tym przykładzie `result` jest identyfikatorem zmienną całkowitoliczbową i `main` i `printf` to identyfikator nazwy funkcji.  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
Po zadeklarowaniu służy identyfikator w późniejszym instrukcjach program do odwoływania się do skojarzona wartość.  
  
Specjalnym rodzajem identyfikatora, zwanego etykiety instrukcji, mogą być używane w `goto` instrukcji. (Deklaracje są opisane w [deklaracje i typy](../c-language/declarations-and-types.md) etykiety instrukcji są opisane w [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md).)  
  
## <a name="syntax"></a>Składnia

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *nie cyfrą*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *cyfra*

*inny*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ h g b c d e f i "j" k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**B C D E F G H I "J" K L MN O P Q R S T U V W X Y Z**

*cyfra*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**
  
Pierwszym znakiem nazwy identyfikatora musi być `nondigit` (oznacza to, że pierwszym znakiem musi być znakiem podkreślenia lub małe i wielkie litery). ANSI umożliwia sześć znaczące znaków w nazwie zewnętrznego identyfikatora do 31. w nazwach identyfikatorów wewnętrzne (w funkcji). Zewnętrzne identyfikatory (te zadeklarowana w zakresie globalnym lub zadeklarowana z klasą magazynu `extern`) może podlegać dodatkowe ograniczenia nazewnictwa, ponieważ identyfikatory te muszą być przetwarzane przez inne oprogramowanie, takie jak wiązania.  
  
**Microsoft Specific**  
  
Mimo że ANSI umożliwia 6 znaków znaczących nazw zewnętrznego identyfikatora do 31. w nazwach identyfikatorów wewnętrzne (w funkcji), kompilator Microsoft C: umożliwia 247 znaków w nazwie identyfikatora wewnętrzne lub zewnętrzne. Jeśli nie masz danych dzięki zgodności z ANSI, można zmodyfikować to ustawienie domyślne numer mniejszy lub większy, za pomocą / h (Ograniczaj długość nazw zewnętrznych) opcji.  
  
**END specyficzny dla Microsoft**  
  
Kompilator języka C uwzględnia wielkie i małe litery jako różne znaki. Ta funkcja o nazwie "wielkość liter" umożliwia utworzenie unikatowych identyfikatorów, które mają taką samą pisownię ale różnych przypadków dla co najmniej jednej litery. Na przykład każda z następujących identyfikatorów jest unikatowa:  
  
```  
add  
ADD  
Add  
aDD  
```  
  
**Microsoft Specific**  
  
Nie należy wybierać nazw identyfikatorów, rozpoczynające się z dwoma podkreśleniami lub znakiem podkreślenia następuje wielką literą. Standard ANSI C umożliwia nazw identyfikatorów, które zaczynają się od kombinacji tych znaków, mają zostać zarezerwowane do użytku kompilatora. Identyfikatorów z zakresem pliku poziomie również nie powinny mieć nazwy za pomocą znaku podkreślenia i małe litery jako dwa pierwsze litery. Nazwy identyfikatorów, które zaczynają się od tych znaków, również są zastrzeżone. Zgodnie z Konwencją firma Microsoft używa znaku podkreślenia i Wielkiej litery umożliwiającą nazw makr i podwójnego podkreślenia dla nazw — słowo kluczowe specyficzne dla firmy Microsoft. Aby uniknąć konfliktów nazw, należy zawsze wybrać nazwy identyfikatorów, które nie zaczynają się od jednego lub dwóch znaków podkreślenia lub nazwy rozpoczynające się od znaku podkreślenia, a następnie wielką literą.  
  
**END specyficzny dla Microsoft**  
  
Poniżej przedstawiono przykłady prawidłowych identyfikatorów, które są zgodne z ANSI lub Microsoft ograniczenia nazewnictwa:  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
**Microsoft Specific**  
  
Identyfikatory w plikach źródłowych jest uwzględniana wielkość liter, domyślnie, symboli w plikach obiektowych nie są. Microsoft C traktuje identyfikatorów w jednostce kompilacji jako wielkość liter.  
  
Konsolidator firmy Microsoft jest uwzględniana wielkość liter. Należy określić wszystkie identyfikatory spójnie zgodnie z przypadek.  
  
"Źródłowy zestaw znaków" ustawiono prawidłowe znaki, które mogą być wyświetlane w plikach źródłowych. Dla Microsoft C: źródłowy zestaw jest standardowy zestaw znaków ASCII. Zestaw znaków źródła i wykonania zestawu znaków obejmują znaki ASCII, używane jako sekwencje ucieczki. Zobacz [stałe znakowe](../c-language/c-character-constants.md) uzyskać informacji o znaków wykonania zestawu.  
  
**END specyficzny dla Microsoft**  
  
Identyfikator ma "scope", czyli region programu, w którym jest znany i "powiązanie", który określa, czy tej samej nazwie w innym zakresie odwołuje się do tego samego identyfikatora. Te tematy zostały wyjaśnione w [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md).  
  
## <a name="see-also"></a>Zobacz też  
[Elementy języka C](../c-language/elements-of-c.md)