---
title: enable_if — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: b6990dba20643b35dde36a492d40c3e3e76ae0b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591883"
---
# <a name="enableif-class"></a>enable_if — Klasa

Warunkowo sprawia, że wystąpienie typu SFINAE Rozpoznanie przeciążenia. Zagnieżdżony typedef `enable_if<Condition,Type>::type` istnieje — i jest synonimem dla `Type`— tylko wtedy, gdy `Condition` jest **true**.

## <a name="syntax"></a>Składnia

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parametry

*B*<br/>
Wartość, która określa istnienie wynikowy typ.

*T*<br/>
Typ do utworzenia wystąpienia, jeśli *B* ma wartość true.

## <a name="remarks"></a>Uwagi

Jeśli *B* ma wartość true, `enable_if<B, T>` ma element zagnieżdżony typedef o nazwie "type", który jest synonimem dla *T*.

Jeśli *B* ma wartość FAŁSZ, `enable_if<B, T>` nie zawiera zagnieżdżony typedef o nazwie "type".

Dostarczono szablon tego aliasu:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

W języku C++, Niepowodzenie podstawiania parametrów szablonu nie jest to błąd w sobie — jest to określane jako *SFINAE* (niepowodzenie podstawienia nie jest błąd "). Zazwyczaj `enable_if` służy do usuwania kandydatów przeciążonym — czyli go culls zestaw przeciążenia — tak, aby jedna definicja może odrzucić na rzecz innego. Odpowiada to zachowanie SFINAE. Aby uzyskać więcej informacji na temat SFINAE zobacz [błąd podstawienia nie jest to błąd](http://go.microsoft.com/fwlink/p/?linkid=394798) w witrynie Wikipedia.

Poniżej przedstawiono cztery przykładowe scenariusze:

- Scenariusz 1: Zawijanie zwracany typ funkcji:

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

- Scenariusz 2: Dodawanie parametru funkcji, która ma argument domyślny:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- Scenariusz 3: Dodawanie parametru szablonu, który ma argument domyślny:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Scenariusz 4: Jeśli funkcji ma argument bez szablonu, można opakować typ:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

Scenariusz 1 nie działa z konstruktorów i operatory konwersji, ponieważ nie mają zwracanych typów.

Scenariusz 2 pozostawia parametrów bez nazwy. Można powiedzieć `::type Dummy = BAR`, ale nazwa `Dummy` nie ma znaczenia, i może wyzwalać to ostrzeżenie "Nieużywany parametr" nadając mu nazwę. Należy wybrać opcję `FOO` typ parametru funkcji i `BAR` domyślnych argumentów.  Można powiedzieć **int** i `0`, ale następnie użytkownicy Twój kod może przypadkowo przekazać do funkcji dodatkowych liczba całkowita, która będzie ignorowane. Zamiast tego zaleca się używanie `void **` i `0` lub **nullptr** ponieważ prawie nic nie jest konwertowany na `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Scenariusz 2 działa również w przypadku zwykłych konstruktorów.  Jednak to nie zadziała dla operatorów konwersji, ponieważ nie przyjmują dodatkowe parametry.  Ponadto nie działa dla [ze zmienną liczbą argumentów](../cpp/ellipses-and-variadic-templates.md) konstruktory ponieważ dodanie dodatkowych parametrów sprawia, że parametr funkcji pakietu kontekst wywnioskować, a tym samym pozbawia `enable_if`.

Scenariusz 3 używa nazwy `Dummy`, ale jest opcjonalny. Po prostu " `typename = typename`" będzie działać, ale jeśli Twoim zdaniem wygląda nieco dziwne, można użyć nazwy "fikcyjny" — po prostu nie użyj jednej z nich, które mogą być również używane w definicji funkcji. Jeśli nie udzielisz typu `enable_if`, jego wartość domyślna to void i doskonale jest uzasadnione, ponieważ nieważne co `Dummy` jest. Działa to w przypadku wszystkim, łącznie z operatorów konwersji i [ze zmienną liczbą argumentów](../cpp/ellipses-and-variadic-templates.md) konstruktorów.

Scenariusz 4 działa w konstruktorach, które nie mają zwracanych typów, a tym samym rozwiązuje ograniczenie zawijania scenariusz 1.  Scenariusz 4 jest jednak ograniczone do argumentów bez szablonu funkcji, które nie są zawsze dostępne.  (Przy użyciu 4 scenariusz na argumentu funkcji oparte na szablonach zapobiega odliczanie argumentu szablon z pracujemy nad tym.)

`enable_if` to zaawansowane, ale także niebezpieczne, jeśli jest niewłaściwego użycia.  Jej celem jest zapewnienie kandydatów znikają przed Rozpoznanie przeciążenia, gdy jest niewłaściwego użycia, jego skutków może być bardzo mylące.  Poniżej przedstawiono kilka zaleceń:

- Nie używaj `enable_if` wybrać między implementacjami w czasie kompilacji. Nigdy nie zapisuj jeden `enable_if` dla `CONDITION` i inny wpis dla `!CONDITION`.  Zamiast tego należy użyć *tag wysyłania* wzorzec — na przykład algorytm, który wybiera implementacji w zależności od silnych Iteratory mają one.

- Nie używaj `enable_if` do wymuszania wymagań.  Jeśli chcesz sprawdzić poprawność parametrów szablonu, a Jeśli weryfikacja zakończy się niepowodzeniem, powodują wystąpienie błędu zamiast zaznaczania innego wdrożenia, należy użyć [static_assert](../cpp/static-assert.md).

- Użyj `enable_if` przypadku zestaw przeciążenia, który sprawia, że w przeciwnym razie dobre kodu niejednoznaczne.  Najczęściej dzieje się to niejawnie konwersja konstruktorów.

## <a name="example"></a>Przykład

W tym przykładzie opisano sposób standardowej biblioteki języka C++ funkcji szablonu [std::make_pair()](../standard-library/utility-functions.md#make_pair) wykorzystuje `enable_if`.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

W tym przykładzie `make_pair("foo", "bar")` zwraca `pair<const char *, const char *>`. Rozpoznanie przeciążenia musi ustalić, które `func()` ma. `pair<A, B>` ma konstruktora niejawnej konwersji z `pair<X, Y>`.  Nie jest to nowy — w języku C ++ 98. Jednak w języku C ++ 98/03, sygnatury konstruktora niejawnej konwersji zawsze istnieje, nawet jeśli jest on `pair<int, int>(const pair<const char *, const char *>&)`.  Rozpoznanie przeciążenia zależy, czy podjęto próbę utworzenia wystąpienia tego konstruktora rozkłada horribly, ponieważ `const char *` nie jest niejawnie konwertowany na **int**; tylko poszukuje podpisów, przed funkcją definicje są wystąpienia.  W związku z tym, przykładowy kod jest niejednoznaczny, ponieważ istnieje podpisów, aby przekonwertować `pair<const char *, const char *>` zarówno `pair<int, int>` i `pair<string, string>`.

C ++ 11 rozwiązać tę niejednoznaczność, za pomocą `enable_if` zapewnienie `pair<A, B>(const pair<X, Y>&)` istnieje **tylko** podczas `const X&` jest niejawnie konwertowany na `A` i `const Y&` jest niejawnie konwertowany na `B`.  Dzięki temu określić, że funkcja rozpoznawania przeciążeń `pair<const char *, const char *>` nie jest konwertowany na `pair<int, int>` i że przeciążenie przyjmującej `pair<string, string>` jest możliwego do użycia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
