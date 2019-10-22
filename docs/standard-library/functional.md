---
title: '&lt;functional &gt;'
ms.date: 02/21/2019
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
ms.openlocfilehash: 67b2ccf70b4d3045cecd13d9096875f77c4cde9a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689622"
---
# <a name="ltfunctionalgt"></a>&lt;functional &gt;

Definiuje C++ standardowe funkcje biblioteki, które ułatwiają konstruowanie *obiektów funkcji*, znanych również jako *funktory*, oraz ich powiązań. Obiekt funkcyjny jest obiektem typu, który definiuje `operator()`. Obiekt funkcji może być wskaźnikiem funkcji, ale zazwyczaj jest to obiekt używany do przechowywania dodatkowych informacji, do których można uzyskać dostęp podczas wywołania funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<functional >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Algorytmy wymagają dwóch typów obiektów funkcyjnych: *jednoargumentowych* i *binarnych*. Jednoargumentowe obiekty funkcyjne wymagają jednego argumentu, a obiekty funkcji binarnych wymagają dwóch argumentów. Obiekt funkcyjny i wskaźniki funkcji mogą być przesyłane jako predykat do algorytmu, ale obiekty funkcji są również dostosowywane i zwiększają zakres, elastyczność i wydajność biblioteki C++ standardowej. Jeśli na przykład wartość wymagana do powiązania z funkcją przed przekazaniem do algorytmu, nie można użyć wskaźnika funkcji. Adaptery funkcji konwertują wskaźniki funkcji do dostosowywalnych obiektów funkcji, które mogą być powiązane z wartością. Nagłówek \<functional > również zawiera adaptery funkcji Członkowskich, które umożliwiają wywoływanie funkcji Członkowskich jako dostosowywalnych obiektów funkcji. Funkcje są dostosowywane, jeśli mają deklaracje typu zagnieżdżonego określające ich argumenty i typy zwracane. Obiekty funkcyjne i ich adaptery umożliwiają C++ uaktualnianie istniejących aplikacji i integrację biblioteki ze środowiskiem C++ programowania.

