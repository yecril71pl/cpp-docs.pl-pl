---
title: /Zc:twoPhase- (Wyłącz dwufazowe wyszukiwanie nazw)
description: 'Wyjaśnia, jak/Zc: twoPhase-wyłącza dwufazowe wyszukiwanie nazw po określeniu/permissive-.'
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: a2ede9f0875bf718d63361201cf8923666078f7a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856959"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (Wyłącz dwufazowe wyszukiwanie nazw)

**/Zc: twoPhase-** opcja w obszarze **/permissive-** , instruuje kompilator, aby używa oryginalnego, niezgodnego z kompilatorem zachowania C++ firmy Microsoft do analizowania i tworzenia wystąpienia szablonów klas i szablonów funkcji.

## <a name="syntax"></a>Składnia

> **/Zc:twoPhase-**

## <a name="remarks"></a>Uwagi

Visual Studio 2017 w wersji 15,3 i nowszej: w obszarze [/permissive-](permissive-standards-conformance.md)kompilator używa dwufazowego wyszukiwania nazw w celu rozpoznawania nazw szablonów. Jeśli określisz także **/Zc: twoPhase-** , kompilator powróci do poprzedniego niezgodnego szablonu klasy i rozpoznawania nazw szablonu funkcji oraz zachowania podstawiania. Gdy **/permissive-** nie jest określony, domyślnie jest zachowanie niezgodne.

Pliki nagłówkowe Windows SDK w wersji 10.0.15063.0 (twórcy Update lub RS2) i starsze nie działają w trybie zgodności. **/Zc: twoPhase —** jest wymagana do kompilowania kodu dla tych wersji zestawu SDK w przypadku używania **/permissive-** . Wersje Windows SDK zaczynające się od wersji 10.0.15254.0 (jesień Update lub RS3) działają prawidłowo w trybie zgodności. Nie wymagają opcji **/Zc: twoPhase** .

Użyj **/Zc: twoPhase —** Jeśli kod wymaga poprawnego skompilowania starego zachowania. Zdecydowanie należy rozważyć zaktualizowanie kodu, aby był zgodny ze standardem.

### <a name="compiler-behavior-under-zctwophase-"></a>Zachowanie kompilatora w obszarze/Zc: twoPhase-

Domyślnie, lub w programie Visual Studio 2017 w wersji 15,3 lub nowszej po określeniu zarówno **/permissive-** , jak i **/Zc: twoPhase —** kompilator używa tego zachowania:

- Analizuje on tylko deklarację szablonu, główną klasę i listę klas bazowych. Treść szablonu jest przechwytywana jako strumień tokenu. Nie są analizowane żadne treści funkcji, inicjatory, argumenty domyślne ani argumenty noexcept. Szablon klasy jest pseudo skonkretyzowany na niezalecanym typie, aby sprawdzić, czy deklaracje w szablonie klasy są poprawne. Rozważmy ten szablon klasy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Są analizowane deklaracje szablonu, `template <typename T>`, `class Derived`główna klasy i `public Base<T>` listy klas podstawowych, ale treść szablonu jest przechwytywana jako strumień tokenu.

- Podczas analizowania szablonu funkcji Kompilator analizuje tylko sygnaturę funkcji. Treść funkcji nigdy nie jest analizowana. Zamiast tego jest przechwytywany jako strumień tokenu.

W związku z tym, jeśli treść szablonu ma błędy składniowe, ale szablon nigdy nie zostanie uruchomiony, kompilator nie zdiagnozowanuje błędów.

Innym skutkiem takiego zachowania jest rozwiązanie przeciążenia. Niestandardowe zachowanie odbywa się ze względu na sposób, w jaki strumień tokenu jest rozwinięty w lokacji tworzenia wystąpienia. Symbole, które nie były widoczne w deklaracji szablonu, mogą być widoczne w punkcie tworzenia wystąpienia. Oznacza to, że mogą uczestniczyć w rozwiązywaniu przeciążenia. Zmiany szablonów można znaleźć na podstawie kodu, który nie był widoczny w definicji szablonu, w przeciwieństwie do standardu.

Na przykład, rozważmy ten kod:

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

Oto dane wyjściowe w przypadku korzystania z trybu domyślnego, tryb zgodności i tryb zgodności z **/Zc: twoPhase-** opcje kompilatora:

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

Po skompilowaniu w trybie zgodności w obszarze **/permissive-** , ten program drukuje "`Standard two-phase`", ponieważ drugie Przeciążenie `func` nie jest widoczne, gdy kompilator osiągnie szablon. W przypadku dodania **/Zc: twoPhase —** program drukuje "`Microsoft one-phase`". Dane wyjściowe są takie same, jak w przypadku nieokreślenia **/permissive-** .

*Nazwy zależne* są nazwami, które są zależne od parametru szablonu. Te nazwy mają zachowanie wyszukiwania, które jest również inne w obszarze **/Zc: twoPhase-** . W trybie zgodności nazwy zależne nie są powiązane w punkcie definicji szablonu. Zamiast tego Kompilator wyszukuje je podczas tworzenia wystąpienia szablonu. W przypadku wywołań funkcji z nazwą funkcji zależnej nazwa jest powiązana z funkcjami widocznymi w miejscu wywołania w definicji szablonu. Dodatkowe przeciążenia z wyszukiwania zależnego od argumentów są dodawane, zarówno w punkcie definicji szablonu, jak i w punkcie tworzenia wystąpienia szablonu.

