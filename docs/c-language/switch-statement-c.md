---
title: "Przełącz Statement (C) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: switch
dev_langs: C++
helpviewer_keywords: switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b66e9f40e3fb7f4c9a6c9f6fcb9bcd9c2a45fdd3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="switch-statement-c"></a>switch — instrukcja (C)
`switch` i **przypadku** instrukcje pomocy złożonych warunkowe i rozgałęziania operacji kontroli. `switch` Instrukcji przekazuje sterowanie do instrukcji w jego treści.  
  
## <a name="syntax"></a>Składnia  
 *Wybór instrukcji*:  
 **Przełącz (** *wyrażenie* **)** *— instrukcja*  
  
 *z etykietą instrukcji*:  
 **przypadek***wyrażenia***:***— instrukcja*   
  
 **domyślne:***— instrukcja*   
  
 Kontrola przechodzi do instrukcji, których **przypadku** *wyrażenia* odpowiada wartości **przełącznika (** *wyrażenie* **)**. `switch` Instrukcja może zawierać dowolną liczbę **przypadku** wystąpień, ale nie dwie stałe przypadków, w tym samym `switch` instrukcji mogą mieć taką samą wartość. Wykonanie treść instrukcji zaczyna się od wybranego instrukcji i będzie kontynuowane aż do zakończenia treści lub do czasu **podziału** instrukcji przekazuje sterowanie poza treści.  
  
 Użycie `switch` instrukcji zwykle wygląda następująco:  
  
 `switch`( *wyrażenie* )  
  
 **{**  
  
 *deklaracje*  
  
 .  
  
 .  
  
 .  
  
 **przypadek** *wyrażenia* **:**  
  
 *instrukcje wykonywane, jeśli wyrażenie jest równe*  
  
 *wartość tego wyrażenia stałej*  
  
 .  
  
 .  
  
 .  
  
 **Podziel;**  
  
 **Wartość domyślna:**  
  
 *instrukcje wykonywane, jeśli wyrażenie nie jest równa*  
  
 *dowolne wielkość wyrażenie stałej*  
  
 **}**  
  
 Można użyć **podziału** oświadczenie zakończenie przetwarzania konkretnego przypadku w `switch` instrukcji i gałęzi do końca `switch` instrukcji. Bez **podziału**, program nadal dalej przypadku wykonywania instrukcji do momentu **podziału** lub osiągnięto końca instrukcji. W niektórych sytuacjach może być pożądane tego kontynuacji.  
  
 **Domyślne** instrukcja jest wykonywana, jeśli nie **przypadku** *wyrażenia* jest równa wartości **przełącznika (**  *wyrażenie* **)**. Jeśli **domyślne** instrukcji zostanie pominięty i nie **przypadku** zostanie znalezione dopasowanie, żaden z instrukcji w `switch` treści są wykonywane. Może istnieć co najwyżej jedna **domyślne** instrukcji. **Domyślne** instrukcji nie muszą występować na końcu; go może występować w dowolnym miejscu w treści `switch` instrukcji. A **przypadku** lub **domyślne** etykiety może wystąpić tylko wewnątrz `switch` instrukcji.  
  
 Typ `switch` *wyrażenie* i **przypadku** *wyrażenia* musi być wartością całkowitą. Wartość każdego **przypadku** *wyrażenia* muszą być unikatowe w treści instrukcji.  
  
 **Przypadku** i **domyślne** etykiety `switch` treść instrukcji są znaczące tylko w początkowej test, który określa, w którym rozpoczyna się wykonywanie w treści instrukcji. Mogą być zagnieżdżane instrukcji Switch. Wszelkie zmienne statyczne są inicjowane przed wykonaniem w każdym `switch` instrukcje.  
  
> [!NOTE]
>  Deklaracje może się pojawić na nagłówek tworzące złożonej instrukcji `switch` treści, ale zawarte w deklaracjach operacji inicjowania nie są wykonywane. `switch` Instrukcji przekazuje sterowanie bezpośrednio do instrukcji wykonywalnej w treści, pomijanie wierszy, które zawierają inicjalizacji.  
  
 Poniższe przykłady przedstawiają `switch` instrukcji:  
  
```  
switch( c )   
{  
    case 'A':  
        capa++;  
    case 'a':  
        lettera++;  
    default :  
        total++;  
}  
```  
  
 Wszystkie trzy instrukcje `switch` treści, w tym przykładzie są wykonywane, jeśli `c` jest równa `'A'` ponieważ **podziału** przed następującego przypadku nie ma instrukcji. Kontrola wykonywania jest przenoszona do pierwszej instrukcji (`capa++;`) i kontynuuje przez pozostała część treści. Jeśli `c` jest równa `'a'`, `lettera` i `total` są zwiększane. Tylko `total` jest zwiększany, jeśli `c` nie jest równa `'A'` lub `'a'`.  
  
```  
switch( i )   
{  
    case -1:  
        n++;  
        break;  
    case 0 :  
        z++;  
        break;  
    case 1 :  
        p++;  
        break;  
}  
```  
  
 W tym przykładzie **podziału** instrukcji następuje każda instrukcja `switch` treści. **Podziału** instrukcji wymusza wyjście z treści instrukcji po wykonaniu jednej instrukcji. Jeśli `i` jest równy -1, tylko `n` jest zwiększany. **Podziału** następującej po instrukcji `n++;` powoduje wykonanie formant do przekazania poza treść instrukcji, pomijanie pozostałe instrukcje. Podobnie jeśli `i` jest równa 0, tylko `z` jest zwiększany; Jeśli `i` jest równa 1, tylko `p` jest zwiększany. Ostatni **podziału** instrukcja nie jest to niezbędne, ponieważ formant przekazuje z treści na końcu złożonej instrukcji, ale jest on dołączony do spójności.  
  
 Pojedyncza instrukcja może przenosić wiele **przypadku** etykiet, jak przedstawiono na poniższym przykładzie:  
  
```  
case 'a' :  
case 'b' :  
case 'c' :  
case 'd' :  
case 'e' :  
case 'f' :  hexcvt(c);  
```  
  
 W tym przykładzie Jeśli *wyrażenia* jest równe dowolnej litery między `'a'` i `'f'`, `hexcvt` funkcja jest wywoływana.  
  
 **Dotyczące firmy Microsoft**  
  
 Microsoft C nie ogranicza liczbę przypadków wartości w `switch` instrukcji. Liczba jest ograniczona tylko przez ilość dostępnej pamięci. ANSI C wymaga co najmniej 257 dozwolone w przypadku etykiety `switch` instrukcji.  
  
 Wartość domyślna Microsoft C to, czy są włączone rozszerzenia Microsoft. /Za — opcja kompilatora umożliwia wyłączenie tych rozszerzeń.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Switch — instrukcja (C++)](../cpp/switch-statement-cpp.md)