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
ms.openlocfilehash: 2eddd87660d996e0d726c4453e0eb732a5553b99
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416661"
---
# <a name="ellipses-and-variadic-templates"></a>Wielokropki i szablony wariadyczne
W tym artykule przedstawiono sposób użycia wielokropka (`...`) z szablonów języka C++ ze zmienną liczbą argumentów. Wielokropek miał wiele zastosowań C i C++. Obejmują one listy zmiennych argumentów dla funkcji. `printf()` Funkcji z biblioteki środowiska uruchomieniowego C jest jednym z przykładów dobrze znany.  
  
 A *ze zmienną liczbą argumentów szablonu* jest szablon klasy lub funkcji, który obsługuje dowolną liczbę argumentów. Mechanizm ten jest przydatny dla deweloperów biblioteki języka C++, ponieważ zastosować je do szablonów klas i szablony funkcji, a tym samym zapewniają szeroką gamę bezpieczne i nieuproszczony funkcjonalność i elastyczność.  
  
## <a name="syntax"></a>Składnia  
 Wielokropek jest używany na dwa sposoby przez Szablony ze zmienną liczbą argumentów. Po lewej stronie nazwy parametru, oznacza *pakiet parametrów*, a z prawej strony nazwy parametru rozszerza pakietów parametrów na oddzielnych nazwy.  
  
 Poniżej przedstawiono podstawowy przykład *ze zmienną liczbą argumentów szablonu klasy* definicji składni:  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 Dla pakietów parametrów i rozszerzenia można dodać odstępy wokół Wielokropek na podstawie preferencji użytkownika, jak pokazano w tym przykładzie:  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 Lub to:  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 Powiadomienie, że w tym artykule używa konwencji, który jest widoczny w pierwszym przykładzie (wielokropek jest dołączony do `typename`).  
  
 W powyższych przykładach `Arguments` jest pakietem parametrów. Klasa `classname` może zaakceptować zmienną liczbę argumentów, jak te przykłady:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 Za pomocą definicji klasy ze zmienną liczbą argumentów szablonu, możesz również wymagać co najmniej jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 Poniżej przedstawiono podstawowy przykład *ze zmienną liczbą argumentów szablonu funkcji* składni:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 `Arguments` Pakiet parametrów jest rozszerzana do użytku, jak pokazano w następnej sekcji **opis szablony wariadyczne**.  
  
 Możliwe są inne formy Składnia funkcji ze zmienną liczbą argumentów szablonu — tym między innymi, te przykłady:  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 Specyfikatory, takich jak `const` również są dozwolone:  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 Jako z ze zmienną liczbą argumentów szablonu definicje klas, możesz wprowadzić funkcje, które wymagają co najmniej jeden parametr:  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 Użyj szablony Wariadyczne `sizeof...()` — operator (niezwiązanych ze sobą starszej `sizeof()` operatora):  
  
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
 W tym artykule opisano wcześniej, umieszczania wielokropka, definiujący parametr pakietów i rozszerzenia jako "po lewej stronie nazwy parametru, oznacza ona pakietem parametrów i z prawej strony nazwy parametru rozszerza on pakietów parametrów na oddzielnych nazwy". To jest technicznie wartość true, ale może być trudne w tłumaczeniu do kodu. Należy wziąć pod uwagę:  
  
-   W przypadku — listy parametrów szablonu — (`template <parameter-list>`), `typename...` wprowadza pakiet parametrów szablonu.  
  
-   W parametru deklaracja — klauzula (`func(parameter-list)`), "najwyższego poziomu" wielokropka wprowadza pakiet parametrów funkcji i ważne jest pozycjonowanie wielokropka:  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   W przypadku, gdy wielokropka pojawi się natychmiast po nazwę parametru, masz rozwinięciem pakietu parametrów.  
  
## <a name="example"></a>Przykład  
 Dobrym sposobem ilustrują mechanizm ze zmienną liczbą argumentów szablonu funkcji jest używany w ponownie zapisać niektórych funkcji `printf`:  
  
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
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  Większości wdrożeń, zawierające ze zmienną liczbą argumentów szablonu funkcji rekursję jakiegoś, ale jest nieco inne niż tradycyjne rekursji.  Rekursja tradycyjnych obejmuje funkcję wywoływania się za pomocą takiego samego podpisu. (Może być przeciążona lub szablonem, ale wybrany jest zawsze takiego samego podpisu). Rekursja ze zmienną liczbą argumentów obejmuje wywoływania ze zmienną liczbą argumentów szablonu funkcji za pomocą różnych (prawie zawsze malejącej) liczby argumentów i tym samym sygnaturze się inny podpis zawsze. "Podstawowa case" jest nadal wymagana, ale jest inny rodzaj rekursji.  
  
