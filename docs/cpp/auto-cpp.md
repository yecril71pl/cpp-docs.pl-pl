---
title: auto (C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 675f6919b6804cfb1d2c5395d046cb5fa39e625d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229197"
---
# <a name="auto-c"></a>`auto`Języków

Wywnioskuje typ zadeklarowanej zmiennej na podstawie jego wyrażenia inicjującego.

> [!NOTE]
> Standard C++ definiuje oryginalne i zmienione znaczenie dla tego słowa kluczowego. Przed Visual Studio 2010 **`auto`** słowo kluczowe deklaruje zmienną w *automatycznej* klasie magazynu, czyli zmienną, która ma lokalny okres istnienia. Począwszy od programu Visual Studio 2010, **`auto`** słowo kluczowe deklaruje zmienną, której typ jest wywnioskowany z wyrażenia inicjowania w jego deklaracji. Opcja kompilatora [ `/Zc:auto`&#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md) kontroluje znaczenie **`auto`** słowa kluczowego.

## <a name="syntax"></a>Składnia

> **`auto`***declarator* *inicjator* deklarator**`;`**

> **`[](auto`***param1* **`, auto`** *param2***`) {};`**

## <a name="remarks"></a>Uwagi

**`auto`** Słowo kluczowe kieruje kompilator do użycia wyrażenia inicjującego zmiennej zadeklarowanej lub parametru wyrażenia lambda, aby ustalić jego typ.

Zalecamy używanie **`auto`** słowa kluczowego w większości sytuacji — chyba że naprawdę chcesz wykonać konwersję, ponieważ zapewnia to następujące korzyści:

- **Niezawodność:** Jeśli typ wyrażenia jest zmieniony — obejmuje to, kiedy typ zwracany funkcji jest zmieniany — tylko działa.

- **Wydajność:** Masz gwarancję, że nie będzie żadnej konwersji.

- **Użyteczność:** Nie musisz martwić się o problemy pisowni nazwy typu i literówki.

- **Wydajność:** Kodowanie może być bardziej wydajne.

Przypadki konwersji, w których może nie być używane **`auto`** :

- Jeśli potrzebujesz określonego typu i nic nie zrobi.

- Typy pomocników szablonu wyrażenia — na przykład `(valarray+valarray)` .

Aby użyć **`auto`** słowa kluczowego, użyj go zamiast typu, aby zadeklarować zmienną i określić wyrażenie inicjalizacji. Ponadto można zmodyfikować **`auto`** słowo kluczowe przy użyciu specyfikatorów i deklaratory takich jak **`const`** , **`volatile`** , wskaźnik ( **`*`** ), Reference ( **`&`** ) i rvalue Reference ( **`&&`** ). Kompilator szacuje wyrażenie inicjalizacji, a następnie użyje tych informacji do wywnioskowania typu zmiennej.

Wyrażeniem inicjalizacji może być przypisanie (składnia znaku równości), bezpośrednie inicjowanie (składnia w stylu funkcji), [`operator new`](new-operator-cpp.md) wyrażenie lub wyrażenie inicjacji, może być parametrem *-Range-deklaracji* w instrukcji [ `for` instrukcji (C++) opartej na zakresie](../cpp/range-based-for-statement-cpp.md) . Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i przykłady kodu w dalszej części tego dokumentu.

**`auto`** Słowo kluczowe jest symbolem zastępczym dla typu, ale nie jest samo typem. W związku z tym **`auto`** słowo kluczowe nie może być używane w rzutach ani operatorach, takich jak [`sizeof`](../cpp/sizeof-operator.md) i (dla C++/CLI) [`typeid`](../extensions/typeid-cpp-component-extensions.md) .

## <a name="usefulness"></a>Przydatność

**`auto`** Słowo kluczowe to prosty sposób deklarowania zmiennej, która ma typ skomplikowany. Na przykład można użyć, **`auto`** Aby zadeklarować zmienną, w której wyrażenie inicjacji obejmuje szablony, wskaźniki do funkcji lub wskaźniki do elementów członkowskich.

Można również użyć **`auto`** do zadeklarowania i zainicjowania zmiennej w wyrażeniu lambda. Nie można zadeklarować typu zmiennej samodzielnie, ponieważ typ wyrażenia lambda jest znany tylko kompilatorowi. Aby uzyskać więcej informacji, zobacz [Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Końcowe zwracane typy

**`auto`** **`decltype`** Aby ułatwić pisanie bibliotek szablonów, można użyć razem ze specyfikatorem typu. Użyj **`auto`** i, **`decltype`** Aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Lub Użyj **`auto`** i, **`decltype`** Aby zadeklarować funkcję szablonu, która zawija wywołanie do innej funkcji, a następnie zwraca dowolny typ zwracany przez inną funkcję. Aby uzyskać więcej informacji, zobacz [`decltype`](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Odwołania i kwalifikatory CV

Należy pamiętać, że przy użyciu **`auto`** odwołujących się odwołań, **`const`** kwalifikatorów i **`volatile`** kwalifikatorów. Rozpatrzmy następujący przykład:

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

W poprzednim przykładzie jest to **`int`** , **`int`** a nie odwołanie, dlatego dane wyjściowe nie są tak `11 11` , `11 12` jak byłyby w przypadku, gdy kwalifikator odwołania nie został porzucony przez **`auto`** .

## <a name="type-deduction-with-braced-initializers-c14"></a>Odliczanie w nawiasach klamrowych (C++ 14)

Poniższy przykład kodu pokazuje, jak zainicjować **`auto`** zmienną za pomocą nawiasów klamrowych. Należy zwrócić uwagę na różnice między B i C oraz między a i E.

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>Ograniczenia i komunikaty o błędach

W poniższej tabeli wymieniono ograniczenia dotyczące użycia **`auto`** słowa kluczowego i odpowiadający mu komunikat o błędzie diagnostycznym, który emituje kompilator.

|Numer błędu|Opis|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|**`auto`** Nie można łączyć słowa kluczowego z żadnym innym specyfikatorem typu.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, który jest zadeklarowany za pomocą **`auto`** słowa kluczowego, musi mieć inicjator.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Słowo kluczowe jest nieprawidłowo używane **`auto`** do deklarowania typu. Na przykład zadeklarowano typ zwracany metody lub tablicę.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Nie można zadeklarować parametru lub argumentu szablonu za pomocą **`auto`** słowa kluczowego.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Nie można zadeklarować metody lub parametru szablonu za pomocą **`auto`** słowa kluczowego.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Nie można użyć symbolu przed jego zainicjowaniem. W tym przypadku oznacza to, że zmienna nie może zostać użyta do zainicjowania siebie.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nie można rzutować na typ, który jest zadeklarowany za pomocą **`auto`** słowa kluczowego.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Wszystkie symbole na liście deklarator, które są zadeklarowane za pomocą **`auto`** słowa kluczowego, muszą być rozpoznawane jako ten sam typ. Aby uzyskać więcej informacji, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Operatorów [sizeof](../cpp/sizeof-operator.md) i [typeid](../extensions/typeid-cpp-component-extensions.md) nie można zastosować do symbolu, który jest zadeklarowany ze **`auto`** słowem kluczowym.|

## <a name="examples"></a>Przykłady

Te fragmenty kodu ilustrują niektóre sposoby **`auto`** używania słowa kluczowego.

Następujące deklaracje są równoważne. W pierwszej instrukcji zmienna `j` jest zadeklarowana jako typ **`int`** . W drugiej instrukcji zmienna `k` jest określana jako typ, **`int`** ponieważ wyrażenie inicjacji (0) jest liczbą całkowitą.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Następujące deklaracje są równoważne, ale druga deklaracja jest prostsza od pierwszej. Jednym z najbardziej atrakcyjnych powodów użycia **`auto`** słowa kluczowego jest prostota.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Poniższy fragment kodu deklaruje typ zmiennych `iter` i `elem` gdy **`for`** **`for`** rozpoczynane są pętle i.

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

Poniższy fragment kodu używa **`new`** deklaracji operatora i wskaźnika, aby zadeklarować wskaźniki.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

Następny fragment kodu deklaruje wiele symboli w każdej instrukcji deklaracji. Zwróć uwagę, że wszystkie symbole w każdej instrukcji rozpoznają ten sam typ.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

Ten fragment kodu używa operatora warunkowego ( `?:` ) do deklarowania zmiennej `x` jako liczby całkowitej o wartości 200:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

Poniższy fragment kodu inicjuje zmienną `x` do typu **`int`** , zmienna `y` dla odwołania do typu **`const int`** i zmienna `fp` do wskaźnika do funkcji, która zwraca typ **`int`** .

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>Zobacz także

[`auto`Kodu](../cpp/auto-keyword.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[`/Zc:auto`(Wywnioskowanie typu zmiennej)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[`sizeof`Zakład](../cpp/sizeof-operator.md)<br/>
[`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
[`operator new`](new-operator-cpp.md)<br/>
[Deklaracje i definicje](declarations-and-definitions-cpp.md)<br/>
[Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicjatory](../cpp/initializers.md)<br/>
[`decltype`](../cpp/decltype-cpp.md)
