---
title: enable_if — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 6e6b8a286dca8c451e6920e7f25f07829d3b453f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454216"
---
# <a name="enableif-class"></a>enable_if — Klasa

Warunkowo tworzy wystąpienie typu do rozpoznawania przeciążenia SFINAE. Zagnieżdżony element `enable_if<Condition,Type>::type` typedef istnieje — i jest synonimem `Type`dla — if i tylko `Condition` wtedy, gdy ma **wartość true**.

## <a name="syntax"></a>Składnia

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parametry

*B*\
Wartość określająca istnienie typu będącego wynikiem.

*&* \
Typ do wystąpienia, jeśli *B* ma wartość true.

## <a name="remarks"></a>Uwagi

Jeśli *B* ma wartość true `enable_if<B, T>` , ma zagnieżdżony element typedef o nazwie "Type", który jest synonimem dla *T*.

Jeśli *B* ma wartość false `enable_if<B, T>` , nie ma zagnieżdżonego elementu typedef o nazwie "Type".

Ten szablon aliasu jest dostępny:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

W C++, Niepowodzenie podstawiania parametrów szablonu nie jest błędem samego siebie — jest to określane jako *SFINAE* (niepowodzenie podstawiania nie jest błędem). `enable_if` Zwykle jest używany do usuwania kandydatów z rozpoznawania przeciążenia — to znaczy, że odrzuca zestaw przeciążenia, dzięki czemu jedna definicja może zostać odrzucona na korzyść innego. Jest to zgodne z zachowaniem SFINAE. Aby uzyskać więcej informacji na temat SFINAE, zobacz niepowodzenie podstawiania [nie jest błędem](https://go.microsoft.com/fwlink/p/?linkid=394798) w witrynie Wikipedia.

Oto cztery przykładowe scenariusze:

- Scenariusz 1: Zawijanie zwracanego typu funkcji:

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

- Scenariusz 2: Dodawanie parametru funkcji, który ma domyślny argument:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- Scenariusz 3: Dodawanie parametru szablonu, który ma domyślny argument:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scenariusz 4: Jeśli funkcja ma argument bez szablonu, można zawijać jego typ:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

Scenariusz 1 nie działa z konstruktorami i operatorami konwersji, ponieważ nie mają typów zwracanych.

Scenariusz 2 pozostawia parametr bez nazwy. Można to powiedzieć `::type Dummy = BAR`, ale nazwa `Dummy` jest nieistotna i nadając jej nazwę może wyzwolić ostrzeżenie "parametr bez odwołania". Musisz wybrać `FOO` typ parametru funkcji i `BAR` argument domyślny.  Można powiedzieć **int** i `0`, ale następnie użytkownicy kodu mogą przypadkowo przekazać do funkcji dodatkową liczbę całkowitą, która byłaby ignorowana. Zamiast tego `void **` zalecamy używanie `0` i lub **nullptr** , ponieważ niemal niczego nie można przekonwertować na `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Scenariusz 2 działa również w przypadku zwykłych konstruktorów.  Jednak nie działa w przypadku operatorów konwersji, ponieważ nie mogą przyjmować dodatkowych parametrów.  Nie działa również w przypadku konstruktorów [wariadyczne](../cpp/ellipses-and-variadic-templates.md) , ponieważ dodanie dodatkowych parametrów sprawia, że pakiet parametrów funkcji nie został wywnioskowany, a tym samym obniża `enable_if`cel.

Scenariusz 3 używa nazwy `Dummy`, ale jest opcjonalny. `typename = typename`"" Może działać, ale jeśli uważasz, że szuka brzmienia, możesz użyć nazwy "fikcyjnej" — po prostu nie używaj tego elementu, który może być również używany w definicji funkcji. Jeśli nie przydajesz typu do `enable_if`, jego wartość domyślna to void i jest to doskonale uzasadnione, ponieważ nie musisz dochodzić do tego, co `Dummy` to jest. Działa to w przypadku wszystkich elementów, takich jak operatory konwersji i konstruktory [wariadyczne](../cpp/ellipses-and-variadic-templates.md) .

Scenariusz 4 działa w konstruktorach, które nie mają zwracanych typów i w związku z tym rozwiązuje ograniczenie otoki scenariusza 1.  Jednak scenariusz 4 jest ograniczony do argumentów funkcji nienależących do szablonu, które nie są zawsze dostępne.  (Użycie scenariusza 4 w argumencie funkcji z szablonami uniemożliwia odliczanie argumentu szablonu od pracy z nim).

`enable_if`jest zaawansowany, ale również niebezpieczny, jeśli jest nieużywany.  Ponieważ celem jest przeprowadzenie kandydatów przed rozpoznaniem przeciążenia, gdy nie jest on używany, jego skutki mogą być bardzo mylące.  Poniżej przedstawiono niektóre zalecenia:

- Nie należy używać `enable_if` do wybierania między implementacjami w czasie kompilacji. Nie pisz jeszcze jeden `enable_if` dla `CONDITION` i drugi dla `!CONDITION`.  Zamiast tego należy użyć wzorca *wysyłania tagów* — na przykład algorytmu, który wybiera implementacje, w zależności od siły podanym iteratorów.

- Nie należy używać `enable_if` do wymuszania wymagań.  Jeśli chcesz sprawdzić poprawność parametrów szablonu, a jeśli Walidacja nie powiedzie się, wystąpi błąd, zamiast wybierać inną implementację, użyj [static_assert](../cpp/static-assert.md).

- Użyj `enable_if` w przypadku zestawu przeciążenia, który sprawia, że w przeciwnym razie dobry kod jest niejednoznaczny.  Najczęściej jest to spowodowane niejawnie konwertowaniem konstruktorów.

## <a name="example"></a>Przykład

W tym przykładzie wyjaśniono C++ , jak funkcja standardowego szablonu biblioteki [std:: make_pair ()](../standard-library/utility-functions.md#make_pair) korzysta `enable_if`z programu.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

W tym przykładzie `make_pair("foo", "bar")` zwraca wartość `pair<const char *, const char *>`. Rozpoznanie przeciążenia musi określić, `func()` która z nich ma zostać wybrana. `pair<A, B>`ma niejawnie przekonwertowanego `pair<X, Y>`konstruktora z.  To nie jest Nowość — w języku C++ 98. Jednak w języku C++ 98/03, niejawnie konwertowany podpis konstruktora zawsze istnieje, nawet jeśli jest `pair<int, int>(const pair<const char *, const char *>&)`to.  Funkcja rozpoznawania przeciążenia nie ma wpływu na to, że próba wystąpienia tego konstruktora zostaje `const char *` rozwinięta horribly, ponieważ nie jest to niejawnie konwertowane na **int**; szuka tylko sygnatur, zanim zostaną utworzone wystąpienia definicji funkcji.  W związku z tym przykładowy kod jest niejednoznaczny, ponieważ istnieją sygnatury do `pair<int, int>` przekonwertowania `pair<const char *, const char *>` na jednocześnie i `pair<string, string>`.

Język c++ 11 rozwiązał tę niejednoznaczność za `enable_if` pomocą polecenia, `pair<A, B>(const pair<X, Y>&)` aby upewnić `const X&` się, że istnieje `A` **tylko** wtedy, gdy jest `B`niejawnie konwertowany na i `const Y&` jest niejawnie konwertowany na.  Umożliwia to rozpoznanie przeciążenia, aby `pair<const char *, const char *>` określić, że nie `pair<int, int>` jest to możliwe do konwersji na `pair<string, string>` i że Przeciążenie, które pobiera, jest żywotne.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
