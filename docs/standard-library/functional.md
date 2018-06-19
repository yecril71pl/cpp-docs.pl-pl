---
title: '&lt;funkcjonalności&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
dev_langs:
- C++
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1cf7d03b9c34f6be15fc947206e8d14ec04c991
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848014"
---
# <a name="ltfunctionalgt"></a>&lt;funkcjonalności&gt;

Definiuje funkcje standardowej biblioteki C++, które Zdefiniuj *funkcji obiektów*— znanej także jako funktorów — i ich obiektów wiążących. Obiekt funkcji jest obiektem typu, który definiuje `operator()`. Obiekt funkcji może być wskaźnik funkcji, ale więcej zwykle obiekt jest używany do przechowywania dodatkowe informacje, które mogą uzyskiwać podczas wywołania funkcji.

## <a name="syntax"></a>Składnia

```cpp
#include <functional>
```

## <a name="remarks"></a>Uwagi

Algorytmy wymagają dwa typy obiektów funkcji: jednoargumentowy a danych binarnych. Jednoargumentowy obiekty funkcji wymaga jednego argumentu i obiekty binarne funkcji wymaga dwóch argumentów. Obiekt funkcji i wskaźniki funkcji mogą być przekazywane jako predykat algorytm, ale funkcja obiekty są również dostosowywalne i zwiększyć zakres, elastyczność i wydajność standardowa biblioteka C++. Jeśli na przykład wartość potrzebne może być powiązane z funkcją przed przesłaniem do algorytmu, następnie wskaźnik funkcji nie można użyć. Funkcja adapterów konwertowanie obiekty dostosowywalne funkcji, które mogą zostać powiązane do wartości wskaźników funkcji. Nagłówek \<funkcjonalności > zawiera także adapterów funkcja elementu członkowskiego, umożliwiających funkcji do wywołania jako obiekty dostosowywalne funkcji elementu członkowskiego. Funkcje są pasujący, jeśli mają deklaracji typu zagnieżdżonego określenie ich argumentu i zwracanych typów. C++ Standard wymaga wykonanie tego zdolności adaptacyjnych przez wszystkie klasy obiektu standardowe, dziedziczą z klasy podstawowej unary_function lub binary_function —. Obiekty funkcji i ich adapterów umożliwiają standardowa biblioteka C++ do uaktualnienia istniejącej aplikacji i pomóc zintegrować biblioteki środowiska programowania C++.

