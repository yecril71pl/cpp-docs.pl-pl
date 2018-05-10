---
title: '&lt;Narzędzie&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a26a4a0cab0bdea8a7a642cc760da0f3fc79b471
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltutilitygt-functions"></a>&lt;Narzędzie&gt; funkcji

||||
|-|-|-|
|[exchange](#exchange)|[Prześlij dalej](#forward)|[Get — funkcja &lt;narzędzia&gt;](#get)|
|[make_pair](#make_pair)|[Przenieś](#move)|[swap](#swap)|

## <a name="exchange"></a>  Program Exchange

**(C ++ 14)**  Przypisuje nową wartość do obiektu i zwraca jej Poprzednia wartość.

```cpp
template <class T, class Other = T>
T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>Parametry

`val` Obiekt, który otrzyma wartość new_val.

`new_val` Obiekt, którego wartość jest kopiowany lub przenoszony do val.

### <a name="remarks"></a>Uwagi

Dla typów złożonych `exchange` pozwala uniknąć kopiowanie stara wartość, gdy Konstruktor przenoszenia jest dostępny, pozwala uniknąć kopiowanie nowa wartość, jeśli jest obiektem tymczasowym lub zostanie przeniesiona, a akceptuje dowolny typ jako nowa wartość, przy użyciu dowolnego dostępne konwertowania operatora przypisania. Funkcja exchange różni się od [std::swap](../standard-library/algorithm-functions.md#swap) w tym Lewy argument nie jest przenoszone lub kopiowane do argumentu po prawej stronie.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie `exchange`. W świecie rzeczywistym `exchange` jest najbardziej przydatna w przypadku dużych obiektów, które są kosztowne do skopiowania:

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

## <a name="forward"></a>  Prześlij dalej

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
|`Type`|Typ przekazanej wartości `Arg`, który może być inny niż typ `Arg`. Zwykle określony przez argument szablonu funkcji przekazywania do przodu.|
|`Arg`|Argument do rzutowania.|

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do r-wartości `Arg` Jeśli przekazano wartość `Arg` pierwotnie r-wartości lub odwołanie do r-wartości; w przeciwnym razie zwraca `Arg` bez modyfikowania jej typu.

### <a name="remarks"></a>Uwagi

Należy określić argument jawnego szablonu, aby wywołać `forward`.

`forward` Nie przekazuj jej argument. Zamiast tego przez warunkowo rzutowanie jej argument odwołania do r-wartości, jeśli był pierwotnie r-wartości lub odwołania do wartości `forward` umożliwia kompilatorowi rozpoznawać przeciążenia znajomości oryginalny typ argumentu przekazany dalej. Jawnego typu argumentu funkcji przesyłania dalej może różnić się od jego oryginalny typ — na przykład gdy r-wartości jest używany jako argument do funkcji i jest powiązany z nazwy parametru; o nazwie ułatwia l-wartością, niezależnie od tego, czy wartość istnieje jako r-wartości — `forward` przywraca r-wartości przetwarzaniem do argumentu.

Przywracanie r-wartości przetwarzaniem do oryginalnej wartości argumentu w celu wykonywania Rozpoznanie przeciążenia nosi nazwę *doskonała przekazywania*. Doskonałe przekazywanie do przodu umożliwia funkcji szablonu zaakceptowanie argumentu któregokolwiek typu odwołania i przywrócenie jego cechy rvalue, gdy jest to niezbędne do poprawnego rozwiązania przeciążenia. Za pomocą doskonałego przekazywania do przodu można zachować semantykę przenoszenia dla rvalue i uniknąć konieczności zapewnienia przeciążeń dla funkcji, które różnią się tylko pod względem typu odwołania ich argumentów.

## <a name="get"></a>  Pobierz

Pobiera element na podstawie `pair` obiekt indeks lub typu.

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

`Index` Na podstawie 0 indeks elementu wyznaczonych.

`T1` Typ pierwszego elementu pary.

`T2` Typ drugiego elementu pary.

`pr` Para można wybierać.

### <a name="remarks"></a>Uwagi

Funkcje szablonów zwraca odwołanie do elementu jego `pair` argumentu.

Dla indeksowanego przeciążeń Jeśli wartość `Index` 0 zwracają `pr.first` i jeśli wartość `Index` 1 zwracają `pr.second`. Typ `RI` jest typ zwróconego elementu.

Do przeciążenia, które nie mają parametr indeksu elementu do zwrócenia jest ustalane przez argument typu. Wywoływanie `get<T>(Tuple)` spowoduje błąd kompilatora, jeśli `pr` zawiera więcej lub mniej niż jeden element typu T.

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

## <a name="make_pair"></a>  make_pair —

Funkcja szablonu, która służy do tworzenia obiektów typu `pair`, gdzie typów składników jest automatycznie wybierany na podstawie typów danych, które są przekazywane jako parametry.

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

`Val1` Wartość, która inicjuje pierwszego elementu obiektu `pair`.

`Val2` Wartość, która inicjuje drugiego elementu `pair`.

### <a name="return-value"></a>Wartość zwracana

Obiekt pary, który jest tworzony: `pair` <  `T`, `U`> ( `Val1`, `Val2`).

### <a name="remarks"></a>Uwagi

`make_pair` Konwertuje obiekt typu [reference_wrapper — klasa](../standard-library/reference-wrapper-class.md) do typów referencyjnych i konwertuje Zanikająca tablice i wskaźniki funkcji.

W zwróconym `pair` obiektu `T` jest określane w następujący sposób:

- Jeśli typ danych wejściowych `T` jest `reference_wrapper<X>`, zwracany typ `T` jest `X&`.

- W przeciwnym razie zwrócony typ `T` jest `decay<T>::type`. Jeśli [decay — klasa](../standard-library/decay-class.md) nie jest obsługiwana, zwrócony typ `T` jest taki sam jak typ danych wejściowych `T`.

Zwrócony typ `U` podobnie jest określana na podstawie typ danych wejściowych `U`.

Jedną z zalet `make_pair` typów obiektów, które są przechowywane są automatycznie określane przez kompilator i nie muszą być jawnie określona. Nie używaj takich jak jawne argumenty szablonu `make_pair<int, int>(1, 2)` korzystając `make_pair` ponieważ jest niepotrzebnie pełne i dodaje złożonych r-wartości odwołania problemów, które mogą spowodować niepowodzenie kompilacji. W tym przykładzie byłaby prawidłowa składnia `make_pair(1, 2)`

`make_pair` Funkcji Pomocnik umożliwia także do przekazania do funkcji, która wymaga pary jako parametr wejściowy dwóch wartości.

### <a name="example"></a>Przykład

Na przykład o tym, jak korzystać z funkcji pomocnika `make_pair` Aby zadeklarować i zainicjować parę, zobacz [pair — struktura](../standard-library/pair-structure.md).

## <a name="move"></a>  Przenieś

Bezwarunkowo rzutuje swój argument na odwołanie rvalue, a tym samym sygnalizuje, że może być przeniesione, jeśli jego typ umożliwia przenoszenie.

```cpp
template <class Type>
constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Type`|Przekazano wynikają z typem argumentu typu `Arg`, wraz z odwołaniem zwijanie reguły.|
|`Arg`|Argument do rzutowania. Mimo że typ `Arg` wydaje się być określone jako odwołanie do r-wartości `move` również akceptuje argumenty l-wartości, ponieważ odwołania l-wartością można powiązać odwołania do r-wartości.|

### <a name="return-value"></a>Wartość zwracana

`Arg` jako odwołanie do r-wartości czy jej typ jest typem referencyjnym.

### <a name="remarks"></a>Uwagi

Argument szablonu `Type` nie ma zostać określone jawnie, ale można określić na podstawie Typ przekazanej wartości `Arg`. Typ `Type` dodatkowe dostosowywane odwołanie zwijanie reguły.

`move` nie powoduje przeniesienia jej argument. Zamiast tego przez rzutowanie bezwarunkowo jej argument — co może być l-wartością — z odwołaniem wartościowanym prawostronnie umożliwia kompilatorowi przeniesienia, zamiast kopiowania, przekazano wartość `Arg` jeśli jej typ jest włączone przenoszenia. Jeżeli jego typ nie umożliwia przenoszenia, jest on zamiast tego kopiowany.

Jeśli przekazano wartość `Arg` jest l-wartością — to znaczy ma nazwę lub jego adresu może zostać pobrany — umieszczeniem po przeniesieniu. Nie odwołują się do wartości przekazano `Arg` według jego nazwy lub adresu po jest przenoszony.

## <a name="swap"></a>  Swap

Zamienia elementy dwóch [pair — struktura](../standard-library/pair-structure.md) obiektów.

```cpp
template <class T, class U>
void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Obiekt typu `pair`.|
|`right`|Obiekt typu `pair`.|

### <a name="remarks"></a>Uwagi

Jedną z zalet `swap` typów obiektów, które są przechowywane są automatycznie określane przez kompilator i nie muszą być jawnie określona. Nie używaj takich jak jawne argumenty szablonu `swap<int, int>(1, 2)` korzystając `swap` ponieważ jest niepotrzebnie pełne i dodaje złożonych r-wartości odwołania problemów, które mogą spowodować niepowodzenie kompilacji.

## <a name="see-also"></a>Zobacz także

[\<utility>](../standard-library/utility.md)<br/>
