---
title: "Deklarator odwołania do wartości: &amp; &amp; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&&'
dev_langs: C++
helpviewer_keywords: '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8d0595078c9515c5c705a1cbfb1ed6b5e55db788
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rvalue-reference-declarator-ampamp"></a>Deklarator odwołania do wartości:&amp;&amp;
Zawiera odwołanie do r-wartości wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
type-id && cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do r-wartości umożliwiają odróżnienia l-wartością r-wartości. L-wartością odwołań i odwołania do r-wartości są podobne składnię i semantycznie, ale ich wykonać nieco inne reguły. Aby uzyskać więcej informacji na temat lvalues i rvalues, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Aby uzyskać więcej informacji o odwołaniach l-wartością, zobacz [deklarator odwołania do l-wartością: &](../cpp/lvalue-reference-declarator-amp.md).  
  
 W poniższych sekcjach opisano, jak odwołania do r-wartości obsługują wykonania *Przenieś semantyki* i *doskonała przekazywania*.  
  
## <a name="move-semantics"></a>Przenieś semantyki  
 Odwołania wartościowane prawostronnie obsługuje wykonania *Przenieś semantyki*, może znacznie zwiększyć wydajność aplikacji. Przenieś semantyki umożliwia pisanie kodu, który przenosi zasoby (na przykład dynamicznej alokacji pamięci) z jednego obiektu do innego. Przenieś semantyki działa, ponieważ dzięki zasoby można przenosić od obiekty tymczasowe, które nie może być przywoływany w innym miejscu w programie.  
  
 Implementuje semantykę przenoszenia, zwykle przedstawienie *przenoszenie konstruktora,* i opcjonalnie operator przypisania przenoszenia (`operator=`), do swojej klasy. Operacje kopiowania i przypisania, których źródła są rvalues, a następnie automatycznie korzystać z Przenieś semantyki. W przeciwieństwie do domyślnego konstruktora kopiującego kompilator nie ma domyślny konstruktor przenoszenia. Aby uzyskać więcej informacji na temat zapisu Konstruktor przenoszący oraz używać go w aplikacji, zobacz [konstruktory przenoszenia i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).  
  
 Można także przeciążać zwykłej funkcji i operatorów, aby móc korzystać z Przenieś semantyki. Visual C++ 2010 wprowadza semantyki Przenieś do standardowa biblioteka C++. Na przykład `string` klasa implementuje operacje przenoszenia semantyki. Rozważmy poniższy przykład, który łączy kilka ciągów i wynik:  
  
