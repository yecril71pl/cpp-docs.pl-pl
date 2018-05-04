---
title: if-else — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8de2511096766cc4852c1c612eccb7dc65713218
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="if-else-statement-c"></a>if-else — instrukcja (C++)
Formanty warunkowego rozgałęziania. Instrukcje w *bloku if* są wykonywane tylko wtedy, gdy *wyrażenie if* ma wartość inną niż zero (lub `true`). Jeśli wartość *wyrażenie* jest różna od zera, *statement1* i inne instrukcje w bloku są wykonywane oraz innego bloku, jeśli istnieje, zostanie pominięty. Jeśli wartość *wyrażenie* wynosi zero, a następnie bloku Jeśli zostanie pominięta i innego bloku, jeśli istnieje, jest wykonywane. Są wyrażenia, których ocena ma inną niż zero
- `true`
- wskaźnik inną niż null
- wszelkie arytmetyczne wartości niezerowej, lub 
- Typ klasy, który określa jednoznaczne konwersji arytmetyczne, boolean lub wskaźnika typu. (Aby uzyskać informacje o konwersji, zobacz [konwersje standardowe](../cpp/standard-conversions.md).)   
  
## <a name="syntax"></a>Składnia  
  
```  
  
if ( expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
} 

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
}  

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
} 
```  
## <a name="example"></a>Przykład  
```  
// if_else_statement.cpp  
#include <iostream>

using namespace std;

class C
{
    public:
    void do_somthing(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

  // no else statement
    if (x == 10)
    {
        x = 0; 
    }
    
  
    C* c;
  init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```  
## <a name="if-statement-with-an-initializer"></a>Jeśli instrukcja przy użyciu inicjatora
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): **Jeśli** instrukcja może również zawierać wyrażenie, które deklaruje i inicjuje nazwanej zmiennej. Skorzystaj z tego formularza instrukcji if, gdy zmienna jest wymagana tylko w zakresie bloku if. 

```cpp
## Example  
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>


using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }


    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }

}
```

 W przypadku wszystkich rodzajów **Jeśli** instrukcji, *wyrażenie*, która może zawierać żadnej wartości, z wyjątkiem strukturą, jest obliczane, w tym wszystkie efekty uboczne. Formant przekazuje z **Jeśli** instrukcji do następnej instrukcji w programie chyba że jedną z *instrukcji*zawiera s [podziału](../cpp/break-statement-cpp.md), [kontynuować](../cpp/continue-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md).  
  
 **Else** klauzuli `if...else` instrukcja jest skojarzony z najbardziej poprzedniej **Jeśli** instrukcji w tym samym zakresie, który nie ma odpowiadającego **else** instrukcji.   

## <a name="constexpr-if-statements"></a>constexpr Jeśli — instrukcje
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępne z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): Szablony funkcji można **constexpr Jeśli** instrukcji podejmowanie decyzji rozgałęziania kompilacji bez o odwołać się do wielu przeciążeń funkcji. Na przykład można napisać jednej funkcji tego dojścia do parametru rozpakowywania (niezbędne żadne przeciążenie parametru zero): 

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
// handle t
   do_something(t);

   // handle r conditionally
   constexpr if (sizeof...(r)) 
   {
      
      f(r...); 
   }
   else
   {
       g(r...);
   }
}
```

  
 
## <a name="see-also"></a>Zobacz też  
 [Zaznaczenie — instrukcje](../cpp/selection-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [switch, instrukcja (C++)](../cpp/switch-statement-cpp.md)