---
title: '&lt;funkcjonalności&gt;'
ms.date: 11/04/2016
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
ms.openlocfilehash: 3e838bf10b710caf12b5dcd51cad4cf625d887e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457320"
---
# <a name="ltfunctionalgt"></a>&lt;funkcjonalności&gt;

Definiuje funkcje standardowej biblioteki języka C++, które pomagają tworzyć *funkcji obiektów*— nazywanego także funktory — i ich wiążących. Obiekt funkcji jest obiektem typu, który definiuje `operator()`. Obiekt funkcyjny mogą być wskaźnik funkcji, ale zazwyczaj obiekt jest używany do przechowywania dodatkowych informacji, które może uzyskać dostęp podczas wywołania funkcji.

## <a name="syntax"></a>Składnia

```cpp
#include <functional>
```

## <a name="remarks"></a>Uwagi

Algorytmy wymagają dwóch typów obiektów funkcyjnych: jednoargumentowy i binarny. Obiekty funkcyjne jednoargumentowe wymaga jednego argumentu i obiekty binarne funkcji wymaga dwóch argumentów. Obiektu funkcyjnego i wskaźników do funkcji mogą być przekazywane jako predykatu do algorytmu, ale obiekty funkcyjne są również dostosowywalne i zwiększyć zakres, elastyczność i efektywność standardowej biblioteki języka C++. Jeśli na przykład wartość potrzebne może być powiązane z funkcją przed przesłaniem do algorytmu, następnie wskaźnik funkcji nie można użyć. Funkcja adapterów konwertowanie wskaźników funkcji obiekty potężnej funkcji, które mogą być powiązane z wartością. Nagłówek \<funkcjonalności > zawiera także adapterów funkcja elementu członkowskiego, zezwalających na wywoływanie jako obiekty funkcyjne potężnej funkcji elementu członkowskiego. Funkcje są potężnej, jeśli mają one deklaracje typu zagnieżdżonego, określając ich argumentów i zwracanych typów. C++ Standard wymaga, że to zdolności adaptacyjnych jest implementowana przez wszystkie klasy obiektu standardowego dziedziczyć z klas bazowych unary_function lub binary_function —. Obiekty funkcji i ich adapterów umożliwiają standardowej biblioteki C++ uaktualnić istniejące aplikacje i pomóc zintegrować biblioteki środowiska programowania w języku C++.