Dwufazowe wyszukiwanie składa się z dwóch części: wyszukiwania nazw niezależnych podczas definiowania szablonu oraz wyszukiwanie nazw zależnych podczas tworzenia wystąpienia szablonu. W obszarze **/Zc: twoPhase —** kompilator nie wykonuje wyszukiwania zależnego od argumentów oddzielnie od niekwalifikowanego wyszukiwania. Oznacza to, że nie wykonuje dwuetapowego wyszukiwania, dlatego wyniki rozpoznawania przeciążenia mogą się różnić.

Oto inny przykład:

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

Po skompilowaniu bez **/permissive-** ten kod drukuje:

```Output
func(int)
NS::func(NS::S)
```

Podczas kompilowania przy użyciu **/permissive-** , ale bez **/Zc: twoPhase —** ten kod drukuje:

```Output
func(long)
NS::func(NS::S)
```

Po skompilowaniu z zarówno **/permissive-** , jak i **/Zc: twoPhase —** ten kod drukuje:

```Output
func(int)
NS::func(NS::S)
```

W trybie zgodności w obszarze **/permissive-** wywołanie `tfunc(1729)` jest rozpoznawane jako Przeciążenie `void func(long)`. Nie jest on rozpoznawany jako Przeciążenie `void func(int)`, jak w obszarze **/Zc: twoPhase-** . Wynika to z faktu, że niekwalifikowana `func(int)` jest zadeklarowana po definicji szablonu i nie można jej znaleźć za pomocą wyszukiwania zależnego od argumentów. Ale `void func(S)` uczestniczy w wyszukiwaniu zależnym od argumentów, więc jest dodawana do zestawu przeciążenia dla `tfunc(s)`wywołania, mimo że jest zadeklarowany po funkcji szablonu.

### <a name="update-your-code-for-two-phase-conformance"></a>Aktualizowanie kodu na potrzeby dwuetapowej zgodności

Starsze wersje kompilatora nie wymagają słów kluczowych `template` i `typename` wszędzie tam, gdzie C++ są one wymagane przez Standard. Te słowa kluczowe są konieczne w niektórych pozycjach w celu odróżnienia, w jaki sposób kompilatory powinny analizować nazwę zależną podczas pierwszej fazy wyszukiwania. Na przykład:

`T::Foo<a || b>(c);`

Kompilator zgodny z analizą `Foo` jako zmienna w zakresie `T`, co oznacza, że ten kod jest wyrażeniem logicznym lub z `T::foo < a` jako lewym operandem i `b > (c)` jako prawy operand. Jeśli zamierzasz używać `Foo` jako szablonu funkcji, musisz wskazać, że jest to szablon poprzez dodanie słowa kluczowego `template`:

`T::template Foo<a || b>(c);`

W wersjach programu Visual Studio 2017 w wersji 15,3 i nowszych, gdy **/permissive-** i **/Zc: twoPhase-** są określone, kompilator zezwala na ten kod bez słowa kluczowego `template`. Interpretuje kod jako wywołanie do szablonu funkcji z argumentem `a || b`, ponieważ analizuje tylko szablony w ograniczony sposób. Powyższy kod nie jest analizowany w pierwszej fazie. W drugiej fazie istnieje wystarczająco dużo kontekstu, aby określić, że `T::Foo` jest szablonem, a nie zmienną, więc kompilator nie wymusza użycia słowa kluczowego.

Takie zachowanie może być również widoczne przez usunięcie słowa kluczowego `typename` przed nazwami w treści szablonu funkcji, inicjatorach, argumentów domyślnych i noexcept argumentów. Na przykład:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Jeśli nie używasz słowa kluczowego `typename` w treści funkcji, ten kod kompiluje się w obszarze **/permissive-/Zc: twoPhase-** , ale nie w ramach samego **/permissive-** . Słowo kluczowe `typename` jest wymagane, aby wskazać, że `TYPE` jest zależna. Ponieważ treść nie jest analizowana w **/Zc: twoPhase-** , kompilator does't wymaga słowa kluczowego. W trybie zgodności **/permissive-** kod bez słowa kluczowego `typename` generuje błędy. Aby przeprowadzić migrację kodu do zgodności w programie Visual Studio 2017 w wersji 15,3 i poza nią, Wstaw słowo kluczowe `typename`, w którym brakuje.

Podobnie Rozważmy ten przykład kodu:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

W obszarze **/permissive-/Zc: twoPhase-** i we wcześniejszych kompilatorach kompilator wymaga tylko słowa kluczowego `template` w wierszu 2. W trybie zgodności kompilator wymaga również słowa kluczowego `template` w wierszu 4, aby wskazać, że `T::X<T>` jest szablonem. Poszukaj kodu, w którym brakuje słowa kluczowego this, i podaj go, aby kod był zgodny ze standardem.

Aby uzyskać więcej informacji na temat problemów ze zgodnością, zobacz [ C++ ulepszenia zgodności w programie Visual Studio](../../overview/cpp-conformance-improvements.md) i [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > strony właściwości **wiersza polecenia** **C++ C/**  > .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: twoPhase-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
