---
title: "Składnia wyrażenia lambda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e41be4a1c69f6bf39e4ca0ede5b0afbe3a09f776
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda
W tym artykule przedstawiono składnię i elementy wyrażenia lambda. Aby uzyskać opis wyrażenia lambda, zobacz [wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="function-objects-vs-lambdas"></a>Funkcja vs obiektów. Wyrażenia Lambda  
 Podczas pisania kodu, prawdopodobnie używasz wskaźników funkcji i funkcji obiektów do rozwiązywania problemów i obliczeń, szczególnie w przypadku, gdy używasz [algorytmy standardowa biblioteka C++](../cpp/algorithms-modern-cpp.md). Wskaźniki funkcji, jak i funkcja obiektów ma zalety i wady — na przykład wskaźników funkcji ma minimalny składni obciążenie, ale nie zachowują stan, w zakresie, a obiekty funkcji mogą zachowują stan, ale wymaga obciążenie składni Definicja klasy.  
  
 Lambda łączy korzyści wskaźników funkcji i obiektów funkcyjnych, unikając ich wad. Podobnie jak obiekty funkcji wyrażenia lambda są elastyczne i mogą zachować stanu, ale w przeciwieństwie do obiektu funkcja jego zwięzłą składnią nie wymaga definicji klasy jawnego. Używając wyrażeń lambda, można pisać kod, który jest mniej skomplikowany i mniej podatny na błędy niż kod dla odpowiadających im obiektów funkcyjnych.  
  
 W następującym przykładzie porównano użycie wyrażenia lambda z użyciem obiektu funkcyjnego. W pierwszym przykładzie użyto wyrażenia lambda drukowanie do konsoli programu czy każdy element `vector` obiekt jest parzysta lub nieparzysta. W drugim przykładzie użyto obiektu funkcyjnego do zrealizowania tego samego zadania.  
  
## <a name="example-1-using-a-lambda"></a>Przykład 1: Używanie wyrażenia lambda  
 W tym przykładzie przekazuje lambda do `for_each` funkcji. Wyrażenie lambda wyświetla wynik stwierdzający, czy każdy element `vector` obiekt jest parzysta lub nieparzysta.  
  
### <a name="code"></a>Kod  
  
```cpp  
// even_lambda.cpp  
// compile with: cl /EHsc /nologo /W4 /MTd  
#include <algorithm>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
   // Create a vector object that contains 10 elements.  
   vector<int> v;  
   for (int i = 1; i < 10; ++i) {  
      v.push_back(i);  
   }  
  
   // Count the number of even numbers in the vector by   
   // using the for_each function and a lambda.  
   int evenCount = 0;  
   for_each(v.begin(), v.end(), [&evenCount] (int n) {  
      cout << n;  
      if (n % 2 == 0) {  
         cout << " is even " << endl;  
         ++evenCount;  
      } else {  
         cout << " is odd " << endl;  
      }  
   });  
  
   // Print the count of even numbers to the console.  
   cout << "There are " << evenCount   
        << " even numbers in the vector." << endl;  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```Output  
1 is odd  
2 is even  
3 is odd  
4 is even  
5 is odd  
6 is even  
7 is odd  
8 is even  
9 is odd  
There are 4 even numbers in the vector.  
  
```  
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie trzeci argument `for_each` funkcja ma wyrażenie lambda. `[&evenCount]` Części określa klauzuli przechwytywania wyrażenia, `(int n)` określa listy parametrów i pozostałej części określa treść wyrażenia.  
  
## <a name="example-2-using-a-function-object"></a>Przykład 2: Używanie obiektu funkcyjnego  
 Czasami wyrażenie lambda byłoby zbyt niewygodne do rozszerzenia dalszego niż w poprzednim przykładzie. W następnym przykładzie użyto obiektem funkcji zamiast lambda, wraz z `for_each` funkcji, aby utworzyć takie same wyniki jako przykład 1. Oba przykłady przechowywania liczba liczby parzyste w `vector` obiektu. Aby zachować stan operacji, `FunctorClass` klasy magazynów `m_evenCount` zmiennej przez odwołanie jako zmienną członkowską. Do wykonania tej operacji `FunctorClass` implementuje operator wywołania funkcji `operator()`. Kompilator Visual C++ generuje kod o rozmiarze i wydajności porównywalnej z kodem wyrażenia lambda z przykładu 1. Dla podstawowego problemu, takiego jak w tym artykule, prostsza konstrukcja lambda jest prawdopodobnie lepsza niż konstrukcja obiektu funkcyjnego. Jednak, jeśli istnieje możliwość, że funkcjonalność będzie wymagać znacznego rozszerzenia w przyszłości, można użyć obiektu funkcyjnego, aby ułatwić utrzymywanie kodu.  
  
 Aby uzyskać więcej informacji na temat `operator()`, zobacz [wywołania funkcji](../cpp/function-call-cpp.md). Aby uzyskać więcej informacji na temat `for_each` funkcji, zobacz [for_each](../standard-library/algorithm-functions.md#for_each).  
  
### <a name="code"></a>Kod  
  
```cpp  
// even_functor.cpp  
// compile with: /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
class FunctorClass  
{  
public:  
    // The required constructor for this example.  
    explicit FunctorClass(int& evenCount)  
        : m_evenCount(evenCount) { }  
  
    // The function-call operator prints whether the number is  
    // even or odd. If the number is even, this method updates  
    // the counter.  
    void operator()(int n) const {  
        cout << n;  
  
        if (n % 2 == 0) {  
            cout << " is even " << endl;  
            ++m_evenCount;  
        } else {  
            cout << " is odd " << endl;  
        }  
    }  
  
private:  
    // Default assignment operator to silence warning C4512.  
    FunctorClass& operator=(const FunctorClass&);  
  
    int& m_evenCount; // the number of even variables in the vector.  
};  
  
int main()  
{  
    // Create a vector object that contains 10 elements.  
    vector<int> v;  
    for (int i = 1; i < 10; ++i) {  
        v.push_back(i);  
    }  
  
    // Count the number of even numbers in the vector by   
    // using the for_each function and a function object.  
    int evenCount = 0;  
    for_each(v.begin(), v.end(), FunctorClass(evenCount));  
  
    // Print the count of even numbers to the console.  
    cout << "There are " << evenCount  
        << " even numbers in the vector." << endl;  
}  
  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```Output  
1 is odd  
2 is even  
3 is odd  
4 is even  
5 is odd  
6 is even  
7 is odd  
8 is even  
9 is odd  
There are 4 even numbers in the vector.  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Generowanie](../standard-library/algorithm-functions.md#generate)   
 [generate_n](../standard-library/algorithm-functions.md#generate_n)   
 [for_each](../standard-library/algorithm-functions.md#for_each)   
 [Specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md)   
 [Kompilator C4297 ostrzegawcze (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)   
 [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)