Obiekty funkcji w implementacji Visual C++ \<funkcjonalności > zawiera *przezroczyste funktory operatora*, specjalizacje standardu funkcji obiektów i nie mają żadnych parametrów szablonu i Wykonaj Perfekcyjne przekazywanie argumentów funkcji i doskonałe zwrócenia wyniku. Ta funkcja jest częścią specyfikacji języka C ++ 14 standardowa wersja robocza. Te specjalizacje szablonu nie wymagają określenia typy argumentów, gdy wywołujesz arytmetyczne, logiczne, porównanie i funktory operatora bitowego. Można przeciążać operacje arytmetyczne, logiczne, porównanie lub operatory bitowe własnych typów lub kombinacji heterogenicznych typów i następnie użyć przezroczyste funktory operatora jako argumenty funkcji. Na przykład jeśli danego typu *MyType* implementuje `operator<`, można wywołać `sort(my_collection.begin(), my_collection.end(), less<>())` zamiast jawne określenie typu `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.

## <a name="c11c14-implementation"></a>C ++ 11 / C ++ 14 implementacji

Następujące funkcje zostały dodane w implementacji Visual C++, C ++ 11 / C ++ 14:

- A *sygnatury wywołania* nazywa się typem zwracanym, a następnie ujęty w nawiasy rozdzielaną przecinkami listę zero lub więcej typów argumentów.

- A *typ możliwy do wywołania* jest wskaźnikiem do funkcji, wskaźnik do funkcji składowej, wskaźnik do składowej danych lub typu klasy, w których obiekty można pojawiają się natychmiast po lewej stronie operatora wywołania funkcji.

- A *wywoływanego obiektu* jest obiektem typu możliwy do wywołania.

- A *wywołać typ otoki* to typ, który przechowuje wywoływanego obiektu i obsługuje operację wywołania, które powodują przekazanie do tego obiektu.

- A *wywołanie otoką* jest obiektem typu wywołania otoki.

- A *obiekt docelowy* jest obiekt w posiadaniu obiektu wywołania.

Pseudo-funkcja `INVOKE(f, t1, t2, ..., tN)` oznacza to jedną z następujących czynności:

- `(t1.*f)(t2, ..., tN)` gdy `f` jest wskaźnikiem do funkcji składowej klasy typu `T` i `t1` jest obiektem typu `T` lub odwołanie do obiektu typu `T` lub odwołanie do obiektu typu pochodną `T`.

- `((*t1).*f)(t2, ..., tN)` gdy `f` jest wskaźnikiem do funkcji składowej klasy typu `T` i `t1` nie jest jednym z typów, opisanych w poprzedniej pozycji.

- `t1.*f` Gdy N == 1 i `f` to wskaźnik do danych elementów członkowskich klasy `T` i `t1` jest obiektem typu `T` lub odwołanie do obiektu typu `T` lub odwołanie do obiektu typu pochodnego od `T`.

- `(*t1).*f` Gdy N == 1 i `f` to wskaźnik do danych elementów członkowskich klasy `T` i `t1` nie jest jednym z typów, opisanych w poprzedniej pozycji.

- `f(t1, t2, ..., tN)` we wszystkich innych przypadkach.

Pseudo-funkcja `INVOKE(f, t1, t2, ..., tN, R)` oznacza `INVOKE(f, t1, t2, ..., tN)` niejawnie konwertowane na `R`.

Jeśli wywołanie otoką *typ wyniku słabe*, typ jego typ elementu członkowskiego `result_type` opiera się na typ `T` obiektu docelowego otoki, w następujący sposób:

- Jeśli `T` jest wskaźnikiem do funkcji, `result_type` jest synonimem dla zwracanego typu `T`.

- Jeśli `T` jest wskaźnikiem do funkcji składowej `result_type` jest synonimem dla zwracanego typu `T`.

- Jeśli `T` jest typu klasy, która ma typ elementu członkowskiego `result_type`, następnie `result_type` jest synonimem dla `T::result_type`.

- W przeciwnym razie nie ma żadnego elementu członkowskiego `result_type`.

Otoka co wywołanie ma Konstruktor przenoszący i Konstruktor kopiujący. A *prostego wywołania otoki* jest otoką wywołania mającego przypisania operatora i której Konstruktor kopiujący, Konstruktor przenoszący i operator przypisania nie zgłaszają wyjątki. A *przekazywania wywołanie otoką* jest otoką wywołań, który można wywoływać za pomocą listy argumentów dowolnego, i który dostarcza argumentów na obiekt opakowany jako odwołania. Wszystkie argumenty r-wartości są dostarczane jako odwołania rvalue, a argumenty lvalue są dostarczane jako odwołania lvalue.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|Klasa, która opisuje wyjątek generowany w celu wskazania, że wywołanie `operator()` na [funkcja](../standard-library/function-class.md) obiektu nie powiodło się, ponieważ obiekt był pusty.|
|[binary_negate](../standard-library/binary-negate-class.md)|Klasa szablonu, zapewniając funkcją składową, negujące wartość zwracaną określoną funkcję binarny.|
|[binder1st](../standard-library/binder1st-class.md)|Klasa szablonu, zapewniając konstruktora, który konwertuje obiekt binarny funkcji do obiektu funkcyjnego jednoargumentowe przez powiązanie pierwszy argument funkcji binarnego na określoną wartość.|
|[binder2nd —](../standard-library/binder2nd-class.md)|Klasa szablonu, zapewniając konstruktora, który konwertuje obiekt binarny funkcji do obiektu funkcyjnego jednoargumentowe przez powiązanie drugi argument funkcji binarnego na określoną wartość.|
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Klasa adaptera, która umożliwia const funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiekt funkcji jednoargumentowe podczas inicjowania przy użyciu argument odwołania.|
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Klasa adaptera, która umożliwia stałą funkcję elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiektu funkcyjnego jednoargumentowe podczas inicjowania przy użyciu argumentu będącego wskaźnikiem.|
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Klasa adaptera, która umożliwia const funkcja elementu członkowskiego, która przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argument odwołania.|
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Klasa adaptera, która umożliwia stałą funkcję elementu członkowskiego, która przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argumentu będącego wskaźnikiem.|
|[— Funkcja](../standard-library/function-class.md)|Klasa, która otacza obiekt możliwy do wywołania.|
|[Skrót](../standard-library/hash-class.md)|Klasa, która oblicza wartość skrótu dla wartości.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Klasa, która sprawdza, czy określony typ jest generowany przez wywołanie metody `bind`.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|Klasa, która sprawdza, czy określony typ jest symbolem zastępczym.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiekt funkcji jednoargumentowe po zainicjowaniu z argumentem odwołania.|
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, która nie przyjmuje żadnych argumentów, które ma być wywoływana jako obiektu funkcyjnego jednoargumentowe podczas inicjowania przy użyciu argumentu będącego wskaźnikiem.|
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argument odwołania.|
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Klasa adaptera, który umożliwia `non_const` funkcja elementu członkowskiego, który przyjmuje jeden argument do wywoływania jako obiektu binarnego funkcja podczas inicjowania przy użyciu argumentu będącego wskaźnikiem.|
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Konwertuje wskaźnika funkcji binarne potężnej funkcja binarnego.|
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Konwertuje funkcję jednoargumentową potężnej jednoargumentowe wskaźnika funkcji.|
|[reference_wrapper —](../standard-library/reference-wrapper-class.md)|Klasa, która otacza odwołania.|
|[unary_negate](../standard-library/unary-negate-class.md)|Klasa szablonu, zapewniając funkcją składową, negujące wartość zwracaną funkcję jednoargumentową określony.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[powiązania](../standard-library/functional-functions.md#bind)|Wiąże argumenty wywoływanego obiektu.|
|[bind1st](../standard-library/functional-functions.md#bind1st)|Funkcja szablonu pomocnika, która tworzy adapter do skonwertowania obiektu binarnego funkcja do obiektu funkcyjnego jednoargumentowe przez powiązanie pierwszy argument funkcji binarnego na określoną wartość.|
|[bind2nd](../standard-library/functional-functions.md#bind2nd)|Funkcja szablonu pomocnika, która tworzy adapter do skonwertowania obiektu binarnego funkcja do obiektu funkcyjnego jednoargumentowe przez powiązanie drugi argument funkcji binarnego na określoną wartość.|
|[bit_and](../standard-library/functional-functions.md#bit_and)|Zwraca wartość iloczynu bitowego AND logiczne (operator binarny &) z dwóch parametrów.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|Zwraca wartość logiczną bitowe uzupełnienie (operator ~) parametru.|
|[bit_or](../standard-library/functional-functions.md#bit_or)|Zwraca wartość logiczną logiczne OR (operator&#124;) z dwóch parametrów.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|Zwraca wartość iloczynu bitowego XOR logiczne (operator ^) z dwóch parametrów.|
|[cref](../standard-library/functional-functions.md#cref)|Konstruuje stałą `reference_wrapper` z argumentem.|
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|Generuje otoki prostemu wywołaniu.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|Pomocnik funkcje szablonu użytego do stworzenia funkcji adapterów obiektu dla funkcji składowych po zainicjowaniu wskaźnika argumentów.|
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|Funkcji pomocnika, która szablonu użytego do stworzenia funkcji adapterów obiektu dla funkcji składowych po zainicjowaniu z argumentami odwołania.|
|[not1](../standard-library/functional-functions.md#not1)|Zwraca uzupełnienie predykat.|
|[not2](../standard-library/functional-functions.md#not2)|Zwraca uzupełnienie predykat binarny.|
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|Funkcję pomocnika szablonu umożliwia jednoargumentowe konwersji i binarnego funkcja wskaźników, odpowiednio do funkcji potężnej jednoargumentowy i danych binarnych.|
|[ref](../standard-library/functional-functions.md#ref)|Konstruuje `reference_wrapper` z argumentem.|
|[swap](../standard-library/functional-functions.md#swap)|Zamień dwa `function` obiektów.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[binary_function —](../standard-library/binary-function-struct.md)|Pusta klasa podstawowa definiująca typy, które mogą być dziedziczone przez klasy pochodnej, który dostarcza obiekt funkcji binarnego.|
|[dzieli](../standard-library/divides-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacji arytmetycznej dzielenia elementów typu określoną wartość.|
|[equal_to](../standard-library/equal-to-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość określonego typu jest taki sam, z inną wartością tego typu.|
|[większa](../standard-library/greater-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest większa niż wartość innego typu.|
|[greater_equal](../standard-library/greater-equal-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest większy lub równy z inną wartością tego typu.|
|[less](../standard-library/less-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest mniejsza niż wartość innego typu.|
|[less_equal](../standard-library/less-equal-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest mniejsze niż lub równe z inną wartością tego typu.|
|[logical_and](../standard-library/logical-and-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacje logiczne połączeniu elementów typu określoną wartość i testów prawdziwość lub falsity wyniku.|
|[logical_not](../standard-library/logical-not-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacje logiczne negacji elementów typu określoną wartość i testów prawdziwość lub falsity wyniku.|
|[logical_or](../standard-library/logical-or-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacje logiczne rozłączenia elementów typu określoną wartość i testów prawdziwość lub falsity wyniku.|
|[znak minus](../standard-library/minus-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacji arytmetycznej odejmowania elementów typu określoną wartość.|
|[modulo](../standard-library/modulus-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje arytmetyczne operacji modulo elementów typu określoną wartość.|
|[Mnoży](../standard-library/multiplies-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje operacji arytmetycznej mnożenia elementów typu określoną wartość.|
|[negate](../standard-library/negate-struct.md)|Klasa oferuje obiektu wstępnie zdefiniowana funkcja, która zwraca ujemne wartości element.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie nie jest równa z inną wartością tego typu.|
|[znak plus](../standard-library/plus-struct.md)|Klasa zawiera obiekt wstępnie zdefiniowana funkcja, która wykonuje arytmetyczne operacji dodawania elementów typu określoną wartość.|
|[unary_function —](../standard-library/unary-function-struct.md)|Pusta klasa podstawowa definiująca typy, które mogą być dziedziczone przez klasy pochodnej, który dostarcza obiekt funkcji jednoargumentowy.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[_1.._M](../standard-library/1-object.md)|Symbole zastępcze dla wymiennych argumentów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](../standard-library/functional-operators.md#op_eq_eq)|Nie zezwala na porównanie równości obiektów możliwy do wywołania.|
|[operator!=](../standard-library/functional-operators.md#op_neq)|Nie zezwala na porównanie nierówności wywoływalnej obiektów.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
