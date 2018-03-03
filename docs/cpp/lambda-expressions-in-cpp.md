---
title: "Wyrażenia lambda w języku C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 035fe5c222f6de5b3f0d71c0ce9133c1101f2993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lambda-expressions-in-c"></a>Wyrażenia lambda w języku C++
W języku C ++ 11 i nowszych wyrażenia lambda — często nazywane *lambda*— jest to wygodny sposób definiowania obiektu funkcji anonimowej ( *zamknięcia*) w lokalizacji, gdzie jest wywoływany lub przekazanego jako argument do funkcji. Wyrażenia lambda są używane zwykle do Hermetyzowanie kilku wierszy kodu, które są przekazywane do algorytmów lub metod asynchronicznych. W tym artykule zdefiniowano, czym są lambdy, porównano je z innymi technikami programowania, omówiono ich zalety i dostarczono podstawowe przykłady.  

## <a name="related-topics"></a>Tematy pokrewne
- [Wyrażenia lambda a obiekty funkcji](lambda-expression-syntax.md)
- [Praca z wyrażenia lambda](examples-of-lambda-expressions.md)
- [wyrażenia lambda constexpr](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Części wyrażenia Lambda  
 Standardowi ISO C++ zawiera proste lambda, który jest przekazywany jako trzeci argument `std::sort()` funkcji:  
  
```cpp  
#include <algorithm>  
#include <cmath>  
  
void abssort(float* x, unsigned n) {  
    std::sort(x, x + n,  
        // Lambda expression begins  
        [](float a, float b) {  
            return (std::abs(a) < std::abs(b));  
        } // end of lambda expression  
    );  
}  
  
```  
  
 Na tej ilustracji przedstawiono elementy wyrażenia lambda:  
  
 ![Elementy wyrażenia lambda](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *Przechwyć klauzuli* (znanej także jako *lambda introducer* w specyfikacji języka C++.)  
  
2.  *Lista parametrów* opcjonalne. (Znanej także jako *deklarator lambda*)  
  
3.  *Specyfikacja modyfikowalną* opcjonalne.  
  
4.  *Specyfikacja wyjątku* opcjonalne.  
  
5.  *końcowe zwracanego typu* opcjonalne.  
  
6.  *Treść lambda*)  
  
### <a name="capture-clause"></a>Klauzula przechwytywania  
 Wyrażenie lambda, może wprowadzić nowe zmienne w jego treści (w **C ++ 14**) i może również dostęp, lub *przechwytywania*, zmiennych z otaczającego zakresu. Wyrażenie lambda rozpoczyna się od klauzuli przechwytywania (*lambda introducer* w standardowej składni), który określa, które zmienne są przechwytywane oraz czy przechwytywania jest według wartości lub według odwołania. Zmienne, które mają handlowego "i" (`&`) prefiks są udostępniane przez odwołanie i zmienne, które nie mają uzyskują wartości.  
  
 Klauzula pusty przechwytywania `[ ]`, wskazuje, że treść wyrażenia lambda uzyskuje dostęp do żadnych zmiennych w otaczającym zakresie.  
  
 Można użyć domyślny tryb przechwytywania (*domyślna przechwytywania* w standardowej składni) do wskazania sposobu przechwytywania zewnętrznego zmienne, do których istnieją odwołania w wyrażeniu lambda: `[&]` oznacza, że wszystkie zmienne odwołujące się do są przechwytywane przez odwołanie, i `[=]` oznacza, że są one przechwycone przez wartość. Można użyć domyślny tryb przechwytywania, a następnie określ tryb przeciwną jawnie określonych zmiennych. Na przykład jeśli zmienna zewnętrznych uzyskuje dostęp do treści wyrażenia lambda `total` przez odwołanie, a zmienna zewnętrznych `factor` wg wartości, następnie poniższych klauzul przechwytywania są równoważne:  
  
```cpp  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 Tylko w przypadku zmiennych, które są wymienione w wyrażeniu lambda są przechwytywane, gdy jest używana wartość domyślna przechwytywania.  
  
 Jeśli domyślna przechwytywania zawiera klauzulę przechwytywania `&`, nie `identifier` w `capture` tego przechwytywania klauzuli może mieć postać `& identifier`. Podobnie jeśli klauzula przechwytywania zawiera wartość domyślna przechwytywania `=`, nie `capture` tego przechwytywania klauzuli może mieć postać `= identifier`. Identyfikator lub `this` nie może występować więcej niż raz w klauzuli przechwytywania. Poniższy fragment kodu ilustruje kilka przykładów.  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};      // OK  
    [&, &i]{};     // ERROR: i preceded by & when & is the default  
    [=, this]{};   // ERROR: this when = is the default  
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated  
}  
```  
  
 Przechwytywanie następuje wielokropek jest rozwinięciem pakietu, jak pokazano w tym [ze zmienną liczbą argumentów szablonu](../cpp/ellipses-and-variadic-templates.md) przykład:  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 Aby użyć wyrażenia lambda w treści metody klasy, należy przekazać `this` wskaźnik do klauzuli przechwytywania zapewniające dostęp do elementów członkowskich danych i metod klasy otaczającej. 
 
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): `this` wskaźnika może być przechwytywany przez wartość określając `*this` w klauzuli przechwytywania. Przechwytywanie przez wartość oznacza, że cały *zamknięcia*, który jest obiektem funkcji anonimowej tego encapulates wyrażenia lambda, zostanie skopiowany do każdej lokacji wywołania przywołane lambda. Przechwytywanie przez wartość jest przydatne, gdy wyrażenie lambda będą wykonywane w ramach operacji równoległych lub asynchroniczne, szczególnie w przypadku niektórych architektury sprzętu, takich jak NUMA. 

