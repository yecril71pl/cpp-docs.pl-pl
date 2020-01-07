---
title: Auto(C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 0991c836d1ade663be3e1b734ec4745796b91abd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301655"
---
# <a name="auto-c"></a>Auto(C++)

Wywnioskuje typ zadeklarowanej zmiennej na podstawie jego wyrażenia inicjującego.

> [!NOTE]
> C++ Standard definiuje oryginalne i zmienione znaczenie dla tego słowa kluczowego. Przed Visual Studio **2010 słowo kluczowe** Automatic deklaruje zmienną w klasie magazynu *automatycznego* ; oznacza to, że zmienna, która ma lokalny okres istnienia. Począwszy od programu Visual Studio 2010, **słowo kluczowe** "autosłowa" deklaruje zmienną, której typ jest wywnioskowany na podstawie wyrażenia inicjowania w jego deklaracji. Opcja [/Zc:&#91;&#93; ](../build/reference/zc-auto-deduce-variable-type.md) autokompilator kontroluje **znaczenie słowa** kluczowego autosłowo kluczowe.

## <a name="syntax"></a>Składnia

```
auto declarator initializer;
```

```
[](auto param1, auto param2) {};
```

## <a name="remarks"></a>Uwagi

Słowo **kluczowe** "Direct" kieruje kompilator do użycia wyrażenia inicjującego zmiennej zadeklarowanej lub parametru wyrażenia lambda, aby ustalić jego typ.

Zalecamy używanie słowa kluczowego "autosłowo kluczowe **" w większości** sytuacji, chyba że naprawdę potrzebujesz konwersji — ponieważ zapewnia to następujące korzyści:

- **Niezawodność:** Jeśli typ wyrażenia jest zmieniony — obejmuje to, kiedy typ zwracany funkcji jest zmieniany — tylko działa.

- **Wydajność:** Masz gwarancję, że nie będzie żadnej konwersji.

- **Użyteczność:** Nie musisz martwić się o problemy pisowni nazwy typu i literówki.

- **Wydajność:** Kodowanie może być bardziej wydajne.

Przypadki konwersji, w których można nie **chcieć używać**Auto:

- Jeśli potrzebujesz określonego typu i nic nie zrobi.

- Typy pomocników szablonu wyrażenia — na przykład `(valarray+valarray)`.

Aby **użyć słowa** kluczowego autosłowo kluczowe, użyj go zamiast typu, aby zadeklarować zmienną i określić wyrażenie inicjalizacji. Ponadto można **zmodyfikować słowo kluczowe** autosłowa przy użyciu specyfikatorów i deklaratory, takich jak **const**, **volatile**, wskaźnik (`*`), Reference (`&`) i odwołania rvalue (`&&`). Kompilator szacuje wyrażenie inicjalizacji, a następnie użyje tych informacji do wywnioskowania typu zmiennej.

Wyrażenie inicjacji może być przypisaniem (składnią znaku równości), bezpośrednim inicjalizacją (składnią stylu funkcji), wyrażeniem [New](new-operator-cpp.md) lub wyrażeniem inicjowania może być parametrem *-Range-deklaracji* w instrukcji ["for" opartej na zakresie (C++)](../cpp/range-based-for-statement-cpp.md) . Aby uzyskać więcej informacji, zobacz [inicjatory](../cpp/initializers.md) i przykłady kodu w dalszej części tego dokumentu.

Słowo kluczowe " **automatycznie** " jest symbolem zastępczym dla typu, ale nie jest samo typem. W związku z tym nie można **używać słowa** kluczowego autosłowo kluczowe w rzutach ani operatorach C++, takich jak [sizeof](../cpp/sizeof-operator.md) i (for/CLI) [typeid](../extensions/typeid-cpp-component-extensions.md).

## <a name="usefulness"></a>Przydatność

**Funkcja** autosłowo kluczowe to prosty sposób deklarowania zmiennej, która ma typ skomplikowany. **Na przykład można użyć funkcji** Auto, aby zadeklarować zmienną, w której wyrażenie inicjacji obejmuje szablony, wskaźniki do funkcji lub wskaźniki do elementów członkowskich.

Można również użyć funkcji autodeklaruj i zainicjować **zmienną do wyrażenia** lambda. Nie można zadeklarować typu zmiennej samodzielnie, ponieważ typ wyrażenia lambda jest znany tylko kompilatorowi. Aby uzyskać więcej informacji, zobacz [Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Końcowe zwracane typy

Możesz użyć Auto, wraz ze specyfikatorem typu **decltype** **, aby**ułatwić pisanie bibliotek szablonów. Użyj **opcji** autoi **decltype** , aby zadeklarować funkcję szablonu, której typ zwracany zależy od typów argumentów szablonu. Lub **Użyj funkcji** autoi **decltype** , aby zadeklarować funkcję szablonu, która zawija wywołanie do innej funkcji, a następnie zwraca dowolny z nich jest typem zwracanym przez inną funkcję. Aby uzyskać więcej informacji, zobacz [decltype](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Odwołania i kwalifikatory CV

Należy pamiętać, **że przy użyciu** odwołań do porzucania, kwalifikatorów const i kwalifikatorów nietrwałych. Rozważmy następujący przykład:

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

W poprzednim przykładzie jest to wartość int, a nie odwołanie int, dlatego dane wyjściowe są `11 11`, a nie `11 12`, tak jakby kwalifikator odwołania nie został porzucony przez **funkcję Autostart**.

## <a name="type-deduction-with-braced-initializers-c14"></a>Odliczanie w nawiasach klamrowych (C++ 14)

Poniższy przykład kodu pokazuje, jak zainicjować funkcję autovariable przy użyciu nawiasów klamrowych. Należy zwrócić uwagę na różnice między B i C oraz między a i E.

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

W poniższej tabeli wymieniono ograniczenia dotyczące **użycia słowa** kluczowego "autosłowo kluczowe" oraz odpowiedni komunikat o błędzie diagnostycznym emitowany przez kompilator.

|Numer błędu|Opis|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|Słowa kluczowego autosłowo kluczowe nie można łączyć z jakimkolwiek innym specyfikatorem typu.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Symbol, który jest zadeklarowany za **pomocą słowa** kluczowego autosłowo kluczowe, musi mieć inicjator.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Użyto nieprawidłowego **słowa** kluczowego autosłowo kluczowe, aby zadeklarować typ. Na przykład zadeklarowano typ zwracany metody lub tablicę.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Nie można zadeklarować parametru lub argumentu szablonu za pomocą **słowa** kluczowego autosłowo kluczowe.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Nie można zadeklarować metody lub parametru szablonu za pomocą **słowa** kluczowego autosłowo kluczowe.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Nie można użyć symbolu przed jego zainicjowaniem. W tym przypadku oznacza to, że zmienna nie może zostać użyta do zainicjowania siebie.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Nie można rzutować na typ, który jest zadeklarowany za **pomocą słowa** kluczowego autosłowo kluczowe.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Wszystkie symbole na liście deklarator, które są zadeklarowane za pomocą słowa kluczowego autosłowo **kluczowe, muszą** być rozpoznawane jako ten sam typ. Aby uzyskać więcej informacji, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Operatorów [sizeof](../cpp/sizeof-operator.md) i [typeid](../extensions/typeid-cpp-component-extensions.md) nie można zastosować do symbolu, który jest zadeklarowany za pomocą **słowa** kluczowego autosłowo kluczowe.|

## <a name="examples"></a>Przykłady

Te fragmenty kodu ilustrują niektóre sposoby **używania słowa** kluczowego autosłowo kluczowe.

Następujące deklaracje są równoważne. W pierwszej instrukcji zmienna `j` jest zadeklarowana jako typ **int**. W drugiej instrukcji zmienna `k` jest określana jako typ **int** , ponieważ wyrażenie inicjalizacji (0) jest liczbą całkowitą.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Następujące deklaracje są równoważne, ale druga deklaracja jest prostsza od pierwszej. Jednym z najbardziej atrakcyjnych powodów **użycia słowa** kluczowego autosłowo kluczowe jest uproszczenie.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Poniższy fragment kodu deklaruje typ zmiennych `iter` i `elem`, gdy rozpoczyna **się pętla** **for** i Range.

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

Poniższy fragment kodu używa operatora **New** i deklaracji wskaźnika do deklarowania wskaźników.

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

Ten fragment kodu używa operatora warunkowego (`?:`) do deklarowania zmiennej `x` jako liczby całkowitej o wartości 200:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

Poniższy fragment kodu inicjuje zmienną `x` do wpisywania **int**, zmiennej `y` do odwołania do typu **const int**, a zmienna `fp` do wskaźnika do funkcji, która zwraca typ **int**.

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

[Auto, słowo kluczowe](../cpp/auto-keyword.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof, operator](../cpp/sizeof-operator.md)<br/>
[typeid](../extensions/typeid-cpp-component-extensions.md)<br/>
[Nowy operator](new-operator-cpp.md)<br/>
[Deklaracje i definicje](declarations-and-definitions-cpp.md)<br/>
[Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Inicjatory](../cpp/initializers.md)<br/>
[decltype](../cpp/decltype-cpp.md)