```  
// string_concatenation.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main()  
{  
   string s = string("h") + "e" + "ll" + "o";  
   cout << s << endl;  
}  
```  
  
 Przed Visual C++ 2010, każdy wywołanie `operator+` przydziela i zwraca nowy tymczasowy `string` obiektu (r-wartości). `operator+`Nie można dołączyć jeden ciąg wzajemnie, ponieważ nie może określić, czy ciągi źródła są lvalues i rvalues. Jeśli parametry źródła są obie lvalues, może być przywoływany w innym miejscu w programie i w związku z tym nie może być modyfikowany. Za pomocą odwołania wartościowane prawostronnie `operator+` można zmodyfikować, aby wykonać rvalues, która nie może być przywoływany w innym miejscu w programie. W związku z tym `operator+` teraz dołączyć jednego ciągu na inny. Może to znacznie zmniejszyć liczbę alokacji pamięci dynamicznej który `string` klasy należy wykonać. Aby uzyskać więcej informacji na temat `string` , zobacz [basic_string — klasa](../standard-library/basic-string-class.md).  
  
 Semantyki przenoszenia pomaga również w przypadku, gdy kompilator nie można użyć zwrócić wartość optymalizacji (RVO) lub o nazwie zwrócić wartość optymalizacji (NRVO). W takich przypadkach kompilator wywołuje konstruktor przenoszenia, jeśli typ definiuje ją. Aby uzyskać więcej informacji na temat o nazwie optymalizacji wartości, zobacz [o nazwie zwracać optymalizacji wartość w programie Visual C++ 2005](http://go.microsoft.com/fwlink/?LinkId=131571).  
  
 Aby lepiej zrozumieć semantyki przenoszenia, należy wziąć pod uwagę przykład wstawianie do elementu `vector` obiektu. Jeśli pojemność `vector` przekroczeniu obiektu `vector` obiektu musi ponownie przydzielić pamięci dla elementów, a następnie skopiuj każdy element do innej lokalizacji pamięci, aby zwolnić miejsce dla wstawiony element. Podczas operacji wstawiania kopiuje element, tworzy nowy element, wywołuje Konstruktor kopiujący, aby skopiować dane z poprzedniego elementu do nowego elementu i następnie niszczy poprzedni element. Przenieś semantyki umożliwia przenoszenie obiektów bezpośrednio, bez konieczności wykonywania alokacji pamięci kosztowne i operacje kopiowania.  
  
 Aby skorzystać z semantyki przenoszenia w `vector` przykład może zapisywać Konstruktor przenoszący do przenoszenia danych z jednego obiektu do innego.  
  
 Aby uzyskać więcej informacji o wprowadzenie semantyki Przenieś do standardowa biblioteka C++ w programie Visual C++ 2010, zobacz [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="perfect-forwarding"></a>Doskonałego przekazywania dalej  
 Doskonałego przekazywania dalej zmniejsza potrzebę przeciążonej funkcji i pozwala uniknąć problem przesyłania dalej. *Przekazywania problem* może wystąpić, gdy zapisu ogólnego funkcję, która przyjmuje odwołań jako jego parametrów i przekazaniem (lub *przekazuje*) tych parametrów na inną funkcję. Na przykład, jeśli funkcja ogólnego przyjmuje parametr typu `const T&`, a następnie wywołana funkcja nie można zmodyfikować wartości tego parametru. Jeśli ogólna funkcja przyjmuje parametr typu `T&`, a następnie funkcji nie można wywołać za pomocą r-wartości (na przykład tymczasowego obiektu lub literał całkowity).  
  
 Zwykle, aby rozwiązać ten problem, należy podać zastąpionej wersji ogólna funkcja przyjmujących zarówno `T&` i `const T&` dla każdego z jego parametrów. W związku z tym liczbę przeciążonej funkcji znacznie zwiększa się z liczbą parametrów. Odwołania do r-wartości pozwalają na zapis jednej wersji funkcję, która akceptuje dowolne argumenty i przekazuje je do innej funkcji tak, jakby była bezpośredniego wywoływania innych funkcji.  
  
 Rozważmy następujący przykład, który deklaruje cztery typy `W`, `X`, `Y`, i `Z`. Konstruktor dla każdego typu ma inną kombinację `const` i nie-`const` odwołania l-wartością jako jego parametrów.  
  
```  
struct W  
{  
   W(int&, int&) {}  
};  
  
struct X  
{  
   X(const int&, int&) {}  
};  
  
struct Y  
{  
   Y(int&, const int&) {}  
};  
  
struct Z  
{  
   Z(const int&, const int&) {}  
};  
```  
  
 Załóżmy, że chcesz zapisać ogólnego funkcję, która generuje obiektów. Poniższy przykład przedstawia sposób zapisania tej funkcji:  
  
```  
template <typename T, typename A1, typename A2>  
T* factory(A1& a1, A2& a2)  
{  
   return new T(a1, a2);  
}  
```  
  
 W poniższym przykładzie przedstawiono prawidłowe wywołanie `factory` funkcji:  
  
```  
int a = 4, b = 5;  
W* pw = factory<W>(a, b);  
```  
  
 Jednak poniższy przykład zawiera prawidłowy wywołanie `factory` działać, ponieważ `factory` przyjmuje l-wartością odwołań, które można modyfikować, jako jego parametrów, ale jest wywoływana przy użyciu rvalues:  
  
```  
Z* pz = factory<Z>(2, 2);  
```  
  
 Zwykle, aby rozwiązać ten problem, należy utworzyć zastąpionej wersji `factory` funkcja dla każdej kombinacji `A&` i `const A&` parametrów. Odwołania do r-wartości pozwalają na zapis jednej wersji `factory` funkcji, jak pokazano w poniższym przykładzie:  
  
```  
template <typename T, typename A1, typename A2>  
T* factory(A1&& a1, A2&& a2)  
{  
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));  
}  
```  
  
 W tym przykładzie użyto odwołania do r-wartości jako parametry `factory` funkcji. Celem [std::forward](../standard-library/utility-functions.md#forward) funkcji jest przesyłanie parametry funkcji fabrykę konstruktora klasy szablonu.  
  
 W poniższym przykładzie przedstawiono `main` funkcja, która używa zweryfikowanej `factory` funkcja służąca do tworzenia wystąpień `W`, `X`, `Y`, i `Z` klasy. Zweryfikowanej `factory` funkcja przekazuje jego parametrów (lvalues i rvalues) do konstruktora odpowiedniej klasy.  
  
```  
int main()  
{  
   int a = 4, b = 5;  
   W* pw = factory<W>(a, b);  
   X* px = factory<X>(2, b);  
   Y* py = factory<Y>(a, 2);  
   Z* pz = factory<Z>(2, 2);  
  
   delete pw;  
   delete px;  
   delete py;  
   delete pz;  
}  
```  
  
## <a name="additional-properties-of-rvalue-references"></a>Dodatkowe właściwości odwołania do r-wartości  
 **Można przeciążyć funkcji odwołania do wartości i odwołania do r-wartości.**  
  
 Przez przeciążenie funkcji podjęcie `const` odwołania do wartości lub odwołania do r-wartości, można napisać kod, który odróżni między obiektami nie można modyfikować (lvalues) i tymczasowej można modyfikować wartości (rvalues). Obiekt można przekazać do funkcji, która przyjmuje odwołanie do r-wartości, chyba że obiekt jest oznaczony jako `const`. Poniższy przykład przedstawia funkcję `f`, która jest przeciążony odwołania do wartości i odwołania do r-wartości. `main` Wywołania funkcji `f` z lvalues i r-wartości.  
  
```  
// reference-overload.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void f(const MemoryBlock&)  
{  
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;  
}  
  
void f(MemoryBlock&&)  
{  
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;  
}  
  
int main()  
{  
   MemoryBlock block;  
   f(block);  
   f(MemoryBlock());  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
In f(const MemoryBlock&). This version cannot modify the parameter.  
In f(MemoryBlock&&). This version can modify the parameter.  
```  
  
 W tym przykładzie pierwsze wywołanie `f` przekazuje zmiennej lokalnej (l-wartością) jako jej argument. Drugie wywołanie `f` przekazuje tymczasowy obiekt jako jej argument. Ponieważ tymczasowego obiektu nie można odwoływać się w innym miejscu w programie, wywołanie jest powiązany z zastąpionej wersji `f` pobierającej odwołania do r-wartości, którego będzie mógł zmodyfikować obiekt.  
  
 **Kompilator traktuje jako l-wartością odwołanie do r-wartości nazwane i odwołania do r-wartości nienazwane jako r-wartości.**  
  
 Podczas pisania funkcję, która przyjmuje odwołanie do r-wartości jako jego parametr, że parametr jest traktowany jako l-wartością w treści funkcji. Kompilator traktuje odwołania do nazwanych wartości jako l-wartość ponieważ nazwanego obiektu może odwoływać się wiele części programu; on niebezpieczne umożliwiają wielu części programu, aby zmodyfikować lub usunąć zasoby z tego obiektu. Na przykład wielu części programu próby przeniesienie zasobów z tego samego obiektu, pierwsza część zostanie pomyślnie przenieść zasobu.  
  
 Poniższy przykład przedstawia funkcję `g`, która jest przeciążony odwołania do wartości i odwołania do r-wartości. Funkcja `f` przyjmuje odwołanie do r-wartości jako jego parametr (odwołanie o nazwie r-wartości) i zwraca odwołanie do r-wartości (odwołania do r-wartości bez nazwy). W wywołaniu `g` z `f`, wiązaniem wybiera wersja `g` pobierającej odwołania do wartości, ponieważ treść `f` traktuje jako l-wartość jego parametru. W wywołaniu `g` z `main`, wiązaniem wybiera wersja `g` pobierającej odwołania do r-wartości, ponieważ `f` zwraca odwołanie do r-wartości.  
  
```  
// named-reference.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void g(const MemoryBlock&)   
{  
   cout << "In g(const MemoryBlock&)." << endl;  
}  
  
void g(MemoryBlock&&)   
{  
   cout << "In g(MemoryBlock&&)." << endl;  
}  
  
MemoryBlock&& f(MemoryBlock&& block)  
{  
   g(block);  
   return block;  
}  
  
int main()  
{  
   g(f(MemoryBlock()));  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
In g(const MemoryBlock&).  
In g(MemoryBlock&&).  
```  
  
 W tym przykładzie `main` funkcja przekazuje do r-wartości `f`. Treść `f` traktuje jego nazwany parametr jako l-wartością. Wywołania z `f` do `g` wiąże parametr odwołania do wartości (pierwszej wersji przeciążone `g`).  
  
-   **Można rzutowania wartościowanego lewostronnie z odwołaniem wartościowanym prawostronnie.**  
  
 Standardowa biblioteka C++ [std::move](../standard-library/utility-functions.md#move) funkcja umożliwia konwertowanie obiektu do r-wartości odwołania do tego obiektu. Alternatywnie można użyć `static_cast` — słowo kluczowe do rzutowania wartościowanego lewostronnie z odwołaniem wartościowanym prawostronnie, jak pokazano w poniższym przykładzie:  
  
```  
// cast-reference.cpp  
// Compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// A class that contains a memory resource.  
class MemoryBlock  
{  
   // TODO: Add resources for the class here.  
};  
  
void g(const MemoryBlock&)   
{  
   cout << "In g(const MemoryBlock&)." << endl;  
}  
  
void g(MemoryBlock&&)   
{  
   cout << "In g(MemoryBlock&&)." << endl;  
}  
  
int main()  
{  
   MemoryBlock block;  
   g(block);  
   g(static_cast<MemoryBlock&&>(block));  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
In g(const MemoryBlock&).  
In g(MemoryBlock&&).  
```  
  
 **Szablony funkcji wywnioskować ich typy argumentów szablonu, a następnie użyj odwołania zwijanie reguły.**  
  
 Często można zapisać szablonu funkcji, która przekazuje (lub *przekazuje*) jego parametrów na inną funkcję. Należy zrozumieć sposób działania wnioskowanie typu szablonu dla szablonów funkcji, które przyjmują odwołania do r-wartości.  
  
 Jeśli argument funkcji jest r-wartości, kompilator deduces argument jako odwołanie do r-wartości. Na przykład w przypadku przekazania odwołania do r-wartości do obiektu typu `X` funkcji szablonu, który przyjmuje typ `T&&` jako jego parametr deduces Wnioskowanie argumentu szablonu `T` jako `X`. W związku z tym parametr ma typ `X&&`. Jeśli argument funkcji jest l-wartością lub `const` l-wartością, kompilator deduces jego typ odwołania do wartości lub `const` odwołania do wartości tego typu.  
  
 W poniższym przykładzie deklaruje jeden szablon struktury i następnie specjalizuje się dla różnych typów odniesienia. `print_type_and_value` Funkcja przyjmuje odwołanie do r-wartości jako jego parametr i przekazuje je do odpowiednich specjalna wersja `S::print` metody. `main` Funkcja przedstawiono różne sposoby, aby wywołać `S::print` metody.  
  
```  
// template-type-deduction.cpp  
// Compile with: /EHsc  
#include <iostream>  
#include <string>  
using namespace std;  
  
template<typename T> struct S;  
  
// The following structures specialize S by   
// lvalue reference (T&), const lvalue reference (const T&),   
// rvalue reference (T&&), and const rvalue reference (const T&&).  
// Each structure provides a print method that prints the type of   
// the structure and its parameter.  
  
template<typename T> struct S<T&> {  
   static void print(T& t)  
   {  
      cout << "print<T&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<const T&> {  
   static void print(const T& t)  
   {  
      cout << "print<const T&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<T&&> {  
   static void print(T&& t)  
   {  
      cout << "print<T&&>: " << t << endl;  
   }  
};  
  
template<typename T> struct S<const T&&> {  
   static void print(const T&& t)  
   {  
      cout << "print<const T&&>: " << t << endl;  
   }  
};  
  
// This function forwards its parameter to a specialized  
// version of the S type.  
template <typename T> void print_type_and_value(T&& t)   
{  
   S<T&&>::print(std::forward<T>(t));  
}  
  
// This function returns the constant string "fourth".  
const string fourth() { return string("fourth"); }  
  
int main()  
{  
   // The following call resolves to:  
   // print_type_and_value<string&>(string& && t)  
   // Which collapses to:  
   // print_type_and_value<string&>(string& t)  
   string s1("first");  
   print_type_and_value(s1);   
  
   // The following call resolves to:  
   // print_type_and_value<const string&>(const string& && t)  
   // Which collapses to:  
   // print_type_and_value<const string&>(const string& t)  
   const string s2("second");  
   print_type_and_value(s2);  
  
   // The following call resolves to:  
   // print_type_and_value<string&&>(string&& t)  
   print_type_and_value(string("third"));  
  
   // The following call resolves to:  
   // print_type_and_value<const string&&>(const string&& t)  
   print_type_and_value(fourth());  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
print<T&>: first  
print<const T&>: second  
print<T&&>: third  
print<const T&&>: fourth  
```  
  
 Aby rozwiązać każde wywołanie `print_type_and_value` funkcji, kompilator najpierw jest przeprowadzane Wnioskowanie argumentu szablonu. Kompilator następnie stosuje odwołanie zwijanie reguły, gdy ta funkcja zastępuje argumenty szablonu wnioskowanym dla typów parametrów. Na przykład przekazywanie zmiennej lokalnej `s1` do `print_type_and_value` funkcja powoduje, że kompilator, aby utworzyć następujące sygnatury funkcji:  
  
```  
print_type_and_value<string&>(string& && t)  
```  
  
 Kompilator korzysta odwołanie zwijanie reguły w celu zmniejszenia ilości podpis do następującego:  
  
```  
print_type_and_value<string&>(string& t)  
```  
  
 Ta wersja `print_type_and_value` funkcja następnie przekazuje jej parametr poprawną wersję specjalne `S::print` metody.  
  
 Poniższa tabela zawiera podsumowanie odwołanie zwijanie zasady wnioskowanie typu argumentu szablonu:  
  
|||  
|-|-|  
|Typ rozszerzonej|Typ zwinięte|  
|`T& &`|`T&`|  
|`T& &&`|`T&`|  
|`T&& &`|`T&`|  
|`T&& &&`|`T&&`|  
  
 Wnioskowanie argumentu szablonu jest ważnym elementem wdrażania doskonałego przekazywania dalej. W sekcji doskonałego przekazywania, której przedstawiono wcześniej w tym temacie opisano doskonałego przekazywania dalej bardziej szczegółowo.  
  
## <a name="summary"></a>Podsumowanie  
 Odwołania wartościowane prawostronnie odróżnienia lvalues rvalues. Mogą one pomóc w poprawy wydajności aplikacji dzięki wyeliminowaniu konieczności dla przydziału pamięci niepotrzebnych i operacje kopiowania. Umożliwiają one również zapisu jednej wersji funkcję, która akceptuje dowolne argumenty i przekazuje je do innej funkcji tak, jakby była bezpośredniego wywoływania innych funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Deklarator odwołania do wartości: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)   
