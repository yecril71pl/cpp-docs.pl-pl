---
title: funkcje&gt; &lt;narzędzi
ms.date: 11/04/2016
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854871"
---
# <a name="ltutilitygt-functions"></a>funkcje&gt; &lt;narzędzi

## <a name="asconst"></a>as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca *T*.

## <a name="declval"></a>declval —

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a>zamian

**(C++ 14)** Przypisuje nową wartość do obiektu i zwraca jego starą wartość.

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

*val*\
Obiekt, który otrzyma wartość new_val.

*new_val*\
Obiekt, którego wartość jest kopiowana lub przenoszona do wartości Val.

### <a name="remarks"></a>Uwagi

W przypadku typów złożonych, `exchange` zapobiega kopiowaniu starej wartości, gdy jest dostępny konstruktor przenoszenia, zapobiega kopiowaniu nowej wartości, jeśli jest obiektem tymczasowym lub jest przenoszona, i akceptuje dowolny typ jako nową wartość przy użyciu dowolnego dostępnego operatora konwersji. Funkcja wymiany różni się od [std:: swap](../standard-library/algorithm-functions.md#swap) w tym, że lewy argument nie jest przenoszony ani kopiowany do prawego argumentu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `exchange`. W świecie rzeczywistym `exchange` jest najbardziej przydatna w przypadku dużych obiektów, które są kosztowne do kopiowania:

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a>prześlą

Warunkowo rzutuje swój argument do odwołania rvalue, jeśli argument to rvalue lub odwołanie rvalue. Spowoduje to przywrócenie cechy rvalue argumentu do funkcji przekazywania do przodu, aby obsłużyć doskonałe przekazywanie do przodu.

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ wartości przekazaną w *ARG*, która może być różna od typu *ARG*. Zwykle określony przez argument szablonu funkcji przekazywania do przodu.

\ *ARG*
Argument do rzutowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie rvalue do *argumentu ARG* , jeśli wartość przeniesiona w *ARG* była pierwotnie rvalue lub odwołaniem do rvalue; w przeciwnym razie zwraca *ARG* bez modyfikowania jego typu.

### <a name="remarks"></a>Uwagi

Musisz określić jawny argument szablonu, aby wywołać `forward`.

`forward` nie przekazuje tego argumentu. Zamiast tego przez warunkowe rzutowanie argumentu na odwołanie rvalue, jeśli było pierwotnie rvalue lub rvalue, `forward` umożliwia kompilatorowi przeprowadzenie rozpoznawania przeciążenia przy użyciu informacji o typie oryginalnym przekazanego argumentu. Pozorny typ argumentu funkcji przekazywania może być inny niż jego oryginalny typ — na przykład gdy rvalue jest używany jako argument funkcji i jest powiązany z nazwą parametru; posiadanie nazwy sprawia, że jest to lvalue, z każdą wartością rzeczywiście istnieje jako rvalue — `forward` przywraca rvalue-stałość argumentu.

Przywrócenie pierwotnej wartości argumentu rvalue-stałość w celu przeprowadzenia rozpoznawania przeciążenia jest znane jako *doskonałe przekazywanie dalej*. Doskonałe przekazywanie do przodu umożliwia funkcji szablonu zaakceptowanie argumentu któregokolwiek typu odwołania i przywrócenie jego cechy rvalue, gdy jest to niezbędne do poprawnego rozwiązania przeciążenia. Za pomocą doskonałego przekazywania do przodu można zachować semantykę przenoszenia dla rvalue i uniknąć konieczności zapewnienia przeciążeń dla funkcji, które różnią się tylko pod względem typu odwołania ich argumentów.

## <a name="from_chars"></a>from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a>Pobierz

Pobiera element z obiektu `pair` według pozycji indeksu lub według typu.

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&
    get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr const tuple_element_t<Index, pair<T1, T2>>&
    get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&&
    get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>Parametry

*Indeks*\
Indeks (0) wybranego elementu.

\ *T1*
Typ pierwszego pary elementu.

\ *T2*
Typ drugiego elementu pary.

*\ żądania* ściągnięcia
Para do wyboru.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje szablonu zwracają odwołanie do elementu `pair` argument.

W przypadku przeciążeń indeksowanych, jeśli wartość *indeksu* jest równa 0, funkcje zwracają `pr.first` i jeśli wartość *indeksu* wynosi 1, zwracane są `pr.second`funkcje. Typ `RI` jest typem zwracanego elementu.

Dla przeciążeń, które nie mają parametru index, element do zwrócenia jest określany przez argument typu. Wywołanie `get<T>(Tuple)` spowoduje błąd kompilatora *, jeśli żądanie* ściągnięcia zawiera więcej lub mniej niż jeden element typu t.

### <a name="example"></a>Przykład

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a>index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a>index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a>make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a>make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a>make_pair

Funkcja szablonu, której można użyć do konstruowania obiektów typu `pair`, w których typy składników są automatycznie wybierane na podstawie typów danych, które są przesyłane jako parametry.

```cpp
template <class T, class U>
    pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>Parametry

*Val1*\
Wartość, która inicjuje pierwszy element `pair`.

*Val2*\
Wartość, która inicjuje drugi element `pair`.

### <a name="return-value"></a>Wartość zwracana

Obiekt pary, który jest zbudowany: `pair`<`T`,`U`> (`Val1`, `Val2`).

### <a name="remarks"></a>Uwagi

`make_pair` Konwertuje obiekt typu [Reference_wrapper klasy](../standard-library/reference-wrapper-class.md) na typy referencyjne i konwertuje zanikają tablicę i funkcje na wskaźniki.

W zwróconym obiekcie `pair` `T` jest określony w następujący sposób:

- Jeśli typ danych wejściowych `T` jest `reference_wrapper<X>`, zwracany typ `T` jest `X&`.

- W przeciwnym razie zwrócony typ `T` jest `decay<T>::type`. Jeśli [Klasa zanikania](../standard-library/decay-class.md) nie jest obsługiwana, zwracany typ `T` jest taka sama jak typ wejściowy `T`.

Zwrócony typ `U` jest w podobny sposób określany na podstawie typu wejściowego `U`.

Jedną z zalet `make_pair` jest to, że typy obiektów, które są przechowywane, są określane automatycznie przez kompilator i nie muszą być jawnie określone. Nie używaj jawnych argumentów szablonu, takich jak `make_pair<int, int>(1, 2)`, gdy używasz `make_pair`, ponieważ jest on pełny i dodaje złożone problemy referencyjne rvalue, które mogą spowodować błąd kompilacji. W tym przykładzie poprawna składnia będzie `make_pair(1, 2)`

Funkcja pomocnika `make_pair` umożliwia również przekazywanie dwóch wartości do funkcji, która wymaga pary jako parametru wejściowego.

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem dotyczącym sposobu używania funkcji pomocnika `make_pair` zadeklarować i zainicjować parę, zobacz [parowanie struktury](../standard-library/pair-structure.md).

## <a name="move"></a>Przenieś

Bezwarunkowo rzutuje swój argument na odwołanie rvalue, a tym samym sygnalizuje, że może być przeniesione, jeśli jego typ umożliwia przenoszenie.

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ wywnioskowany z typu argumentu, który przeszedł w *ARG*, wraz z regułami zwijania odwołania.

\ *ARG*
Argument do rzutowania. Mimo że typ *argumentu* jest określony jako odwołanie rvalue, `move` również akceptuje argumenty lvalue, ponieważ odwołania lvalue mogą być powiązane z odwołaniami do rvalue.

### <a name="return-value"></a>Wartość zwracana

`Arg` jako odwołanie rvalue, niezależnie od tego, czy typ jest typem referencyjnym.

### <a name="remarks"></a>Uwagi

*Typ* argumentu szablonu nie jest przeznaczony do określenia jawnie, ale do wywnioskowania z typu wartości przekazaną w argumencie *ARG*. Typ *typu* jest dostosowywany w oparciu o reguły zwijane odwołania.

`move` nie przenosi tego argumentu. Zamiast tego przez bezwarunkowo rzutowanie argumentu, który może być lvalue — do odwołania rvalue, umożliwia kompilatorowi przeniesienie, a nie kopiowanie, wartość przekazaną w argumencie *ARG* , jeśli jej typ jest włączony. Jeśli typ nie jest włączony do przenoszenia, jest kopiowany.

Jeśli wartość przeniesiona w *ARG* to lvalue — to znaczy, że ma nazwę lub jego adres może zostać pobrany — jest on unieważniony po przeniesieniu. Nie należy odwoływać się do wartości przekazaną w *ARG* o nazwę lub adres po przeniesieniu.

## <a name="moveif"></a>move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a>wymiany

Wymienia elementy dwóch obiektów struktury typu lub [pary](../standard-library/pair-structure.md) .

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu lub `pair`.

*prawa*\
Obiekt typu lub `pair`.

### <a name="remarks"></a>Uwagi

Jedną z zalet `swap` jest to, że typy obiektów, które są przechowywane, są określane automatycznie przez kompilator i nie muszą być jawnie określone. Nie używaj jawnych argumentów szablonu, takich jak `swap<int, int>(1, 2)`, gdy używasz `swap`, ponieważ jest on pełny i dodaje złożone problemy referencyjne rvalue, które mogą spowodować błąd kompilacji.

## <a name="to_chars"></a>to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value); 
to_chars_result to_chars(char* first, char* last, double value); 
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>Uwagi

Konwertuje wartość na ciąg znaków, wypełniając zakres `[first, last)`, gdzie `[first, last)` musi być prawidłowym zakresem.
