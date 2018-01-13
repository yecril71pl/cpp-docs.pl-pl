---
title: "Jednolite inicjowanie i delegowanie konstruktorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68d8f9724ba7f26ac9df9b81c1e4c3f6213f76a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Jednolite inicjowanie i delegowanie konstruktorów
W nowoczesnych wersji języka C++, można użyć *nawiasy inicjowania* dla dowolnego typu bez znaku równości. Ponadto umożliwia konstruktory delegujące uprościć kod, jeśli masz wiele konstruktorów, które wykonały podobne.  
  
## <a name="brace-initialization"></a>Inicjowanie nawiasu klamrowego  
 Inicjowanie nawias klamrowy służącego do dowolnej klasy, struktury lub związku. Jeśli typ ma konstruktora domyślnego jawnie lub niejawnie zadeklarowany, można użyć domyślnego nawiasu klamrowego inicjowania (z pustymi nawiasami klamrowymi). Na przykład następującej klasy mogą być inicjowane przez przy użyciu domyślnych i inicjowania nawiasu klamrowego innych niż domyślne:  
  
```cpp  
#include <string>  
using namespace std;  
  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}  
double m_double;  
string m_string;  
};  
  
int main()  
{  
    class_a c1{};  
    class_a c1_1;  
  
    class_a c2{ "ww" };  
    class_a c2_1("xx");  
  
    // order of parameters is the same as the constructor  
    class_a c3{ "yy", 4.4 };  
    class_a c3_1("zz", 5.5);  
}  
  
```  
  
 Jeśli klasa ma konstruktorów innych niż domyślne, kolejność klasy, które elementy członkowskie w inicjatorze nawiasów klamrowych jest kolejność wyświetlania odpowiednich parametrów w konstruktorze, nie kolejność, w którym są deklarowane jako członkowie (jak `class_a` w poprzedniego przykładu). W przeciwnym razie jeśli typ nie ma zadeklarowane konstruktora, kolejność wyświetlania elementów członkowskich w inicjatorze nawias klamrowy jest taka sama jak kolejność, w którym jest zadeklarowany; w takim przypadku należy można zainicjować dowolnej liczby publicznych elementów członkowskich mają, ale nie można pominąć dowolnego elementu członkowskiego. W poniższym przykładzie przedstawiono kolejność, która jest używana podczas inicjowania nawias klamrowy, gdy nie istnieje żaden konstruktor zadeklarowane:  
  
```cpp  
class class_d {  
public:  
    float m_float;  
    string m_string;  
    wchar_t m_char;  
};  
  
int main()  
{  
    class_d d1{};  
    class_d d1{ 4.5 };  
    class_d d2{ 4.5, "string" };  
    class_d d3{ 4.5, "string", 'c' };  
  
    class_d d4{ "string", 'c' }; // compiler error  
    class_d d5("string", 'c', 2.0 }; // compiler error  
}   
```  
  
 Jeśli domyślny konstruktor jest jawnie zadeklarowana, ale oznaczone jako usunięte, nie można użyć inicjowanie nawiasu klamrowego domyślnych:  
  
```cpp  
class class_f {  
public:  
    class_f() = delete;  
    class_f(string x): m_string { x } {}  
    string m_string;  
};  
int main()  
{  
    class_f cf{ "hello" };  
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function  
}  
```  
  
 Można użyć nawiasów klamrowych inicjowania dowolnym zwykle należy inicjowanie — na przykład jako parametr funkcji lub wartości zwracanej lub z `new` — słowo kluczowe:  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## <a name="initializerlist-constructors"></a>initializer_list konstruktorów  
 [Initializer_list klasy](../standard-library/initializer-list-class.md) reprezentuje listę obiektów określonego typu, które mogą być używane w Konstruktorze i w innych kontekstach. Można utworzyć initializer_list przy użyciu inicjowania nawiasu klamrowego:  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  Aby korzystać z tej klasy, należy uwzględnić [< initializer_list >](../standard-library/initializer-list.md) nagłówka.  
  
 `initializer_list` Mogą zostać skopiowane. W takim przypadku nową listę elementów członkowskich są odwołania do elementów członkowskich oryginalnej listy:  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 Klasy kontenerów biblioteki standardowej, a także `string`, `wstring`, i `regex`, ma `initializer_list` konstruktorów. Poniższe przykłady pokazują, jak nawiasy inicjowania konstruktorów te:  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## <a name="delegating-constructors"></a>Delegowanie konstruktorów  
 Wiele klas ma wiele konstruktorów, które wykonują podobnych elementów — na przykład Waliduj parametry:  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c() {}  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) {   
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) {  
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
    }  
};  
```  
  
 Pozwala zredukować kodu powtarzających się przez dodanie funkcji, który wykonuje wszystkie sprawdzania poprawności, ale kod `class_c` będzie można łatwiej zrozumieć i konserwacji, jeśli jeden konstruktor może przekazywać niektóre pracy z innym. Aby dodać konstruktory delegujące, użyj `constructor (. . .) : constructor (. . .)` składni:  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) : class_c(my_max) {   
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
}  
};  
int main() {  
  
    class_c c1{ 1, 3, 2 };  
}  
  
```  
  
 Jak można kroków opisanych w poprzednim przykładzie, zwróć uwagę, że Konstruktor `class_c(int, int, int)` najpierw wywołuje konstruktor `class_c(int, int)`, który z kolei wywołuje `class_c(int)`. Każdy z konstruktorów wykonuje pracy, który nie jest wykonywane przez inne konstruktorów.  
  
 Pierwszy Konstruktor, który jest nazywany inicjuje obiekt tak, aby wszystkie jego elementy członkowskie są inicjowane w tym momencie. Inicjowanie elementu członkowskiego w konstruktora, który deleguje do innego konstruktora, nie są w sposób pokazany poniżej:  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    // member initialization here, no delegate  
    class_a(string str) : m_string{ str } {}  
  
    //can’t do member initialization here  
    // error C3511: a call to a delegating constructor shall be the only member-initializer  
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}  
  
    // only member assignment  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string;  
};  
  
```  
  
 Kolejnym przykładzie pokazano sposób użycia inicjatory niestatycznego elementu członkowskiego danych. Zwróć uwagę, że jeśli Konstruktor inicjuje także członkiem danych danego, zastąpić inicjator elementu członkowskiego:  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };  
};  
  
int main() {  
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"  
    int y = 4;  
}  
```  
  
 Składni konstruktora delegowania nie zapobiega przypadkowemu tworzeniu rekursji konstruktora — Constructor1 wywołuje Constructor2, która wywołuje Constructor1 — i nie są generowane błędy momentu przepełnienia stosu. Jest obowiązek pominąć cykli.  
  
```cpp  
class class_f{  
public:  
    int max;  
    int min;  
  
    // don't do this  
    class_f() : class_f(6, 3){ }  
    class_f(int my_max, int my_min) : class_f() { }  
};  
```