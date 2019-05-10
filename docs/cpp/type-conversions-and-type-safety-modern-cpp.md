---
title: Konwersje i bezpieczeństwo typów (Modern C++)
ms.date: 05/07/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: e06ea3f9c3ea427f205764c35988ea3316c3794a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221863"
---
# <a name="type-conversions-and-type-safety-modern-c"></a>Konwersje i bezpieczeństwo typów (Modern C++)

W tym dokumencie wymieniono typowe problemy z konwersją typów oraz opisano sposoby ich unikania w kodzie języka C++.

Pisząc program w języku C++, należy dopilnować, aby był on bezpieczny pod względem typów. Oznacza to, że każda zmienna, argument funkcji i wartość zwracana przez funkcję musi zawierać akceptowalny rodzaj danych, a operacje wykorzystujące wartości o różnych typach muszą „mieć sens” i nie mogą powodować utraty danych, nieprawidłowej interpretacji wzorców bitowych ani uszkodzeń pamięci. Program, który nigdy jawnie lub niejawnie nie konwertuje wartości z jednego typu na inny, jest z definicji bezpieczny pod względem typów. Czasami jednak konwersje typów, nawet niebezpieczne, są wymagane. Może na przykład może być konieczne zapisanie wyniku zmiennoprzecinkowy punktu operacji w zmiennej typu **int**, lub może być konieczne przekazanie wartości bez znaku **int** do funkcji, która przyjmuje zalogowany  **int**. Oba przykłady ilustrują konwersje niebezpieczne, ponieważ ich skutkiem może być utrata danych lub zmiana interpretacji wartości.

Gdy kompilator wykryje niebezpieczną konwersję, zgłasza błąd lub ostrzeżenie. Błąd zatrzymuje kompilację, natomiast ostrzeżenie pozwala na kontynuowanie kompilacji, ale wskazuje możliwy błąd w kodzie. Jednak nawet jeśli program kompiluje się bez ostrzeżeń, może zawierać kod, który prowadzi do niejawnych konwersji typu generujących niepoprawne wyniki. Błędy typu mogą być także wprowadzone przez jawne konwersje (rzutowania) w kodzie.

## <a name="implicit-type-conversions"></a>Niejawne konwersje typów

Wyrażenie zawiera argumenty operacji różnych typów wbudowanych, gdy nie ma jawnych rzutowań, kompilator używa wbudowanego *konwersje standardowe* do konwersji, jeden z argumentów tak, aby typy do siebie pasowały. Kompilator próbuje wykonać konwersje w dobrze zdefiniowanej kolejności, aż któraś się powiedzie. Jeśli wybrana konwersja skutkuje podwyższeniem poziomu, kompilator nie generuje ostrzeżenia. Jeśli konwersja powoduje zawężenie, kompilator generuje ostrzeżenie o możliwej utracie danych. To, czy rzeczywiście dojdzie do utraty danych, zależy od faktycznych wartości, jednak zalecamy traktowanie tego ostrzeżenia jako zgłoszenia błędu. Jeśli w operacji uczestniczy typ zdefiniowany przez użytkownika, kompilator podejmuje próbę użycia konwersji określonych w definicji klasy. Jeśli nie jest w stanie znaleźć odpowiedniej konwersji, zgłasza błąd i nie kompiluje programu. Aby uzyskać więcej informacji na temat reguł, które określają sposób konwersje standardowe zobacz [konwersje standardowe](../cpp/standard-conversions.md). Aby uzyskać więcej informacji dotyczących konwersji zdefiniowanych przez użytkownika, zobacz [konwersje zdefiniowane przez użytkownika (C++sposób niezamierzony)](../dotnet/user-defined-conversions-cpp-cli.md).

### <a name="widening-conversions-promotion"></a>Konwersje rozszerzające (podwyższające poziom)

W konwersji rozszerzającej wartość mniejszej zmiennej jest przypisywana do większej zmiennej bez utraty danych. Ponieważ konwersje rozszerzające są zawsze bezpieczne, kompilator wykonuje je dyskretnie i nie generuje ostrzeżeń. Poniższe konwersje są konwersjami rozszerzającymi.

|Z|Zadanie|
|----------|--------|
|Dowolny podpisane lub niepodpisane typu całkowitoliczbowego z wyjątkiem **long long** lub **__int64**|**double**|
|**wartość logiczna** lub **char**|Każdy inny typ wbudowany|
|**krótki** lub **wchar_t**|**int**, **długie**, **długi długi**|
|**int**, **długi**|**długi długi**|
|**float**|**double**|

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

Należy zauważyć, że wartości są reinterpretowane w obu kierunkach. Jeśli program generuje wyniki nieparzyste, w których znak wartości jest przeciwny wobec oczekiwanego, należy poszukać niejawnych konwersji między typami całkowitymi ze znakiem i bez znaku. W poniższym przykładzie wynik wyrażenia (0 – 1) jest niejawnie konwertowany z **int** do **unsigned int** gdy jest on przechowywany w `num`. Powoduje to ponowne interpretowanie wzorca bitowego.

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

Kompilator nie ostrzega o niejawnych konwersjach między typami całkowitymi ze znakiem i bez znaku. Dlatego zaleca się całkowite unikanie konwersji z typów ze znakiem na typy bez znaku. Jeśli nie jest to możliwe, należy dodać do kodu mechanizm kontroli w czasie wykonywania, który będzie wykrywał, czy konwertowana wartość jest większa lub równa zero i mniejsza lub równa maksymalnej wartości typu ze znakiem. Wartości w tym zakresie zostaną przekształcone z typów ze znakiem na typy bez znaku lub odwrotnie bez ponownego interpretowania.

