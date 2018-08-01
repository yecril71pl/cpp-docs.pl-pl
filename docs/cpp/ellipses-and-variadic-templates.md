---
title: Wielokropki i szablony Wariadyczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45dc0dfe85e7693cdea9c6e469ff347d75c13d57
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402949"
---
# <a name="ellipses-and-variadic-templates"></a>Wielokropki i szablony wariadyczne
W tym artykule przedstawiono sposób użycia wielokropka (`...`) za pomocą szablonów ze zmienną liczbą argumentów języka C++. Wielokropek miał wiele zastosowań w C i C++. Należą do nich listy zmiennych argumentów dla funkcji. `printf()` Funkcji z biblioteki środowiska uruchomieniowego języka C jest jednym z najbardziej znanych przykładów.  
  
 A *szablonu wariadycznego* jest szablonu klasy lub funkcji, która obsługuje dowolną liczbę argumentów. Ten mechanizm jest szczególnie przydatny dla deweloperów bibliotek C++, ponieważ dotyczą zarówno szablony klas, jak i szablonów funkcji, a tym samym zapewniać szeroki zakres bezpiecznego typu i zaawansowanej funkcjonalności i elastyczności.  
  
## <a name="syntax"></a>Składnia  
 Wielokropek jest używany na dwa sposoby przez zmienne szablony. Po lewej stronie nazwy parametru, oznacza *pakiet parametrów*, a po prawej stronie nazwy parametru, rozszerza pakiety parametru w osobne nazwy.  
  
 Oto przykład podstawowej *klasy zmiennego szablonu* składnię definicji:  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 Pakietami parametrów i rozszerzenia można dodać odstęp wokół Wielokropek na podstawie preferencji użytkownika, jak pokazano w tych przykładach:  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 Lub to:  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 Zwróć uwagę, że w tym artykule używa konwencji, która jest wyświetlana w pierwszym przykładzie (wielokropka jest dołączony do `typename`).  
  
 W powyższych przykładach *argumenty* jest pakietem parametrów. Klasa `classname` może akceptować zmienną liczbę argumentów, jak w następujących przykładach:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
```  
  
 Za pomocą definicji klasy zmiennej szablonu, możesz również wymagać co najmniej jednego parametru:  
  
```cpp  
template <typename First, typename... Rest> class classname;  
```  
  
 Oto przykład podstawowej *funkcji zmiennego szablonu* składni:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 *Argumenty* pakiet parametrów jest rozszerzany do użycia, jak pokazano w następnej sekcji **zrozumienie szablonów zmiennych**.  
  
 Możliwe są inne formy Składnia funkcji zmiennych szablonów — w tym, między innymi, te przykłady:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 Specyfikatory takie jak **const** są również dozwolone:  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
```  
  
 Jak z definicjami klasy zmiennej szablonu można także wykonać funkcje, które wymagają co najmniej jednego parametru:  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
```  
  
 Szablony zmienne korzystają `sizeof...()` — operator (niezwiązany ze starszym `sizeof()` operator):  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    constexpr auto numargs{ sizeof...(Arguments) };  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
```  
  
## <a name="more-about-ellipsis-placement"></a>Więcej informacji na temat umieszczania wielokropka  
 Wcześniej w tym artykule opisano umieszczania wielokropka, definiujący pakietami parametrów i rozszerzenia jako "po lewej stronie nazwy parametru, oznacza pakiet parametrów, a po prawej stronie nazwy parametru, rozszerza pakiety parametru w osobne nazwy". Z technicznego punktu widzenia obowiązuje, ale może być myląca w tłumaczeniu do kodu. Należy wziąć pod uwagę:  
  
-   W szablonie listy parametrów (`template <parameter-list>`), `typename...` wprowadza pakiet parametrów szablonu.  
  
-   W parametrze deklaracji — klauzuli (`func(parameter-list)`), "najwyższego poziomu" wielokropka wprowadza pakiet parametrów funkcji i pozycjonowanie wielokropka jest ważne:  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   W przypadku, gdy przycisk wielokropka pojawia się natychmiast po nazwę parametru, masz rozwinięciem pakietu parametrów.  
  
## <a name="example"></a>Przykład  
 Dobrym sposobem ilustrowania mechanizmu funkcji zmiennych szablonu jest z niego korzystać w celu ponownego napisania niektórych funkcji `printf`:  
  
```cpp  
#include <iostream>  
  
using namespace std;  
  
void print() {  
    cout << endl;  
}  
  
template <typename T> void print(const T& t) {  
    cout << t << endl;  
}  
  
template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {  
    cout << first << ", ";  
    print(rest...); // recursive call using pack expansion syntax  
}  
  
int main()  
{  
    print(); // calls first overload, outputting only a newline  
    print(1); // calls second overload  
  
    // these call the third overload, the variadic template,   
    // which uses recursion as needed.  
    print(10, 20);  
    print(100, 200, 300);  
    print("first", 2, "third", 3.14159);  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```Output  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  Większość implementacji, które zawierają funkcje szablonów ze zmienną liczbą argumentów rekursję jakąś formę, ale różni się nieco od tradycyjnych rekursji.  Tradycyjna rekursja obejmuje wywoływanie się za pomocą tego samego podpisu funkcji przez. (Może to być przeciążone lub oparte na szablonach, ale ten sam podpis jest wybierany każdorazowo). Rekursja zmienna polega na wywołanie funkcji ze zmienną liczbą argumentów szablonu za pomocą różnych (prawie zawsze malejących) argumentów, a tym samym wybijaniu inny podpis każdym. "Przypadek podstawowy" jest wciąż wymagany, ale różni się rodzaj rekursji.  