Na przykład pokazujący sposób wyrażenia lambda za pomocą metody klasy, zobacz "Przykład: przy użyciu Lambda wyrażenia w metody" w [przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Użycie klauzuli przechwytywania, firma Microsoft zaleca zachowanie tych punktów na uwadze, szczególnie w przypadku, gdy używasz wyrażeń lambda z wielowątkowość:  
  
-   Odwołanie do przechwytywania może służyć do modyfikowania zmiennych poza, ale nie przechwytywania wartość. (`mutable` umożliwia kopie ma być zmodyfikowana, ale nie oryginału.)  
  
-   Odwołanie do przechwytywania odzwierciedlanie aktualizacji do zmiennych poza, ale wartość przechwytywania nie.  
  
-   Odwołanie do przechwytywania wprowadzenie zależności okres istnienia, ale przechwytywania wartość ma żadnych zależności okres istnienia. Jest to szczególnie ważne w przypadku, gdy wyrażenie lambda jest uruchamiane asynchronicznie. Jeśli lokalnym są przechwytywane przez odwołanie w wyrażeniu lambda asynchroniczne, tego lokalnego bardzo prawdopodobnie znikną przez przy uruchomieniu Wyrażenie lambda, co powoduje naruszenie zasad dostępu w czasie wykonywania.  
  
### <a name="generalized-capture-c-14"></a>Przechwytywanie uogólniony (C++ 14)  
  
 W języku C ++ 14 możesz wprowadzić i zainicjować nowe zmienne w klauzuli przechwytywania, bez konieczności posiadania tych zmiennych istnieje w otaczającym zakresie funkcja lambda. Inicjowanie może zostać wyrażona jako dowolne wyrażenie dowolnego; Typ nowej zmiennej jest ustalane od typu utworzonego przez wyrażenie. Jedną z korzyści płynących z tej funkcji jest, że w języku C ++ 14 można przechwytywać tylko do przeniesienia zmienne (takie jak std::unique_ptr) z otaczającego zakresu i ich używać w wyrażeniu lambda.  
  
```cpp  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### <a name="parameter-list"></a>Lista parametrów  
 Oprócz przechwytywania zmienne, wyrażeniu lambda może przyjmować parametry wejściowe. Lista parametrów (*deklarator lambda* w standardowej składni) jest opcjonalna i w większości aspektów podobny listy parametrów dla funkcji.  
  
```cpp  
auto y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 W **C++ 14**, jeśli typ parametru jest rodzajowy, auto — słowo kluczowe można użyć jako specyfikatora typu. Ta wartość informuje kompilator, aby utworzyć operator wywołania funkcji jako szablon. Każde wystąpienie automatycznie na liście parametrów jest równoważna z parametrem typu distinct.  
  
```cpp  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Wyrażenie lambda może przyjmować inne wyrażenie lambda jako argument. Aby uzyskać więcej informacji, zobacz "Wyższego kolejność wyrażenia Lambda" w temacie [przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Ponieważ parametr jest opcjonalny, można pominąć pustych nawiasów, jeśli argument nie jest przekazywany do wyrażenia lambda i jego deklarator lambda nie zawiera *specyfikacji wyjątku*,  *końcowe zwracanego typu*, lub `mutable`.  
  
### <a name="mutable-specification"></a>Specyfikacja modyfikowalna  
 Operator wywołania funkcji Wyrażenie lambda jest zwykle stałą wartość, ale użycie `mutable` — słowo kluczowe anuluje ten. Nie generuje to modyfikowalnych elementów członkowskich danych. Specyfikacja modyfikowalna umożliwia treści wyrażenia lambda modyfikację zmiennych, które są przechwytywane przez wartość. Przykłady w tym artykule przedstawiono sposoby używania `mutable`.  
  
### <a name="exception-specification"></a>Specyfikacja wyjątku  
 Można użyć `noexcept` specyfikacji wyjątku, aby wskazać, czy wyrażenia lambda nie zgłasza wszelkie wyjątki. Zgodnie ze zwykłej funkcji kompilatora Visual C++ generuje ostrzeżenie [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) Jeśli wyrażenie lambda deklaruje `noexcept` specyfikacji wyjątku i treści lambda zgłasza wyjątek, jak pokazano poniżej:  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() noexcept { throw 5; }();  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).  
  
### <a name="return-type"></a>Zwracany typ  
 Zwracany typ wyrażenia lambda jest automatycznie ustalana. Nie trzeba używać [automatycznie](../cpp/auto-cpp.md) — słowo kluczowe chyba że zostanie *końcowe zwracanego typu*. *Końcowe zwracanego typu* podobny zwracanego typu część zwykłej metody lub funkcji. Jednak zwracany typ należy postępować zgodnie z listą parametrów i musi zawierać słowa kluczowego końcowe zwracanego typu `->` przed zwracanym typem.  
  
 Można pominąć części zwracanego typu wyrażenia lambda, jeśli treść lambda zawiera tylko jedną instrukcję return lub wyrażenie nie zwraca wartości. Jeśli jednostka lambda zawiera jedną instrukcję return, kompilator deduces zwracanego typu z typu zwracane wyrażenie. W przeciwnym razie kompilator deduces zwracany typ `void`. Rozważmy następujące przykładowe fragmenty kodu, które ilustrują tę zasadę.  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
```  
  
 Wyrażenie lambda może generować inne wyrażenie lambda jako wartość zwracaną. Aby uzyskać więcej informacji, zobacz "Wyższego kolejność wyrażenia Lambda" w [przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md).  
  
### <a name="lambda-body"></a>Treść lambda  
 Treść lambda (*instrukcji złożonej* w standardowej składni) wyrażenia lambda wyrażenia mogą zawierać wszystko, co może zawierać treść zwykłej metody lub funkcji. Treść zwykłej funkcji, jak i wyrażenia lambda, mogą uzyskiwać dostęp do tego rodzaju zmiennych:  
  
-   Przechwyconych zmiennych z otaczającego zakresu, jak opisano wcześniej.  
  
-   Parametry  
  
-   Lokalnie deklarowane zmienne  
  
-   Klasa elementy członkowskie danych, gdy zadeklarowana w klasie i `this` przechwytywania  
  
-   Wszelkie zmiennej, która jest statycznym okresem magazynu — na przykład zmienne globalne  
  
 Poniższy przykład zawiera wyrażenie lambda, które jawnie przechwytuje zmiennej `n` według wartości i niejawnie przechwytuje zmiennej `m` przez odwołanie:  
  
```cpp  
// captures_lambda_expression.cpp  
// compile with: /W4 /EHsc   
#include <iostream>  
using namespace std;  
  
int main()  
{  
   int m = 0;  
   int n = 0;  
   [&, n] (int a) mutable { m = ++n + a; }(4);  
   cout << m << endl << n << endl;  
}  
```  
  
```Output  
5  
0  
```  
  
 Ponieważ zmiennej `n` jest przechwytywany przez wartość, jego wartość pozostaje `0` po wywołaniu wyrażenia lambda. `mutable` Specyfikacja umożliwia `n` można zmodyfikować w lambda.  
  
 Mimo że wyrażenie lambda może przechwytywać tylko zmienne, które mają automatyczny czas trwania przechowywania, można używać zmiennych o statycznym czasie trwania przechowywania w treści wyrażenia lambda. W poniższym przykładzie użyto `generate` funkcji i wyrażenia lambda do przypisania wartości dla każdego elementu w `vector` obiektu. Wyrażenie lambda modyfikuje zmienną statyczną, aby wygenerować wartość następnego elementu.  
  
```cpp  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });   
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz [Generowanie](../standard-library/algorithm-functions.md#generate).  
  
 Poniższy przykład kodu wykorzystuje funkcję z poprzedniego przykładu i dodaje przykład wyrażenia lambda, który używa algorytmu standardowa biblioteka C++ `generate_n`. To wyrażenie lambda przypisuje element `vector` obiektu Suma poprzednich dwóch elementów. `mutable` Słowo kluczowe jest używane, aby treść wyrażenia lambda można modyfikować jej kopii zmiennych zewnętrznych `x` i `y`, który przechwytuje wyrażenia lambda przez wartość. Ponieważ wyrażenia lambda przechwytuje oryginalnego zmienne `x` i `y` wg wartości, ich wartości pozostają `1` po wykonaniu lambda.  
  
```cpp  
// compile with: /W4 /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });  
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
  
int main()  
{  
    // The number of elements in the vector.  
    const int elementCount = 9;  
  
    // Create a vector object with each element set to 1.  
    vector<int> v(elementCount, 1);  
  
    // These variables hold the previous two elements of the vector.  
    int x = 1;  
    int y = 1;  
  
    // Sets each element in the vector to the sum of the   
    // previous two elements.  
    generate_n(v.begin() + 2,  
        elementCount - 2,  
        [=]() mutable throw() -> int { // lambda is the 3rd parameter  
        // Generate current value.  
        int n = x + y;  
        // Update previous two values.  
        x = y;  
        y = n;  
        return n;  
    });  
    print("vector v after call to generate_n() with lambda: ", v);  
  
    // Print the local variables x and y.  
    // The values of x and y hold their initial values because   
    // they are captured by value.  
    cout << "x: " << x << " y: " << y << endl;  
  
    // Fill the vector with a sequence of numbers  
    fillVector(v);  
    print("vector v after 1st call to fillVector(): ", v);  
    // Fill the vector with the next sequence of numbers  
    fillVector(v);  
    print("vector v after 2nd call to fillVector(): ", v);  
}  
```  
  
```Output  
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34  
x: 1 y: 1  
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9  
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18  
```  
  
 Aby uzyskać więcej informacji, zobacz [generate_n](../standard-library/algorithm-functions.md#generate_n).  

## <a name="constexpr-lambda-expressions"></a>wyrażenia lambda constexpr
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): wyrażenia lambda, może być zadeklarowana jako `constexpr` lub użyć w wyrażeniu stałym podczas inicjowania dla każdego elementu członkowskiego danych it Przechwytuje lub wprowadza jest dozwolona w wyrażeniu stałym.  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }

``` 
Wyrażenie lambda jest niejawnie `constexpr` Jeśli wynik spełnia wymagania `constexpr` funkcji:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Jeśli wyrażenie lambda jest jawnie lub niejawnie `constexpr`, tworzy konwersji do wskaźnika funkcji `constexpr` funkcji:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Wyrażenia lambda nie są obsługiwane w następujących wspólnych jednostki zarządzane środowiska uruchomieniowego (języka wspólnego CLR) języka: `ref class`, `ref struct`, `value class`, lub `value struct`.  
  
 Jeśli używasz modyfikator specyficzne dla firmy Microsoft takich jak [__declspec](../cpp/declspec.md), można wstawić je do wyrażenia lambda natychmiast po `parameter-declaration-clause`— na przykład:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Aby ustalić, czy modyfikujący jest obsługiwana przez wyrażeń lambda, zobacz artykuł o nim w [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md) sekcji dokumentacji.  
  
 Oprócz języka C ++ 11 lambda standardowe funkcje program Visual Studio obsługuje bezstanowych wyrażeń lambda, które są rozproszone — możliwe do przekonwertowania na wskaźników funkcji, korzystających z dowolnego konwencji wywoływania.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Obiekty funkcji w standardowej bibliotece C++](../standard-library/function-objects-in-the-stl.md)   
 [Wywołania funkcji](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)
