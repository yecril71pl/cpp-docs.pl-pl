---
title: '&lt;Narzędzie&gt; funkcji'
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
ms.openlocfilehash: 7a061ede19c5c4c181b5fea912b9c6212c583267
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543913"
---
# <a name="ltutilitygt-functions"></a>&lt;Narzędzie&gt; funkcji

||||
|-|-|-|
|[exchange](#exchange)|[do przodu](#forward)|[Get — funkcja &lt;narzędzia&gt;](#get)|
|[make_pair](#make_pair)|[Przenieś](#move)|[swap](#swap)|

## <a name="exchange"></a>  Program Exchange

**(C ++ 14)**  Przypisuje nową wartość do obiektu i zwraca starą wartość.

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Obiekt, który otrzyma wartość new_val.

*new_val*<br/>
Obiekt, którego wartość jest kopiowany lub przenoszony do val.

### <a name="remarks"></a>Uwagi

W przypadku typów złożonych `exchange` zapobiega kopiowaniu starej wartości, gdy Konstruktor przenoszenia, jest dostępna, zapobiega kopiowaniu nowej wartości, jeśli jest obiektem tymczasowym lub są przenoszone i akceptuje dowolny typ jako nową wartość, przy użyciu wszelkich dostępnych operatorów konwersji przypisania. Funkcja exchange różni się od [std::swap](../standard-library/algorithm-functions.md#swap) w tym argument po lewej stronie nie jest przenoszone lub kopiowane do argumentu po prawej stronie.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `exchange`. W świecie rzeczywistym `exchange` jest najbardziej przydatna w przypadku dużych obiektów, które są kosztowne do skopiowania:

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

## <a name="forward"></a>  do przodu

Warunkowo rzutuje swój argument do odwołania rvalue, jeśli argument to rvalue lub odwołanie rvalue. Spowoduje to przywrócenie cechy rvalue argumentu do funkcji przekazywania do przodu, aby obsłużyć doskonałe przekazywanie do przodu.

```cpp
template <class Type>    // accepts lvalues
constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ wartości przekazanej w *Arg*, który może być inny niż typ *Arg*. Zwykle określony przez argument szablonu funkcji przekazywania do przodu.|
|*ARG*|Argument do rzutowania.|

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie rvalue do *Arg* Jeśli wartość przekazywana w *Arg* była pierwotnie rvalue lub odwołaniem rvalue; w przeciwnym razie zwraca *Arg* bez zmiany jego typu.

### <a name="remarks"></a>Uwagi

Musisz określić jawny argument szablonu do wywołania `forward`.

`forward` nie przekazuje swojego argumentu. Zamiast tego, przez warunkowe rzutowanie swojego argumentu na odwołanie rvalue, jeśli pierwotnie był on rvalue lub odwołaniem rvalue, `forward` umożliwia kompilatorowi wykonanie rozwiązania przeciążenia przy zachowaniu wiedzy o oryginalnym typie argumentu przekazywane. Jawny typ argumentu do funkcji przekazywania może być inny niż jego typ oryginalny — na przykład, kiedy rvalue jest używana jako argument do funkcji i jest powiązana z nazwą parametru; posiadanie nazwy sprawia, że lvalue, niezależnie od tego, czy wartość faktycznie istnieje jako rvalue — `forward` przywrócenie cechy rvalue argumentu.

Przywracanie cechy rvalue oryginalnej wartości argumentu w celu wykonania rozwiązania przeciążenia jest znane jako *doskonała przekazywania*. Doskonałe przekazywanie do przodu umożliwia funkcji szablonu zaakceptowanie argumentu któregokolwiek typu odwołania i przywrócenie jego cechy rvalue, gdy jest to niezbędne do poprawnego rozwiązania przeciążenia. Za pomocą doskonałego przekazywania do przodu można zachować semantykę przenoszenia dla rvalue i uniknąć konieczności zapewnienia przeciążeń dla funkcji, które różnią się tylko pod względem typu odwołania ich argumentów.

## <a name="get"></a>  Pobierz

Pobiera element z `pair` obiekt w pozycji indeksu lub typu.

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

*Index*<br/>
Indeks oparty na 0 elementu wyznaczonym.

*T1*<br/>
Typ pierwszy element pary.

*T2*<br/>
Typ drugiego elementu pary.

*żądania ściągnięcia*<br/>
Pary, które można wybierać.

### <a name="remarks"></a>Uwagi

Funkcje szablonów zwracają odwołania do elementu jego `pair` argumentu.

Dla indeksowanych przeciążeń Jeśli wartość *indeksu* wynosi 0, te funkcje zwracają `pr.first` i, jeśli wartość *indeksu* 1, te funkcje zwracają `pr.second`. Typ `RI` jest typu zwracanego elementu.

Dla przeciążeń, które nie mają parametr indeksu elementu do zwrócenia jest ustalane przez argument typu. Wywoływanie `get<T>(Tuple)` generuje błąd kompilatora, jeśli *żądania ściągnięcia* zawiera więcej lub mniej niż jeden element typu T.

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

    /*
    Output:
    9 3.14
    1 0.27
    */

}
```

## <a name="make_pair"></a>  make_pair

Funkcja szablonu, który służy do konstruowania obiektów typu `pair`, gdzie typy składników są wybierane automatycznie na podstawie typów danych, które są przekazywane jako parametry.

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

*val1*<br/>
Wartość, która inicjuje pierwszy element `pair`.

*Val2*<br/>
Wartość, która inicjuje drugi element `pair`.

### <a name="return-value"></a>Wartość zwracana

Obiekt pary, który jest konstruowany: `pair` <  `T`, `U`> ( `Val1`, `Val2`).

### <a name="remarks"></a>Uwagi

`make_pair` Konwertuje obiekt typu [reference_wrapper, klasa](../standard-library/reference-wrapper-class.md) na typy odwołań i konwertuje zanikające tablice i funkcje do wskaźników.

W zwracanym `pair` obiektu `T` jest określany w następujący sposób:

- Jeśli typ danych wejściowych `T` jest `reference_wrapper<X>`, zwrócony typ `T` jest `X&`.

- W przeciwnym razie zwracany typ `T` jest `decay<T>::type`. Jeśli [decay, klasa](../standard-library/decay-class.md) nie jest obsługiwany, zwrócony typ `T` jest taki sam jak typ danych wejściowych `T`.

Zwracany typ `U` jest podobnie określany z typu wejściowego `U`.

Jedną z zalet `make_pair` są określane automatycznie przez kompilator i nie muszą być jawnie określone typy obiektów, które są przechowywane. Nie używaj jawnych argumentów szablonów takich jak `make_pair<int, int>(1, 2)` zastosowania `make_pair` ponieważ jest to niepotrzebne powielenie informacji i dodaje problemy z odwołaniami rvalue złożonych, które mogą spowodować błąd kompilacji. W tym przykładzie poprawna składnia to `make_pair(1, 2)`

`make_pair` Funkcji pomocnika umożliwia także przekazywanie dwóch wartości do funkcji, która wymaga pary jako parametru wejściowego.

### <a name="example"></a>Przykład

Na przykład o tym, jak korzystać z funkcji pomocnika `make_pair` do zadeklarowania i zainicjowania pary, zobacz [pair — struktura](../standard-library/pair-structure.md).

## <a name="move"></a>  Przenieś

Bezwarunkowo rzutuje swój argument na odwołanie rvalue, a tym samym sygnalizuje, że może być przeniesione, jeśli jego typ umożliwia przenoszenie.

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ wywnioskowany z typu argumentu przekazanego *Arg*, wraz z regułami zwijania odwołania.|
|*ARG*|Argument do rzutowania. Chociaż typ *Arg* wydaje się być określony jako odwołanie rvalue, `move` również akceptuje argumenty lvalue, ponieważ odwołania lvalue można powiązać z odwołaniami rvalue.|

### <a name="return-value"></a>Wartość zwracana

`Arg` jako odwołanie rvalue czy jej typ jest typem referencyjnym.

### <a name="remarks"></a>Uwagi

Argument szablonu *typu* nie ma być jawnie określony, ale wnioskowany z typu wartości przekazanej w *Arg*. Typ *typu* jest następnie korygowany według reguł zwijania odniesienia.

`move` nie przenosi swojego argumentu. Zamiast tego przez rzutowanie bezwarunkowo swój argument — który może być lvalue — na odwołanie rvalue, pozwala następnie kompilatorowi przenieść, zamiast kopiowania, wartość przekazywana w *Arg* jeśli jego typ umożliwia przenoszenia. Jeżeli jego typ nie umożliwia przenoszenia, jest on zamiast tego kopiowany.

Jeśli wartość przekazywana w *Arg* to lvalue — czyli o nazwie lub mogą być podejmowane jego adres — zostaje unieważniony po przeniesieniu. Odwołuje się do wartości przekazanej w *Arg* przez jego nazwę lub adres po przeniesieniu.

## <a name="swap"></a>  swap

Zamienia elementy z dwóch [pair — struktura](../standard-library/pair-structure.md) obiektów.

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `pair`.|
|*right*|Obiekt typu `pair`.|

### <a name="remarks"></a>Uwagi

Jedną z zalet `swap` są określane automatycznie przez kompilator i nie muszą być jawnie określone typy obiektów, które są przechowywane. Nie używaj jawnych argumentów szablonów takich jak `swap<int, int>(1, 2)` zastosowania `swap` ponieważ jest to niepotrzebne powielenie informacji i dodaje problemy z odwołaniami rvalue złożonych, które mogą spowodować błąd kompilacji.

## <a name="see-also"></a>Zobacz także

[\<utility>](../standard-library/utility.md)<br/>