Implementacja Visual C++ obiekty funkcji w \<funkcjonalności > zawiera *funktorów przezroczysty operator*, specjalizacje standard, które są działania obiektów i nie mają żadnych parametrów szablonu i Wykonaj doskonałego przekazywania dalej argumentów funkcji i doskonałe zwrot wyników. Ta funkcja jest częścią specyfikacji języka C ++ 14 standardowe projekt. Te specjalizacji szablonu nie wymagają Określ typy argumentów, uruchamiając arytmetyczne, porównanie logiczne i funktorów z bitowego operatora. Przeciążenia arytmetyczne, porównanie logiczne lub operatory bitowe własnych typów lub heterogenicznych kombinacji typów i użycie funktorów przezroczysty operatora jako argumenty funkcji. Na przykład jeśli z danym typem *Mojtyp* implementuje `operator<`, można wywołać `sort(my_collection.begin(), my_collection.end(), less<>())` zamiast jawne określenie typu `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.

## <a name="c11c14-implementation"></a>C ++ 11 / C ++ 14 implementacji

W implementacji Visual C++, C ++ 11 / C ++ 14 dodano następujące funkcje:

- A *sygnatury wywołania* jest nazwą typu zwracanego następuje ujętego w nawiasy listy rozdzielanej przecinkami zero lub więcej typów argumentu.

- A *można wywołać typu* jest wskaźnikiem do funkcji, wskaźnika do funkcji członkowskiej, wskaźnik do elementu członkowskiego danych lub typu klasy, w których obiekty może występować bezpośrednio z lewej strony operator wywołania funkcji.

- A *można wywołać obiektu* jest można wywołać typu obiektu.

- A *typ otoki* jest typem, który zawiera można wywołać obiektu i obsługuje operację wywołania, który przesyła dalej do tego obiektu.

- A *wywołanie otoką* jest obiektem typu otoki wywołania.

- A *obiektu docelowego* jest obiektem można wywołać w posiadaniu obiektu połączenia.

Pseudo-funkcja `INVOKE(f, t1, t2, ..., tN)` oznacza, że jedną z następujących czynności:

- `(t1.*f)(t2, ..., tN)` gdy `f` wskaźnika do funkcji członkowskiej klasy `T` i `t1` jest obiektem typu `T` lub odwołanie do obiektu typu `T` lub odwołanie do obiektu typu pochodzącego od `T`.

- `((*t1).*f)(t2, ..., tN)` gdy `f` wskaźnika do funkcji członkowskiej klasy `T` i `t1` nie jest jednym z typów opisanych w poprzedniej pozycji.

- `t1.*f` Gdy N == 1 i `f` wskaźnik do elementu członkowskiego danych klasy `T` i `t1` jest obiektem typu `T` lub odwołanie do obiektu typu `T` lub odwołanie do obiektu typu pochodzącego od `T`.

- `(*t1).*f` Jeśli N == 1 i `f` wskaźnik do elementu członkowskiego danych klasy `T` i `t1` nie jest jednym z typów opisanych w poprzedniej pozycji.

- `f(t1, t2, ..., tN)` we wszystkich innych przypadkach.

Pseudo-funkcja `INVOKE(f, t1, t2, ..., tN, R)` oznacza `INVOKE(f, t1, t2, ..., tN)` niejawnie przekonwertowana na `R`.

Jeśli wywołanie otoką ma *typu wyniku słabe*, jego typ elementu członkowskiego typu `result_type` jest oparty na typie `T` obiektu docelowego otoki w następujący sposób:

- Jeśli `T` jest wskaźnikiem do funkcji, `result_type` jest synonimem zwracany typ `T`.

- Jeśli `T` wskaźnika do funkcji członkowskiej `result_type` jest synonimem zwracany typ `T`.

- Jeśli `T` jest typ klasy, która ma typ elementu członkowskiego `result_type`, następnie `result_type` jest synonimem `T::result_type`.

- W przeciwnym razie nie ma żadnego członka `result_type`.

Co wywołanie otoką ma Konstruktor przenoszący oraz Konstruktor kopiujący. A *proste wywołanie otoką* jest otoką wywołania przypisaniem operatora i którego konstruktora kopiującego, Konstruktor przenoszenia i operatora przypisania nie zgłaszają wyjątki. A *przekazywania wywołanie otoką* jest otoki wywołania, który można wywołać za pomocą listy argumentów dowolnego i dostarcza argumenty opakowana można wywołać obiekt jako odwołania. Wszystkie argumenty wartościowania prawostronnego są dostarczane jako odwołania do r-wartości i argumenty l-wartość są dostarczane jako l-wartością odwołania.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|Klasa, która opisuje wyjątek, aby wskazać, że wywołanie `operator()` na [funkcja](../standard-library/function-class.md) obiektu nie powiodło się, ponieważ obiekt był pusty.|
|[binary_negate](../standard-library/binary-negate-class.md)|Klasy szablonów zapewnianie funkcji członkowskiej, która Negacja zwracana wartość określona funkcja binarnej.|
|[binder1st](../standard-library/binder1st-class.md)|Klasy szablonów dostarczanie konstruktora, który konwertuje obiektu binarnego funkcja na obiekt funkcja jednoargumentowy przez powiązanie pierwszy argument funkcji binarnego do określonej wartości.|
|[binder2nd —](../standard-library/binder2nd-class.md)|Klasy szablonów dostarczanie konstruktora, który konwertuje obiektu binarnego funkcja na obiekt funkcja jednoargumentowy przez powiązanie drugi argument funkcji binarnego do określonej wartości.|
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Klasa karty, która umożliwia stałej funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.|
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Klasa karty, która umożliwia stałej funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem wskaźnika.|
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Klasa karty, która umożliwia stałej funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem odwołania.|
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Klasa karty, która umożliwia stałej funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem wskaźnika.|
|[Funkcja](../standard-library/function-class.md)|Klasa, która opakowuje można wywołać obiektu.|
|[Wyznaczania wartości skrótu](../standard-library/hash-class.md)|Klasa, która oblicza wartość skrótu dla wartości.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Klasy, który umożliwia sprawdzenie, czy określony typ jest generowany przez wywołanie metody `bind`.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|Klasa, która testów, jeśli symbol zastępczy jest określonego typu.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem odwołania.|
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która nie przyjmuje żadnych argumentów do wywołania jako obiekt funkcja jednoargumentowy po zainicjowaniu z argumentem wskaźnika.|
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem odwołania.|
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Klasa karty, który umożliwia **non_const** funkcji członkowskiej, która pobiera jeden argument ma być wywoływana jako obiektu binarnego funkcja po zainicjowaniu z argumentem wskaźnika.|
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Konwertuje wskaźnika funkcji binarne dostosowywalne funkcja binarnej.|
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Konwertuje wskaźnik funkcji jednoargumentowy funkcja dostosowywalne jednoargumentowy.|
|[reference_wrapper —](../standard-library/reference-wrapper-class.md)|Klasa, która opakowuje odwołanie.|
|[unary_negate](../standard-library/unary-negate-class.md)|Zapewnianie funkcji członkowskiej, która Negacja wartość zwracana funkcji jednoargumentowy określonej klasy szablonów.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[BIND](../standard-library/functional-functions.md#bind)|Wiąże argumentów można wywołać obiektu.|
|[bind1st](../standard-library/functional-functions.md#bind1st)|Funkcja szablonu pomocnika, która tworzy adaptera, aby przekonwertować obiektu binarnego funkcja obiektem funkcji jednoargumentowy przez powiązanie pierwszy argument funkcji binarnego do określonej wartości.|
|[bind2nd](../standard-library/functional-functions.md#bind2nd)|Funkcja szablonu pomocnika, która tworzy adaptera, aby przekonwertować obiektu binarnego funkcja obiektem funkcji jednoargumentowy przez powiązanie drugi argument funkcji binarnego do określonej wartości.|
|[bit_and](../standard-library/functional-functions.md#bit_and)|Zwraca wartość logiczną logiczny AND (operator binarny &) z dwóch parametrów.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|Zwraca dopełnienia bitowego logiczne (operator ~) parametru.|
|[bit_or](../standard-library/functional-functions.md#bit_or)|Zwraca wartość logiczną lub logiczne (operator&#124;) z dwóch parametrów.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|Zwraca iloczynu bitowego XOR logiczne (operator ^) z dwóch parametrów.|
|[cref](../standard-library/functional-functions.md#cref)|Konstrukcje typu const `reference_wrapper` z argumentem.|
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|Generuje otoki proste wywołania.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|Funkcje pomocy szablonu, użyty do utworzenia karty obiektu funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami wskaźnika.|
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|Funkcja szablonu pomocnika używany do budowy adapterów obiektu funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami odwołania.|
|[not1](../standard-library/functional-functions.md#not1)|Zwraca dopełnienia predykatu jednoargumentowy.|
|[not2](../standard-library/functional-functions.md#not2)|Zwraca dopełnienia predykatu binarnego.|
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|Funkcji szablonu pomocnika używany do jednoargumentowy convert i funkcja binarnej wskaźników, odpowiednio do funkcji dostosowywalne jednoargumentowy i danych binarnych.|
|[ref](../standard-library/functional-functions.md#ref)|Tworzy `reference_wrapper` z argumentem.|
|[swap](../standard-library/functional-functions.md#swap)|Zamienia dwa `function` obiektów.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[binary_function —](../standard-library/binary-function-struct.md)|Pusta klasa podstawowa definiujący typy, które mogą być dziedziczone przez klasy pochodnej, która zawiera obiekt funkcja binarnej.|
|[dzieli](../standard-library/divides-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który wykonuje operacji arytmetycznej podziału na elementy typu określonej wartości.|
|[equal_to](../standard-library/equal-to-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie są takie same z inną wartością tego typu.|
|[większa](../standard-library/greater-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest większa niż wartość inna tego typu.|
|[greater_equal](../standard-library/greater-equal-struct.md)|Predykat binarne sprawdza, czy wartość o określonym typie jest większa niż lub równa wartości innego typu.|
|[mniej](../standard-library/less-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest mniejsza niż wartość inna tego typu.|
|[less_equal](../standard-library/less-equal-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość o określonym typie jest mniejsza lub równa wartości innego typu.|
|[logical_and](../standard-library/logical-and-struct.md)|Ta klasa dostarcza obiektem wstępnie zdefiniowanych funkcji, która wykonuje operacje logiczne połączeniu na elementy typu określoną wartość, jak i testy dla prawdy lub falsity wyniku.|
|[logical_not](../standard-library/logical-not-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który wykonuje operacje logiczne negację na elementy typu określoną wartość, jak i testy dla prawdy lub falsity wyniku.|
|[logical_or](../standard-library/logical-or-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który wykonuje operacje logiczne rozłączenia na elementy typu określoną wartość, jak i testy dla prawdy lub falsity wyniku.|
|[minus](../standard-library/minus-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który wykonuje działania arytmetyczne odejmowania na elementy typu określonej wartości.|
|[modulo](../standard-library/modulus-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który wykonuje działania arytmetycznego modulo w elementach typu określonej wartości.|
|[Mnoży](../standard-library/multiplies-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który dokonuje operacji arytmetycznej mnożenia elementów typu określonej wartości.|
|[negate](../standard-library/negate-struct.md)|Ta klasa dostarcza obiektu wstępnie zdefiniowanych funkcji zwracającej ujemne wartości elementu.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|Predykat binarny, który umożliwia sprawdzenie, czy wartość określonego typu nie jest równa z inną wartością tego typu.|
|[plus](../standard-library/plus-struct.md)|Ta klasa dostarcza obiekt wstępnie zdefiniowanych funkcji, który dokonuje operacji arytmetycznej dodawania elementów typu określonej wartości.|
|[unary_function](../standard-library/unary-function-struct.md)|Pusta klasa podstawowa definiujący typy, które mogą być dziedziczone przez klasy pochodnej, która zawiera obiekt funkcji jednoargumentowy.|

### <a name="objects"></a>Obiekty

|||
|-|-|
|[_1.._M](../standard-library/1-object.md)|Symbole zastępcze dla argumentów do zastąpienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](../standard-library/functional-operators.md#op_eq_eq)|Uniemożliwia porównania równości można wywołać obiektów.|
|[operator!=](../standard-library/functional-operators.md#op_neq)|Uniemożliwia porównania nierówności można wywołać obiektów.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
