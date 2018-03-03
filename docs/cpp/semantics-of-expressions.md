---
title: "Semantyka wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efdf3f67e488af0e7c20c882552b18c533a031b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semantics-of-expressions"></a>Semantyka wyrażeń
Wyrażenia są oceniane według priorytetu i grupowanie ich operatorów. ([Priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md) w [konwencje leksykalne](../cpp/lexical-conventions.md), przedstawiono relacje C++ operatory nakładają się na wyrażenia.)  
  
## <a name="order-of-evaluation"></a>Kolejność obliczeń  
 Rozważmy następujący przykład:  
  
```cpp  
// Order_of_Evaluation.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
    int a = 2, b = 4, c = 9;  
  
    cout << a + b * c << "\n";  
    cout << a + (b * c) << "\n";  
    cout << (a + b) * c << "\n";  
}  
```  
  
```Output  
38  
38  
54  
```  
  
 ![Kolejność obliczania w wyrażeniu](../cpp/media/vc38zv1.gif "vc38ZV1")  
Kolejność obliczania wyrażenia  
  
 Kolejność, w jakiej są oceniane wyrażenia na ilustracji powyżej wynika priorytet i łączność operatorów:  
  
1.  Mnożenia (*) ma najwyższy priorytet w tym wyrażeniu; Dlatego Podwyrażenie `b * c` jest szacowana jako pierwsza.  
  
2.  Dodawania (+) ma najwyższy priorytet dalej, więc `a` zostanie dodany do produktu `b` i `c`.  
  
3.  Przesunięcia w lewo (<<) ma najniższy w wyrażeniu, ale istnieją dwa wystąpienia. Operator przesunięcia w lewo grupy od lewej do prawej, po lewej stronie wyrażenia podrzędnego dlatego najpierw ocenione, a następnie prawo jeden.  
  
 W przypadku używania nawiasów do grupowania użyto zmieniają priorytet, a także kolejności, w którym wyrażenie jest obliczane, jak pokazano na poniższej ilustracji.  
  
 ![Kolejność obliczania wyrażenia w nawiasach](../cpp/media/vc38zv2.gif "vc38ZV2")  
Kolejność obliczania wyrażenia w nawiasach  
  
 Wyrażenia, takich jak te na rysunku powyżej są obliczane wyłącznie w celu ich skutki uboczne — w tym przypadku do przekazywania informacji do wyjścia standardowego urządzenia.  
  
## <a name="notation-in-expressions"></a>Notacja w wyrażeniach  
 Język C++ określa niektórych możliwości podczas określania argumentów operacji. W poniższej tabeli przedstawiono typy argumentów operacji dopuszczalne operatorów, które wymagają argumentów operacji typu *typu*.  
  
### <a name="operand-types-acceptable-to-operators"></a>Typy argumentów operacji dopuszczalne operatorów  
  
|Oczekiwano typu|Dozwolone typy|  
|-------------------|-------------------|  
|*Typ*|`const`*typu*<br /> `volatile`*typu*<br /> *Typ*&<br /> `const`*typu*&<br /> `volatile`*typu*&<br /> `volatile const`*typu*<br /> `volatile const`*typu*&|  
|*Typ*\*|*Typ*\*<br /> `const`*typu*\*<br /> `volatile`*typu*\*<br /> `volatile const`*typu*\*|  
|`const`*typu*|*Typ*<br /> `const`*typu*<br />`const`*typu*&|  
|`volatile`*typu*|*Typ*<br /> `volatile`*typu*<br /> `volatile`*typu*&|  
  
 Ponieważ poprzednie reguł zawsze można używać w połączeniu, stała wskaźnika do obiektu volatile należy podać gdy oczekiwano wskaźnika.  
  
## <a name="ambiguous-expressions"></a>Wyrażenie niejednoznaczne  
 Niektóre wyrażenia są niejednoznaczne w ich znaczenie. Wyrażenia te występują najczęściej modyfikacji wartości obiektu jest więcej niż raz w tym samym wyrażeniu. Wyrażenia te są zależne od określonej kolejności szacowania, gdy język nie definiuje jedną. Rozważmy następujący przykład:  
  
```  
int i = 7;  
  
func( i, ++i );  
```  
  
 W języku C++ nie gwarantuje kolejność, w jakiej są oceniane argumentów dla wywołania funkcji. W związku z tym w powyższym przykładzie `func` otrzymują wartości 7 i 8, lub 8 i 8 jego parametrów, w zależności od tego, czy parametry są oceniane od lewej do prawej lub od prawej do lewej.  
  
## <a name="c-sequence-points-microsoft-specific"></a>Punkty sekwencji języka C++ (Microsoft Specific)  
 Wyrażenie może modyfikować wartość obiektu tylko raz między kolejnymi „punktami sekwencji”.  
  
 Definicja języka C++ nie określa obecnie punktów sekwencji. Microsoft C++ używa tych samych punktów sekwencji co standard ANSI C dla dowolnych wyrażeń obejmujących operatory języka C i nieobejmujących przeciążonych operatorów. Gdy operatory są przeciążone, semantyka zmienia się z sekwencjonowania operatora do sekwencjonowania wywołania funkcji. Microsoft C++ używa następujących punktów sekwencji:  
  
-   Lewy operand logicznego operatora AND (&&). Lewy operand logicznego operatora AND jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora AND zostanie obliczony.  
  
-   Lewy argument operacji operator logiczny OR (&#124; &#124;). Lewy operand logicznego operatora OR jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora OR zostanie obliczony.  
  
-   Lewy operand operatora przecinka. Lewy operand logicznego operatora przecinka jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze.  
  
-   Operator wywołania funkcji. Obliczane jest wyrażenie wywołania funkcji i wszystkie argumenty funkcji, włączając w to argumenty domyślne, a wszystkie efekty uboczne są zakończone przed wejściem do funkcji. Nie ma żadnej określonej kolejności obliczania między argumentami lub wyrażeniem wywołania funkcji.  
  
-   Pierwszy operand operatora warunkowego. Pierwszy operand operatora warunkowego jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem.  
  
-   Koniec pełnej inicjalizacji wyrażenia, taki jak koniec inicjalizacji w instrukcji deklaracji.  
  
-   Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażeń składają się z opcjonalnego wyrażenia z następującym po nim średnikiem (;). Wyrażenie jest obliczane całkowicie ze wszystkimi efektami ubocznymi.  
  
-   Wyrażenie kontrolujące w instrukcji wyboru (if lub switch). Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem kodu zależnego od wyboru.  
  
-   Wyrażenie kontrolujące instrukcji while lub do. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem dowolnej instrukcji z następnej iteracji pętli while lub do.  
  
-   Każde z trzech wyrażeń instrukcji for. Każde wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed przeniesieniem do następnego wyrażenia.  
  
-   Wyrażenie w instrukcji return. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed zwróceniem sterowania do funkcji wywołującej.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia](../cpp/expressions-cpp.md)