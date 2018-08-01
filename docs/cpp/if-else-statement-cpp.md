---
title: if-else, instrukcja (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 15748249a39813edc4446fa25511d20361b0706c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405113"
---
# <a name="if-else-statement-c"></a>if-else — instrukcja (C++)
Formanty warunkowych gałęzi. Instrukcje w *bloku if* są wykonywane tylko wtedy, gdy *wyrażenie if* daje w wyniku wartość różna od zera (lub wartość PRAWDA). Jeśli wartość *wyrażenie* jest różna od zera, *instrukcja1* i wszelkie inne instrukcje w bloku są wykonywane, oraz innego bloku, jeśli jest obecny, jest pomijana. Jeśli wartość *wyrażenie* wynosi zero, a następnie bloku if zostanie pominięta i innego bloku, jeśli jest obecny, jest wykonywany. Wyrażenia, które dają różna od zera są
- WARTOŚĆ TRUE
- wskaźnik zerowy
- dowolna wartość arytmetyczne różna od zera, lub 
- Typ klasy, który definiuje jednoznaczną konwersję na operacje arytmetyczne, boolean lub wskaźnika typu. (Aby uzyskać informacji dotyczących konwersji, zobacz [konwersje standardowe](../cpp/standard-conversions.md).)   
  
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

```cpp  
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
## <a name="if-statement-with-an-initializer"></a>Jeśli instrukcja za pomocą inicjatora
**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **Jeśli** instrukcji może również zawierać wyrażenie, które deklaruje i inicjuje zmienną o nazwie. Użyj tego formularza, instrukcji if, gdy zmienna jest wymagana tylko w zakresie bloku if. 

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

 We wszystkich rodzajach **Jeśli** instrukcji *wyrażenie*, która może zawierać żadnej wartości, z wyjątkiem strukturę, jest obliczane, łącznie ze wszystkimi efektami ubocznymi. Kontrola przechodzi z **Jeśli** instrukcji do następnej instrukcji w programie chyba że jeden z *instrukcji*zawiera s [podziału](../cpp/break-statement-cpp.md), [nadal](../cpp/continue-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md).  
  
 **Else** klauzuli `if...else` instrukcja jest skojarzone z najbliższą poprzedniej **Jeśli** instrukcji w tym samym zakresie, który nie ma odpowiadającego **else** Instrukcja.   

## <a name="constexpr-if-statements"></a>wyrażenia constexpr Jeśli instrukcji
**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): W funkcji szablonów, można użyć `constexpr if` instrukcję, aby podejmować decyzje rozgałęziania kompilacji bez konieczności uciekania się do wielu przeciążenia funkcji. Na przykład można napisać pojedynczą funkcję tego dojścia parametru podczas rozpakowywania (wymagane żadne przeciążenie parametr zero): 

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

## <a name="see-also"></a>Zobacz także  
 [Instrukcje wyboru](../cpp/selection-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [switch, instrukcja (C++)](../cpp/switch-statement-cpp.md)