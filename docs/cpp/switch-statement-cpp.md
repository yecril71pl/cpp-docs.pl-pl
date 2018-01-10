---
title: "Przełącz — instrukcja (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs: C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e668756e8cabafbdef522d6754487efe452f96de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="switch-statement-c"></a>switch — instrukcja (C++)
Umożliwia wybór między wielu fragmentów kodu, w zależności od wartości wyrażenia wartości całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
   switch ( init; expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie* musi być typu całkowitego lub typu klasy, dla którego jest jednoznaczne konwersji na typ całkowity. Promocję typu całkowitego odbywa się zgodnie z opisem w [konwersje standardowe](standard-conversions.md).  
  
 `switch` Treść instrukcji składa się z szeregu **przypadku** etykiety i opcjonalnie **domyślne** etykiety. Nie dwóch wyrażeń stałych w **przypadku** instrukcji można oszacować na tę samą wartość. **Domyślne** etykiety może wystąpić tylko raz. Labeled — instrukcje nie są wymagania dotyczące składni, ale `switch` instrukcja jest bez znaczenia bez nich.   Domyślna deklaracja nie muszą pochodzić na końcu; go może występować w dowolnym miejscu w treści instrukcji switch. Przypadek lub domyślne etykiety może wystąpić tylko wewnątrz instrukcji switch.  
  
 *Wyrażenia* w każdym **przypadku** etykiety jest konwertowana na typ *wyrażenie* i w porównaniu z *wyrażenie* dla równości. Kontrola przechodzi do instrukcji, których **przypadku** *wyrażenia* odpowiada wartości *wyrażenia*. W poniższej tabeli przedstawiono efekty.  
  
### <a name="switch-statement-behavior"></a>Zachowanie instrukcji Switch  
  
|Warunek|Akcja|  
|---------------|------------|  
|Skonwertowana wartość odpowiada awansowana kontrolowanie wyrażenia.|Formant jest przekazywany do instrukcji następującej tej etykiecie.|  
|Żadna stałe nie zgadza się stałe **przypadku** etykiet; **domyślne** etykiety jest obecny.|Sterowanie jest przekazywane na **domyślne** etykiety.|  
|Żadna stałe nie zgadza się stałe **przypadku** etykiet; **domyślne** etykieta nie jest obecny.|Sterowanie jest przekazywane do instrukcji następującej po `switch` instrukcji.|  
  
 Jeśli wyrażenie dopasowania zostanie znaleziony, formantu nie jest utrudnione przez kolejne **przypadku** lub **domyślne** etykiety. [Podziału](../cpp/break-statement-cpp.md) zatrzymuje wykonywanie, a transfer kontroli do instrukcji następującej po używana jest instrukcja `switch` instrukcji. Bez **podziału** instrukcji, co instrukcji z dopasowanej **przypadku** etykiet na końcu `switch`, takie jak **domyślne**, jest wykonywany. Na przykład:  
  
```  
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 W powyższym przykładzie `capa` jest zwiększany, jeśli `c` jest wielką `A`. `break` Instrukcji po `capa++` kończy wykonywanie `switch` treść instrukcji i kontroli przekazuje do `while` pętli. Bez `break` instrukcji, wykonanie "spadnie za pośrednictwem" do następnej instrukcji etykietą, dzięki czemu `lettera` i `nota` również być zwiększane. Podobnych celów jest obsługiwana przez `break` instrukcji dla `case 'a'`. Jeśli `c` jest jedną małą literę `a`, `lettera` jest zwiększany i `break` kończy instrukcji `switch` treść instrukcji. Jeśli `c` nie jest `a` lub `A`, `default` instrukcja jest wykonywana.  

 **Visual Studio 2017 lub nowszy:** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut został określony w standardzie C ++ 17. Mogą być używane w `switch` instrukcji jako wskazówka do kompilatora (lub innym osobom odczytywanie kodu) jest przeznaczony tego zachowania fall-through. Kompilatora Visual C++ aktualnie nie ostrzega na zachowanie przepuszczająca, więc ten atrybut nie zachowanie kompilatora nie wpływu. Uwaga dotyczy atrybut pustą instrukcję w instrukcji etykietą; innymi słowy średnik jest konieczne.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

 **Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): instrukcji switch może powodować i zainicjuj zmienną, której zakres jest ograniczony do bloku instrukcji switch:

```cpp
 switch (Gadget gadget(args); auto s = gadget.get_status())
        {
        case status::good:
            gadget.zip();
            break;
        case status::bad:
            throw BadGadget();
        };
```

 Wewnętrzny blok `switch` instrukcji mogą zawierać definicji inicjalizacji, pod warunkiem, że są one dostępne — to znaczy nie pomijany przez wszystkie możliwe wykonanie ścieżki. Nazwy wprowadzone za pomocą deklaracji mają zakres lokalny. Na przykład:  
  
```cpp  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 A `switch` instrukcja może być zagnieżdżone. W takich przypadkach **przypadku** lub **domyślne** etykiety skojarzenia z najbardziej `switch` instrukcji, która umieszcza je.  

 
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Microsoft C nie ogranicza liczbę przypadków wartości w `switch` instrukcji. Liczba jest ograniczona tylko przez ilość dostępnej pamięci. ANSI C wymaga co najmniej 257 dozwolone w przypadku etykiety `switch` instrukcji.  
  
 Wartość domyślna Microsoft C to, czy są włączone rozszerzenia Microsoft. Użyj [/Za](../build/reference/za-ze-disable-language-extensions.md) opcję kompilatora, aby wyłączyć te rozszerzenia.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Zaznaczenie — instrukcje](../cpp/selection-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 