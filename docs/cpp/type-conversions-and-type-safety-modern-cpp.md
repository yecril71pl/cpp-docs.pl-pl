---
title: Konwersje i bezpieczeństwo typów (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13dabba7b7cfc769d91471c2dfc6f92f1b414996
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424779"
---
# <a name="type-conversions-and-type-safety-modern-c"></a>Konwersje i bezpieczeństwo typów (Modern C++)
W tym dokumencie wymieniono typowe problemy z konwersją typów oraz opisano sposoby ich unikania w kodzie języka C++.  
  
 Pisząc program w języku C++, należy dopilnować, aby był on bezpieczny pod względem typów. Oznacza to, że każda zmienna, argument funkcji i wartość zwracana przez funkcję musi zawierać akceptowalny rodzaj danych, a operacje wykorzystujące wartości o różnych typach muszą „mieć sens” i nie mogą powodować utraty danych, nieprawidłowej interpretacji wzorców bitowych ani uszkodzeń pamięci. Program, który nigdy jawnie lub niejawnie nie konwertuje wartości z jednego typu na inny, jest z definicji bezpieczny pod względem typów. Czasami jednak konwersje typów, nawet niebezpieczne, są wymagane. Na przykład może być konieczne zapisanie wyniku operacji zmiennoprzecinkowej w zmiennej typu `int` albo przekazanie wartości jako typu `int` bez znaku do funkcji, która przyjmuje typ `int` ze znakiem. Oba przykłady ilustrują konwersje niebezpieczne, ponieważ ich skutkiem może być utrata danych lub zmiana interpretacji wartości.  
  
 Gdy kompilator wykryje niebezpieczną konwersję, zgłasza błąd lub ostrzeżenie. Błąd zatrzymuje kompilację, natomiast ostrzeżenie pozwala na kontynuowanie kompilacji, ale wskazuje możliwy błąd w kodzie. Jednak nawet jeśli program kompiluje się bez ostrzeżeń, może zawierać kod, który prowadzi do niejawnych konwersji typu generujących niepoprawne wyniki. Błędy typu mogą być także wprowadzone przez jawne konwersje (rzutowania) w kodzie.  
  
## <a name="implicit-type-conversions"></a>Niejawne konwersje typów  
 W przypadku wyrażenie zawiera wbudowane typy argumentów operacji, a nie jawnego rzutowania są obecne, kompilator korzysta z wbudowanej *konwersje standardowe* przekonwertować jeden z argumentów, aby były zgodne typy. Kompilator próbuje wykonać konwersje w dobrze zdefiniowanej kolejności, aż któraś się powiedzie. Jeśli wybrana konwersja skutkuje podwyższeniem poziomu, kompilator nie generuje ostrzeżenia. Jeśli konwersja powoduje zawężenie, kompilator generuje ostrzeżenie o możliwej utracie danych. To, czy rzeczywiście dojdzie do utraty danych, zależy od faktycznych wartości, jednak zalecamy traktowanie tego ostrzeżenia jako zgłoszenia błędu. Jeśli w operacji uczestniczy typ zdefiniowany przez użytkownika, kompilator podejmuje próbę użycia konwersji określonych w definicji klasy. Jeśli nie jest w stanie znaleźć odpowiedniej konwersji, zgłasza błąd i nie kompiluje programu. Aby uzyskać więcej informacji o regułach, które będą zarządzały sposobem konwersje standardowe, zobacz [konwersje standardowe](../cpp/standard-conversions.md). Aby uzyskać więcej informacji na temat konwersje zdefiniowane przez użytkownika, zobacz [konwersje zdefiniowane przez użytkownika (C + +/ CLI)](../dotnet/user-defined-conversions-cpp-cli.md).  
  
### <a name="widening-conversions-promotion"></a>Konwersje rozszerzające (podwyższające poziom)  
 W konwersji rozszerzającej wartość mniejszej zmiennej jest przypisywana do większej zmiennej bez utraty danych. Ponieważ konwersje rozszerzające są zawsze bezpieczne, kompilator wykonuje je dyskretnie i nie generuje ostrzeżeń. Poniższe konwersje są konwersjami rozszerzającymi.  
  
|Z|Do|  
|----------|--------|  
|Każdy typ całkowity ze znakiem lub bez, z wyjątkiem `long long` i `__int64`|`double`|  
|`bool` lub `char`|Każdy inny typ wbudowany|  
|`short` lub `wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### <a name="narrowing-conversions-coercion"></a>Konwersje zawężające (przekształcenia)  
 Kompilator wykonuje konwersje zawężające niejawnie, ale ostrzega o możliwej utracie danych. Ostrzeżenia te należy traktować bardzo poważnie. Jeśli istnieje pewność, że nie dojdzie do utraty danych, ponieważ wartości w większej zmiennej zawsze będą się mieścić w mniejszej zmiennej, można dodać jawne rzutowanie. Kompilator nie będzie wtedy generował ostrzeżeń. Jeśli nie ma pewności, że konwersja jest bezpieczna, należy dodać do kodu jakiś mechanizm kontroli w czasie wykonywania, który będzie obsługiwał zdarzenia ewentualnej utraty danych i w ten sposób zapobiegnie generowaniu błędnych wyników przez program. 
  
 Każda konwersja z typu zmiennoprzecinkowego na typ całkowity jest konwersją zawężającą, ponieważ ułamkowa część wartości liczby zmiennoprzecinkowej jest odrzucana i tracona.  
  
 Poniższy przykład kodu zawiera kilka niejawnych konwersji zawężających oraz ostrzeżenia generowane dla nich przez kompilator.  
  
```cpp  
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow  
wchar_t wch = 'A'; //OK  
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'  
              // to 'char', possible loss of data  
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from  
                           // 'int' to 'unsigned char'  
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to  
              // 'int', possible loss of data  
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to  
             // 'int', possible loss of data  
```  
  
### <a name="signed---unsigned-conversions"></a>Konwersje między typami ze znakiem i bez znaku  
 Typ całkowity ze znakiem i jego odpowiednik bez znaku są zawsze tej samej wielkości, ale różnią się sposobem interpretacji wzorca bitowego podczas przekształcania wartości. Poniższy przykład kodu pokazuje, co się dzieje, gdy ten sam wzorzec bitowy jest interpretowany jako wartość ze znakiem oraz bez znaku. Wzorzec bitowy zapisany w parametrach `num` i `num2` nigdy się nie zmienia względem przedstawionego na wcześniejszej ilustracji.  
  
```cpp  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
```  
  
 Należy zauważyć, że wartości są reinterpretowane w obu kierunkach. Jeśli program generuje wyniki nieparzyste, w których znak wartości jest przeciwny wobec oczekiwanego, należy poszukać niejawnych konwersji między typami całkowitymi ze znakiem i bez znaku. W poniższym przykładzie wynik wyrażenia (0 - 1) jest niejawnie przekonwertowana z `int` do `unsigned int` podczas przechowywania w `num`. Powoduje to ponowne interpretowanie wzorca bitowego.  
  
```cpp  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 Kompilator nie ostrzega o niejawnych konwersjach między typami całkowitymi ze znakiem i bez znaku. Dlatego zaleca się całkowite unikanie konwersji z typów ze znakiem na typy bez znaku. Jeśli nie jest to możliwe, należy dodać do kodu mechanizm kontroli w czasie wykonywania, który będzie wykrywał, czy konwertowana wartość jest większa lub równa zero i mniejsza lub równa maksymalnej wartości typu ze znakiem. Wartości w tym zakresie zostaną przekształcone z typów ze znakiem na typy bez znaku lub odwrotnie bez ponownego interpretowania.  
  
### <a name="pointer-conversions"></a>Konwersje wskaźników  
 W wielu wyrażeniach tablica w stylu języka C jest niejawnie konwertowana na wskaźnik do pierwszego elementu w tablicy, a konwersje stałe mogą odbywać się dyskretnie. Takie rozwiązanie jest wygodne, ale powoduje ryzyko błędów. Na przykład poniższy źle zaprojektowany kod wygląda bezsensownie, a jednak zostanie skompilowany w programie Visual C++ i wygeneruje wynik w postaci litery „p”. Najpierw literał będący stałą w postaci ciągu „Help” jest konwertowany na typ `char*`, który wskazuje na pierwszy element tablicy. Następnie wskaźnik jest zwiększany o trzy elementy tak, że teraz wskazuje ostatni element „p”.  
  
```cpp  
char* s = "Help" + 3;  
  
```  
  
## <a name="explicit-conversions-casts"></a>Konwersje jawne (rzutowania)  
 Za pomocą operacji rzutowania można nakazać kompilatorowi przekształcenie wartości z jednego typu na inny. Jeśli dwa typy są zupełnie z sobą niezwiązane, czasami kompilator zgłosi błąd, ale w innych przypadkach nie zgłosi błędu nawet wtedy, gdy operacja nie jest bezpieczna pod względem typów. Rzutowań należy używać rozważnie, ponieważ każda konwersja z jednego typu na drugi jest potencjalnym źródłem błędów w programie. Czasami jednak rzutowania są konieczne, a nie wszystkim towarzyszy wysokie ryzyko. Jednym z przydatnych zastosowań rzutowania są sytuacje, gdy kod wykonuje konwersję zawężająca, a wiadomo, że nie powoduje ona generowanie błędnych wyników przez program. W efekcie kompilator otrzymuje informację, że użytkownik wie co robi, dlatego nie trzeba mu pokazywać więcej ostrzeżeń. Innym zastosowaniem jest rzutowanie ze wskaźnika prowadzącego do klasy pochodnej na wskaźnik prowadzący do klasy bazowej. Kolejna sytuacja to eliminowanie atrybutu stałości (typu `const`) zmiennej w celu przekazania jej do funkcji, która wymaga argumentu niebędącego typem `const`. Większość tych operacji rzutowania niesie z sobą pewne ryzyko.  
  
 W programowaniu w stylu języka C jeden operator rzutowania w stylu C jest używany do różnych rodzajów rzutowań.  
  
```cpp  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 Operator rzutowania w stylu języka C jest identyczny z operatorem wywołania (), dlatego w kodzie nie rzuca się w oczy i łatwo go przegapić. Oba operatory sprawiają problemy, ponieważ trudno je rozpoznać na pierwszy rzut oka oraz wyszukać, a są na tyle różne, że mogą wywołać dowolną kombinację rzutowań `static`, `const` i `reinterpret_cast`. Stwierdzenie, co faktycznie wykonuje rzutowanie w starym stylu, może być trudne i obarczone ryzykiem błędów. Z tych powodów w sytuacjach, gdy jest potrzebne rzutowanie, zalecamy użycie jednego następujących z operatorów rzutowania języka C++. Często są one znacznie bezpieczniejsze pod względem typów i lepiej wyrażają cele programistyczne:  
  
-   `static_cast` dla rzutowań sprawdzanych tylko podczas kompilacji. Jeśli kompilator wykryje próbę rzutowania między całkowicie niezgodnymi typami, operator `static_cast` zwraca błąd. Może on także służyć do rzutowania między wskaźnikiem prowadzącym do klasy bazowej a wskaźnikiem prowadzącym do klasy pochodnej, jednak kompilator nie zawsze rozpozna, czy takie konwersje będą bezpieczne w czasie wykonywania.  
  
    ```cpp  
    double d = 1.58947;  
    int i = d;  // warning C4244 possible loss of data  
    int j = static_cast<int>(d);       // No warning.  
    string s = static_cast<string>(d); // Error C2440:cannot convert from  
                                       // double to std:string  
  
    // No error but not necessarily safe.  
    Base* b = new Base();  
    Derived* d2 = static_cast<Derived*>(b);  
  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [static_cast](../cpp/static-cast-operator.md).  
  
-   `dynamic_cast` dla bezpiecznych, sprawdzanych w czasie wykonywania rzutowań ze wskaźnika prowadzącego do klasy bazowej na wskaźnik prowadzący do klasy pochodnej. Operator `dynamic_cast` jest bezpieczniejszy niż `static_cast` w rzutowaniach na elementy podrzędne, jednak kontrola w czasie wykonywania obciąża system.  
  
    ```cpp  
    Base* b = new Base();  
  
    // Run-time check to determine whether b is actually a Derived*  
    Derived* d3 = dynamic_cast<Derived*>(b);  
  
    // If b was originally a Derived*, then d3 is a valid pointer.  
    if(d3)  
    {  
       // Safe to call Derived method.  
       cout << d3->DoSomethingMore() << endl;  
    }  
    else  
    {  
       // Run-time check failed.  
       cout << "d3 is null" << endl;  
    }  
  
    //Output: d3 is null;  
  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [dynamic_cast](../cpp/dynamic-cast-operator.md).  
  
-   `const_cast` do eliminowania atrybutu stałości (typu `const`) zmiennej lub konwertowania zmiennej o typie innym niż `const` na zmienną typu `const`. Eliminowanie atrybutu `const` za pomocą tego operatora jest równie podatne na błędy jak rzutowanie w stylu języka C. Jedyna różnica polega na tym, iż rzutowanie `const-cast` trudniej wykonać przypadkowo. Czasami w zmiennej trzeba eliminować atrybut `const`, na przykład w celu przekazania zmiennej typu `const` do funkcji, która przyjmuje parametry typu innego niż `const`. W przykładzie poniżej pokazano, jak to zrobić.  
  
    ```cpp  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [const_cast](../cpp/const-cast-operator.md).  
  
-   `reinterpret_cast` dla rzutowań między niepowiązanymi z sobą typami, np. z `pointer` na `int`.  
  
    > [!NOTE]
    >  Tego operatora rzutowania używa się rzadziej niż innych. Nie ma też gwarancji, że będzie działał w innych kompilatorach.  
  
     Poniższy przykład ilustruje różnice między operatorami `reinterpret_cast` i `static_cast`.  
  
    ```cpp  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md).  
  
## <a name="see-also"></a>Zobacz też  
 [System typów języka C++](../cpp/cpp-type-system-modern-cpp.md)   
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)