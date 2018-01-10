---
title: "enable_if — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::enable_if
dev_langs: C++
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4df9da47925919a005d3c235d35f57f54a3568aa
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="enableif-class"></a>enable_if — Klasa
Warunkowo sprawia, że wystąpienie typu techniki SFINAE przeciążenia. Zagnieżdżony element typedef `enable_if<Condition,Type>::type` istnieje, i jest synonimem `Type`— tylko wtedy, gdy `Condition` jest `true`.  
  
## <a name="syntax"></a>Składnia  
  
```
template <bool B, class T = void>
struct enable_if;
```  
  
#### <a name="parameters"></a>Parametry  
 `B`  
 Wartość, która określa istnienie wynikowy typ.  
  
 `T`  
 Typ do utworzenia wystąpienia, jeśli `B` ma wartość true.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `B` ma wartość true, `enable_if<B, T>` ma zagnieżdżonych typedef o nazwie "typ", który jest synonimem `T`.  
  
 Jeśli `B` ma wartość false, `enable_if<B, T>` nie ma zagnieżdżonych typedef o nazwie "type".  
  
 Znajduje się ten szablon alias:  
  
```cpp  
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```  
  
 W języku C++ awarii podstawiania parametrów szablonu nie jest to błąd w sobie — jest to określane jako *techniki SFINAE* (błąd podstawienia nie jest błąd). Zazwyczaj `enable_if` służy do usuwania z wiązaniem kandydatów — to znaczy go culls zestaw przeciążenia — tak, aby jedna definicja można odrzucić na rzecz innej. Odpowiada to zachowanie techniki SFINAE. Aby uzyskać więcej informacji na temat techniki SFINAE, zobacz [awarii podstawienia nie jest błąd](http://go.microsoft.com/fwlink/p/?linkid=394798) w witrynie Wikipedia.  
  
 Poniżej przedstawiono cztery przykładowe scenariusze:  
  
-   Scenariusz 1: Zawijanie zwracany typ funkcji:  
  
 ```cpp  
    template <your_stuff>  
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
 }
// The alias template makes it more concise:
    template <your_stuff>  
enable_if_t<your_condition, your_return_type>  
yourfunction(args) {// ...
 }
```  
  
-   Scenariusz 2: Dodawanie parametru funkcji, który ma domyślnego argumentu:  
  
 ```cpp  
    template <your_stuff>  
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
 }
```  
  
-   Scenariusz 3: Dodawanie parametru szablonu, który ma domyślnego argumentu:  
  
 ```cpp  
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>  
rest_of_function_declaration_goes_here
```  
  
-   Scenariusz 4: Jeśli funkcja ma argument bez szablonu, może zawijać jej typ:  
  
 ```cpp  
    template <typename T>  
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>  
s) {// ...
 }
```  
  
 Scenariusz 1 nie działa z konstruktorów i operatory konwersji, ponieważ nie mają zwracanych typów.  
  
 Scenariusz 2 pozostawia parametru bez nazwy. Można powiedzieć `::type Dummy = BAR`, ale nazwa `Dummy` nie ma znaczenia, i może wyzwolić ostrzeżenie "nieużywane parametru" nadanie mu nazwy. Musisz wybrać `FOO` typ parametru funkcji i `BAR` argument domyślny.  Można powiedzieć `int` i `0`, ale następnie użytkownicy kodu może przypadkowo przekazać do funkcji całkowitą dodatkowe, które zostałyby one zignorowane. Zamiast tego zaleca się używanie `void **` i `0` lub `nullptr` ponieważ prawie nic nie można przekonwertować na typ `void **`:  
  
```cpp  
template <your_stuff>  
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```  
  
 Scenariusz 2 działa również w przypadku zwykłej konstruktorów.  Jednak ta funkcja nie działa dla operatorów konwersji, ponieważ one nie może przyjąć dodatkowe parametry.  Ponadto nie działa dla [ze zmienną liczbą argumentów](../cpp/ellipses-and-variadic-templates.md) konstruktorów ponieważ dodanie dodatkowych parametrów sprawia, że parametr funkcji-ustalona kontekst pakietu, a tym samym pozbawia sensu `enable_if`.  
  
 Scenariusz 3 używa nazwy `Dummy`, ale jest opcjonalny. Tylko " `typename = typename`" będzie działać, ale jeśli uważasz, że wygląda nieco dziwne, można użyć nazwy "zastępczego" — po prostu nie używaj jednej, które również mogą być używane w definicji funkcji. Nie przyznaje typu na `enable_if`domyślne void i doskonale to uzasadnione, ponieważ nie zależy Ci co `Dummy` jest. Działa to w przypadku wszystkich operatorów konwersji i [ze zmienną liczbą argumentów](../cpp/ellipses-and-variadic-templates.md) konstruktorów.  
  
 Scenariusz 4 działa w konstruktorach, które nie mają zwracanych typów, a tym samym rozwiązuje ograniczenia zawijania scenariusz 1.  Jednak Scenariusz 4 jest ograniczona do argumentów bez szablonu funkcji, które nie są zawsze dostępne.  (Używanie Scenariusz 4 na parametr szablonu funkcji uniemożliwia Wnioskowanie argumentu szablonu z pracy).  
  
 `enable_if`są wydajne, ale również niebezpieczne jest niewłaściwego użycia.  Ponieważ jego celem jest zapewnienie kandydatów znikają przed wiązaniem, gdy jest niewłaściwego użycia, jego skutków może być bardzo trudne.  Poniżej przedstawiono kilka zaleceń:  
  
-   Nie używaj `enable_if` wybrać między implementacji w czasie kompilacji. Nigdy nie zapisu jedną `enable_if` dla `CONDITION` i drugi dla `!CONDITION`.  Zamiast tego należy użyć *tagu wysyłania* wzorzec — na przykład z algorytmu, który wybiera implementacji w zależności od możliwości Iteratory one otrzymuje.  
  
-   Nie używaj `enable_if` wymusić wymagania.  Jeśli chcesz sprawdzić poprawność parametrów szablonu, a w przypadku niepowodzenia weryfikacji, spowodować wystąpienie błędu zamiast zaznaczania innej implementacji, należy użyć [static_assert](../cpp/static-assert.md).  
  
-   Użyj `enable_if` gdy masz zestawu przeciążenia, które w przeciwnym razie zapewnia dobre kodu niejednoznaczne.  Najczęściej dzieje się tak w niejawnej konwersji konstruktorów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyjaśniono, jak funkcja szablonu standardowa biblioteka C++ [std::make_pair()](../standard-library/utility-functions.md#make_pair) korzysta z `enable_if`.  
  
```cpp  
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```  
  
  W tym przykładzie `make_pair("foo", "bar")` zwraca `pair<const char *, const char *>`. Rozpoznanie przeciążenia musi ustalić, które `func()` ma. `pair<A, B>`ma niejawnie konwertowania konstruktora z `pair<X, Y>`.  Nie jest to nowy — w języku C ++ 98. Jednak w języku C ++ 98/03, sygnatury konstruktora niejawnie konwertowania istnieje zawsze, nawet jeśli jest ona `pair<int, int>(const pair<const char *, const char *>&)`.  Rozpoznanie przeciążenia nie szczególną uwagę, że próba uruchomienia tego konstruktora horribly rozkłada ponieważ `const char *` nie umożliwiają niejawnej konwersji na `int`; tylko wyszukiwania podpisów, przed funkcją tworzone są definicje.  W związku z tym przykładowy kod jest niejednoznaczny, ponieważ istnieje podpisów można przekonwertować `pair<const char *, const char *>` zarówno `pair<int, int>` i `pair<string, string>`.  
  
 C ++ 11 rozwiązać tę niejednoznaczność za pomocą `enable_if` do upewnij się, że `pair<A, B>(const pair<X, Y>&)` istnieje **tylko** podczas `const X&` niejawnie przekonwertować `A` i `const Y&` niejawnie przekonwertować `B`.  Dzięki temu Rozpoznanie przeciążenia określić, że `pair<const char *, const char *>` nie jest możliwe do przekonwertowania na `pair<int, int>` i że przeciążenie pobierającej `pair<string, string>` jest działało.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