Implementacja obiektów funkcji w \<functional > zawiera *przezroczyste operatory funktory*. są to specjalizacje standardowych obiektów funkcyjnych i nie pobierają parametrów szablonu i realizują doskonałe przekazywanie argumentów funkcji i idealny zwrot wyniku. Te specjalizacje szablonów nie wymagają określenia typów argumentów podczas wywoływania arytmetycznego, porównania, logicznego i bitowego operatora funktory. Operatory arytmetyczne, porównania, logiczne lub bitowe można przeciążać dla własnych typów lub dla niejednorodnych kombinacji typów, a następnie używać przezroczystego operatora funktory jako argumenty funkcji. Na przykład, jeśli typ *MyType* implementuje `operator<`, można wywołać `sort(my_collection.begin(), my_collection.end(), less<>())` zamiast jawnie określić typ `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.

W językach C++ 11, C++ 14 i C++ 17 dodano następujące funkcje:

- *Sygnatura wywołania* to nazwa typu zwracanego, po którym następuje rozdzielona przecinkami lista z zerem lub większą liczbą typów argumentów.

- Możliwy do wywołania *Typ* jest wskaźnikiem do funkcji, wskaźnikiem do funkcji składowej, wskaźnikiem do danych elementu członkowskiego lub typem klasy, której obiekty mogą pojawić się bezpośrednio po lewej stronie operatora wywołania funkcji.

- Wywoływany *obiekt* jest obiektem typu, który jest możliwy do przetrwania.

- *Typ otoki wywołania* to typ, który posiada wywoływany obiekt i obsługuje operację wywołania, która przekazuje do tego obiektu.

- *Otoka wywołań* jest obiektem typu otoki wywołania.

- *Obiekt docelowy* jest obiektem możliwym do przetrzymywania przez obiekt otoki wywołania.

Pseudo funkcja `INVOKE(f, t1, t2, ..., tN)` oznacza jedną z następujących czynności:

- `(t1.*f)(t2, ..., tN)`, gdy `f` jest wskaźnikiem do funkcji składowej klasy `T` i `t1` jest obiektem typu `T` lub odwołaniem do obiektu typu `T` lub odwołaniem do obiektu typu pochodnego od `T`.

- `((*t1).*f)(t2, ..., tN)`, gdy `f` jest wskaźnikiem do funkcji składowej klasy `T` i `t1` nie jest jednym z typów opisanych w poprzednim elemencie.

- `t1.*f`, gdy N = = 1 i `f` jest wskaźnikiem do danych składowych klasy `T` i `t1` jest obiektem typu `T` lub odwołaniem do obiektu typu `T` lub odwołaniem do obiektu typu pochodnego z `T`.

- `(*t1).*f`, gdy N = = 1 i `f` jest wskaźnikiem do danych elementu członkowskiego klasy `T` i `t1` nie jest jednym z typów opisanych w poprzednim elemencie.

- `f(t1, t2, ..., tN)` we wszystkich innych przypadkach.

Pseudo funkcja `INVOKE(f, t1, t2, ..., tN, R)` oznacza `INVOKE(f, t1, t2, ..., tN)` niejawnie przekonwertowane na `R`.

Jeśli otoka wywołania ma *słaby typ wyniku*, typ jego typu elementu członkowskiego `result_type` jest oparty na typie `T` obiektu docelowego otoki w następujący sposób:

- Jeśli `T` jest wskaźnikiem do funkcji, `result_type` jest synonimem dla zwracanego typu `T`.

- Jeśli `T` jest wskaźnikiem do funkcji składowej, `result_type` jest synonimem dla zwracanego typu `T`.

- Jeśli `T` jest typem klasy, który ma `result_type` typu elementu członkowskiego, wówczas `result_type` jest synonimem dla `T::result_type`.

- W przeciwnym razie nie ma `result_type` członkowskich.

Każda otoka wywołania ma Konstruktor przenoszenia i Konstruktor kopiujący. *Prosta otoka wywołań* jest otoką wywołania, która ma operator przypisania i której Konstruktor kopiujący, Konstruktor przenoszenia i operator przypisania nie zgłasza wyjątków. *Otoka wywołań przekazywania* jest otoką wywołania, która może być wywoływana przy użyciu arbitralnej listy argumentów i która dostarcza argumenty do zapakowanego wywołującego obiektu jako odwołania. Wszystkie argumenty rvalue są dostarczane jako odwołania rvalue, a argumenty lvalue są dostarczane jako odwołania lvalue.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|Klasa opisująca wyjątek zgłoszony w celu wskazania, że wywołanie `operator()` w obiekcie [funkcji](../standard-library/function-class.md) nie powiodło się, ponieważ obiekt był pusty.|
|[binary_negate](../standard-library/binary-negate-class.md)|Szablon klasy dostarczający funkcję członkowską, która wyklucza wartość zwracaną określonej funkcji binarnej.<br/> (Przestarzałe w języku C++ 17). |
|[binder1st —](../standard-library/binder1st-class.md)|Szablon klasy dostarczający Konstruktor, który konwertuje obiekt funkcji binarnej na jednoargumentowy obiekt funkcji przez powiązanie pierwszego argumentu funkcji Binary z określoną wartością.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[binder2nd —](../standard-library/binder2nd-class.md)|Szablon klasy dostarczający Konstruktor, który konwertuje obiekt funkcji binarnej na jednoargumentowy obiekt funkcji przez powiązanie drugiego argumentu funkcji Binary z określoną wartością.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[boyer_moore_horspool_searcher](../standard-library/boyer-moore-horspool-searcher-class.md)||
|[boyer_moore_searcher](../standard-library/boyer-moore-searcher-class.md)||
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Klasa adaptera, która umożliwia stałej funkcji składowej, która nie przyjmuje argumentów, które mają być wywoływane jako jednoargumentowy obiekt funkcji po zainicjowaniu z argumentem Reference.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Klasa adaptera, która umożliwia stałej funkcji składowej, która nie przyjmuje argumentów, które mają być wywoływane jako jednoargumentowy obiekt funkcji, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Klasa adaptera, która umożliwia stałemu funkcji składowej, która przyjmuje pojedynczy argument jako obiekt funkcji binarnej po zainicjowaniu z argumentem Reference.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Klasa adaptera, która umożliwia stałemu funkcji składowej, która przyjmuje pojedynczy argument jako obiekt funkcji binarnej, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[default_searcher](../standard-library/default-searcher-class.md)||
|[funkcyjn](../standard-library/function-class.md)|Klasa, która otacza wywoływany obiekt.|
|[skrótu](../standard-library/hash-class.md)|Klasa, która oblicza kod skrótu dla wartości.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|Klasa, która sprawdza, czy określony typ jest generowany przez wywołanie `bind`.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|Klasa, która sprawdza, czy określony typ jest symbolem zastępczym.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Klasa adaptera, która umożliwia `non_const` funkcji członkowskiej, która nie przyjmuje argumentów do wywołania jednoargumentowego obiektu, gdy zostanie zainicjowany z argumentem odwołania.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Klasa adaptera, która umożliwia `non_const` funkcji członkowskiej, która nie przyjmuje argumentów do wywołania jednoargumentowego obiektu funkcyjnego, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Klasa adaptera, która umożliwia `non_const` funkcję członkowską, która przyjmuje jeden argument jako obiekt funkcji binarnej po zainicjowaniu z argumentem odwołania.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Klasa adaptera, która umożliwia `non_const` funkcję członkowską, która przyjmuje jeden argument jako obiekt funkcji binarnej, gdy zostanie zainicjowany przy użyciu argumentu wskaźnika.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Konwertuje wskaźnik funkcji binarnej na dostosowywalną funkcję binarną.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Konwertuje wskaźnik jednoargumentowy funkcji na dostosowywalną funkcję jednoargumentową.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|Klasa, która otacza odwołanie.|
|[unary_negate](../standard-library/unary-negate-class.md)|Szablon klasy dostarczający funkcję członkowską, która wyklucza wartość zwracaną przez określoną funkcję jednoargumentową.<br/> (Przestarzałe w języku C++ 17).  |

### <a name="functions"></a>Funkcje

|||
|-|-|
|[węglowodor](../standard-library/functional-functions.md#bind)|Tworzy powiązania argumentów z wywoływanym obiektem.|
|[bind1st —](../standard-library/functional-functions.md#bind1st)|Funkcja szablonu pomocnika, która tworzy adapter do konwertowania obiektu funkcji binarnej na jednoargumentowy obiekt funkcji przez powiązanie pierwszego argumentu funkcji Binary z określoną wartością.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[bind2nd —](../standard-library/functional-functions.md#bind2nd)|Funkcja szablonu pomocnika, która tworzy adapter do przekonwertowania obiektu funkcji binarnej na jednoargumentowy obiekt funkcji przez powiązanie drugiego argumentu funkcji Binary z określoną wartością.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[bit_and](../standard-library/functional-functions.md#bit_and)|Zwraca koniunkcję logiczną i (operator binarny &) dwóch parametrów.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|Zwraca bitowe dopełnienie logiczne (operator ~) parametru.<br/> (Dodano w języku C++ 14). |
|[bit_or](../standard-library/functional-functions.md#bit_or)|Zwraca bitowe wartości logiczne OR (operator&#124;) dwóch parametrów.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|Zwraca bitowe logiczne XOR (operator ^) dwóch parametrów.|
|[cref](../standard-library/functional-functions.md#cref)|Tworzy element const `reference_wrapper` z argumentu.|
|[wywołuje](../standard-library/functional-functions.md#invoke)||
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|Generuje prosty otokę wywołania.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|Funkcje szablonu pomocnika służące do konstruowania adapterów obiektów funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami wskaźnika.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|Funkcja szablonu pomocnika służąca do konstruowania adapterów obiektów funkcji dla funkcji Członkowskich po zainicjowaniu z argumentami odwołania.|
|[not1 —](../standard-library/functional-functions.md#not1)|Zwraca uzupełnienie predykatu jednoargumentowego.<br/> (Przestarzałe w języku C++ 17). |
|[not2 —](../standard-library/functional-functions.md#not2)|Zwraca uzupełnienie predykatu binarnego.<br/> (Przestarzałe w języku C++ 17). |
|[not_fn](../standard-library/functional-functions.md#not_fn)|Zwraca uzupełnienie wyniku obiektu funkcji.<br/> (Dodano w języku C++ 17) |
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|Funkcja szablonu pomocnika służąca do konwersji jednoargumentowych i binarnych wskaźników funkcji, odpowiednio, do funkcji, które można dostosowywać jednoargumentowo.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[ref](../standard-library/functional-functions.md#ref)|Konstruuje `reference_wrapper` z argumentu.|
|[wymiany](../standard-library/functional-functions.md#swap)|Zamienia dwa obiekty `function`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[binary_function](../standard-library/binary-function-struct.md)|Pusta Klasa bazowa, która definiuje typy, które mogą być dziedziczone przez klasę pochodną, która udostępnia obiekt funkcji binarnej.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |
|[dzieli](../standard-library/divides-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który wykonuje operację arytmetyczną dzielenia na elementy o określonym typie wartości.|
|[equal_to](../standard-library/equal-to-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu jest równa innej wartości tego typu.|
|[mniejszą](../standard-library/greater-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu jest większa niż inna wartość tego typu.|
|[greater_equal](../standard-library/greater-equal-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu jest większa lub równa innej wartości tego typu.|
|[wcześniejsz](../standard-library/less-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu jest mniejsza niż inna wartość tego typu.|
|[less_equal](../standard-library/less-equal-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu jest mniejsza lub równa innej wartości tego typu.|
|[logical_and](../standard-library/logical-and-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który wykonuje logiczną operację połączenia dla elementów określonego typu wartości i testów dla prawdy lub falsity wyniku.|
|[logical_not](../standard-library/logical-not-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który wykonuje logiczną operację negacji dla elementów określonego typu wartości i testów dla prawdy lub falsity wyniku.|
|[logical_or](../standard-library/logical-or-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który wykonuje logiczną operację rozłączenia dla elementów określonego typu wartości i testów dla prawdy lub falsity wyniku.|
|[przed](../standard-library/minus-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje arytmetyczne odejmowania dla elementów o określonym typie wartości.|
|[Moduł](../standard-library/modulus-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt funkcji, który wykonuje operacje arytmetyczne modułu dla elementów o określonym typie wartości.|
|[Mnoży](../standard-library/multiplies-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który wykonuje operacje arytmetyczne mnożenia dla elementów o określonym typie wartości.|
|[Negate](../standard-library/negate-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt Function, który zwraca wartość ujemną wartości elementu.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|Predykat binarny, który sprawdza, czy wartość określonego typu nie jest równa innej wartości tego typu.|
|[dłużon](../standard-library/plus-struct.md)|Klasa zawiera wstępnie zdefiniowany obiekt funkcji, który wykonuje operację arytmetyczną dodawania dla elementów o określonym typie wartości.|
|[unary_function](../standard-library/unary-function-struct.md)|Pusta Klasa bazowa, która definiuje typy, które mogą być dziedziczone przez klasę pochodną, która dostarcza jednoargumentowy obiekt funkcji.<br/> (Przestarzałe w języku C++ 11, usunięte w języku C++ 17). |

### <a name="objects"></a>Obiekty

|||
|-|-|
|[_1.._M](../standard-library/1-object.md)|Symbole zastępcze dla argumentów do przemieszczenia.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator = =](../standard-library/functional-operators.md#op_eq_eq)|Nie zezwala na porównanie wartości wywoływanych obiektów.|
|[operator!=](../standard-library/functional-operators.md#op_neq)|Nie zezwala na porównanie wywoływanych obiektów.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