### <a name="pointer-conversions"></a>Konwersje wskaźników

W wielu wyrażeniach tablica w stylu języka C jest niejawnie konwertowana na wskaźnik do pierwszego elementu w tablicy, a konwersje stałe mogą odbywać się dyskretnie. Takie rozwiązanie jest wygodne, ale powoduje ryzyko błędów. Na przykład poniższy źle zaprojektowany kod bezsensownie, a jeszcze zostanie skompilowany i wygeneruje wynik w postaci "p". Najpierw literał będący stałą w postaci ciągu „Help” jest konwertowany na typ `char*`, który wskazuje na pierwszy element tablicy. Następnie wskaźnik jest zwiększany o trzy elementy tak, że teraz wskazuje ostatni element „p”.

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>Konwersje jawne (rzutowania)

Za pomocą operacji rzutowania można nakazać kompilatorowi przekształcenie wartości z jednego typu na inny. Jeśli dwa typy są zupełnie z sobą niezwiązane, czasami kompilator zgłosi błąd, ale w innych przypadkach nie zgłosi błędu nawet wtedy, gdy operacja nie jest bezpieczna pod względem typów. Rzutowań należy używać rozważnie, ponieważ każda konwersja z jednego typu na drugi jest potencjalnym źródłem błędów w programie. Czasami jednak rzutowania są konieczne, a nie wszystkim towarzyszy wysokie ryzyko. Jednym z przydatnych zastosowań rzutowania są sytuacje, gdy kod wykonuje konwersję zawężająca, a wiadomo, że nie powoduje ona generowanie błędnych wyników przez program. W efekcie kompilator otrzymuje informację, że użytkownik wie co robi, dlatego nie trzeba mu pokazywać więcej ostrzeżeń. Innym zastosowaniem jest rzutowanie ze wskaźnika prowadzącego do klasy pochodnej na wskaźnik prowadzący do klasy bazowej. Innym zastosowaniem jest oddać **const**- ness zmiennej w celu przekazania jej do funkcji, która wymaga -**const** argumentu. Większość tych operacji rzutowania niesie z sobą pewne ryzyko.

W programowaniu w stylu języka C jeden operator rzutowania w stylu C jest używany do różnych rodzajów rzutowań.

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

Operator rzutowania w stylu języka C jest identyczny z operatorem wywołania (), dlatego w kodzie nie rzuca się w oczy i łatwo go przegapić. Oba są nieprawidłowe, ponieważ trudno je rozpoznać na pierwszy rzut oka lub Wyszukaj, a następnie są one używane, aby wywołać dowolną kombinację **statyczne**, **const**, i **operatorareinterpret_cast**. Stwierdzenie, co faktycznie wykonuje rzutowanie w starym stylu, może być trudne i obarczone ryzykiem błędów. Z tych powodów w sytuacjach, gdy jest potrzebne rzutowanie, zalecamy użycie jednego następujących z operatorów rzutowania języka C++. Często są one znacznie bezpieczniejsze pod względem typów i lepiej wyrażają cele programistyczne:

- **static_cast**, dla rzutowań, które są sprawdzane podczas kompilacji tylko raz. **static_cast** zwraca błąd, jeśli kompilator wykryje, że podjęto próbę rzutowania między typami, które nie są całkowicie zgodne. Może on także służyć do rzutowania między wskaźnikiem prowadzącym do klasy bazowej a wskaźnikiem prowadzącym do klasy pochodnej, jednak kompilator nie zawsze rozpozna, czy takie konwersje będą bezpieczne w czasie wykonywania.

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

- **dynamic_cast**, dla bezpiecznych, sprawdzanych w czasie wykonywania rzutowań wskaźnik do podstawowego do wskaźnika do pochodnego. A **dynamic_cast** jest bezpieczniejszy niż **static_cast** dla rzutowań, ale środowisko uruchomieniowe wyboru powoduje pewne nadmiarowe obciążenie.

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

- **Operator const_cast**dla rzutowanie **const**- ness zmiennej lub konwertowania bez -**const** zmienną **const**. Rzutowanie **const**-ness za pomocą tego operatora jest po prostu tak podatne na błędy jak rzutowanie, chyba że przy użyciu stylu języka C **rzutowania elementu const** trudniej wykonać przypadkowo. Czasami trzeba oddać **const**-ness zmiennej, na przykład, aby przekazać **const** zmienną do funkcji, która przyjmuje innej niż**const** parametru. W przykładzie poniżej pokazano, jak to zrobić.

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   Aby uzyskać więcej informacji, zobacz [const_cast](../cpp/const-cast-operator.md).

- **reinterpret_cast**dla rzutowań między niepowiązanymi z sobą typami takich jak **wskaźnik** do **int**.

    > [!NOTE]
    >  Tego operatora rzutowania używa się rzadziej niż innych. Nie ma też gwarancji, że będzie działał w innych kompilatorach.

   Poniższy przykład ilustruje sposób **reinterpret_cast** różni się od **static_cast**.

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

## <a name="see-also"></a>Zobacz także

[System typów języka C++ (Modern C++)](../cpp/cpp-type-system-modern-cpp.md)<br/>
[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
