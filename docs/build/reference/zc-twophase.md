---
title: /Zc:twoPhase-(Wyłącz dwufazowe wyszukiwanie nazw) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30647ab07984c393b10d7c0fb74d0e2be35cdf26
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723297"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(Wyłącz dwufazowe wyszukiwanie nazw)

Gdy **/Zc:twoPhase-** opcja zostanie określona, kompilator analizuje i tworzy szablony klas i funkcji w taki sam sposób niezgodnych, dostępne w wersjach programu Visual Studio przed Visual Studio 2017 w wersji 15.3.

## <a name="syntax"></a>Składnia

> **/Zc:twoPhase-**

## <a name="remarks"></a>Uwagi

W programie Visual Studio 2017 w wersji 15.3 lub nowszy, domyślnie kompilator używa dwufazowe wyszukiwanie nazw do rozpoznawania nazwy szablonu. Jeśli **/Zc:twoPhase-** jest określony, kompilator powraca do jego poprzedniego niezgodnych klasy szablonu i funkcji szablonu rozdzielczość i podstawienia zachowanie nazwy.

**/Zc:twoPhase-** nie ustawiono opcję, aby włączyć niezgodnych zachowanie domyślne. [/ Permissive-](permissive-standards-conformance.md) opcji ustawia niejawnie odpowiadające zachowanie kompilatora dwufazowe wyszukiwanie, ale może być zastąpiona przy użyciu **/Zc:twoPhase-**.

Pliki nagłówków zestawu Windows SDK w wersji 10.0.15063.0 (Aktualizacja dla twórców lub czerwonego kamienia 2) i starszych wersjach będą działać poprawnie w trybie zgodności. Należy użyć **/Zc:twoPhase-** do kompilowania kodu dla tych wersji zestawu SDK, gdy używasz programu Visual Studio 2017 w wersji 15.3 lub nowszym. Wersje zestawu SDK Windows, począwszy od wersji 10.0.15254.0 (3 czerwonego kamienia lub Fall Creators Update) działają prawidłowo w trybie zgodności i nie wymagają **/Zc:twoPhase-** opcji.

Użyj **/Zc:twoPhase-** Jeśli kod wymaga stare zachowanie do poprawnej kompilacji. Zdecydowanie rozważyć aktualizowanie kodu w taki sposób, aby były zgodne ze standardem.

### <a name="compiler-behavior-under-zctwophase-"></a>Zachowanie kompilatora, w obszarze /Zc:twoPhase-

W wersji kompilatora przed Visual Studio 2017 w wersji 15.3 i kiedy **/Zc:twoPhase-** jest określony, kompilator używa tego zachowania:

- Analizuje ona tylko do deklaracji szablonu, head klasy i liście klas bazowych. Treść szablonu jest przechwytywany jako strumień tokenu. Nie treści funkcji, inicjatory, argumenty domyślne lub noexcept argumenty są parsowane. Szablon klasy jest tworzone pseudo niepewnego typu, aby sprawdzić, czy deklaracji w klasie szablonu są prawidłowe. Należy wziąć pod uwagę ten szablon klasy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Deklaracja szablonu `template <typename T`>, head klasy `class Derived`i listy klas podstawowych `public Base<T>` są analizowane, ale treści szablonu jest przechwytywany jako strumień tokenu.

- Podczas analizowania szablonu funkcji, w którym kompilator analizuje tylko sygnatura funkcji. Nigdy nie jest analizowana z treści funkcji. Zamiast tego jest przechwytywany jako strumień tokenu.

W rezultacie jeśli treść szablonu zawiera błędy składniowe i nigdy nie zostanie utworzone wystąpienie szablonu, nigdy nie są zdiagnozować błędy.

Inny wpływ to zachowanie jest w przeciążeniu rozdzielczości. Ze względu na sposób, w jaki strumień tokenu jest rozwinięty w lokacji utworzenia wystąpienia symbole, które nie były widoczne w deklaracji szablonu mogą być widoczne w punkcie tworzenia wystąpienia i uczestniczy w przeciążeniu rozdzielczości. Może to prowadzić do zmiany zachowania na podstawie kodu, który nie był widoczny, gdy szablon został zdefiniowany, w przeciwieństwie do standardowych szablonów.

Na przykład, rozważmy ten kod:

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main()
{
    g(3.14);
}
```

Podczas kompilowania w ramach **/Zc:twoPhase-**, ten program wyświetli "wywołanie jest rozpoznawana jako int". W trybie zgodności w obszarze **/ permissive-**, ten program wyświetli "wywołanie jest rozpoznawany jako void *", ponieważ drugi przeciążenia `func` nie jest widoczny, gdy kompilator napotka szablonu.

*Nazwy zależne*, w przypadku nazw, które są zależne od parametru szablonu, obowiązują zachowania wyszukiwania, która różni się również w obszarze **/Zc:twoPhase-**. W trybie zgodności nazwy zależne nie są powiązane w punkcie definicji szablonu. Zamiast tego te nazwy są wyszukiwane przy tworzeniu wystąpienia szablonu. Dla wywołań funkcji o nazwie funkcji zależnych nazwa jest powiązany zestaw funkcji, które są widoczne w punkcie połączenia w definicji szablonu, jak powyżej. W punkcie definicji szablonu i punkt, gdzie konkretyzacji szablonu są dodawane dodatkowe przeciążenia z wyszukiwania zależnego od argumentów. W dwóch fazach dwufazowe wyszukiwanie są wyszukiwanie zależne od innych nazw w czasie definicji szablonu i wyszukiwania dla nazwy zależne w momencie konkretyzacji szablonu. W obszarze **/Zc:twoPhase-**, kompilator nie wyszukiwania zależnego od argumentów oddzielnie od zwykłych, niekwalifikowane wyszukiwania (czyli nie robi dwufazowe wyszukiwanie), dlatego wyniki funkcja rozpoznawania przeciążeń może różnić się.

Oto inny przykład:

```cpp
// zctwophase1.cpp
// Compile by using
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

Gdy kompilowany bez **/Zc:twoPhase-**, drukowania

```Output
func(long)
NS::func(NS::S)
```

Gdy skompilowano z opcją **/Zc:twoPhase-**, drukowania

```Output
func(int)
NS::func(NS::S)
```

W trybie zgodności w obszarze **/ permissive-**, wywołanie `tfunc(1729)` jest rozpoznawana jako `void func(long)` przeciążenia nie `void func(int)` przeciążenia zgodnie z sekcją **/Zc:twoPhase-**, ponieważ niekwalifikowanej `func(int)` jest zadeklarowana po definicji szablonu i nie można odnaleźć za pomocą wyszukiwania zależnego od argumentów. Ale `void func(S)` uczestniczyć w wyszukiwania zależnego od argumentów, aby dodać go do przeciążenia, ustaw dla wywołania `tfunc(s)` nawet, jeśli jest on zadeklarowany po funkcji szablonu.

### <a name="update-your-code-for-two-phase-conformance"></a>Zaktualizuj swój kod pod kątem zgodności dwufazowe

Starsze wersje kompilatora nie wymagają słowa kluczowe `template` i `typename` wszędzie, gdzie C++ Standard wymaga ich. Te słowa kluczowe są wymagane w niektórych pozycji do odróżniania, jak przeanalizować zależna nazwa w pierwszej fazie wyszukiwania kompilatory. Na przykład:

`T::Foo<a || b>(c);`

Odpowiadające kompilator analizuje `Foo` jako zmienne w zakresie `T`, co oznacza ten kod jest wartość logiczna — lub wyrażenie o `T::foo < a` jako lewy operand i `b > (c)` jako prawy operand. Jeśli chcesz użyć `Foo` jako szablon funkcji, należy wskazać, że jest to szablon, dodając `template` — słowo kluczowe:

`T::template Foo<a || b>(c);`

W wersjach wcześniejszych niż Visual Studio 2017 w wersji 15.3 i kiedy **/Zc:twoPhase-** jest określony, kompilator umożliwi ten kod bez `template` — słowo kluczowe i interpretuje ją jako wywołanie funkcji szablonu z nieprawidłowym argumentem `a || b`, ponieważ jej analizuje szablonów w sposób bardzo ograniczona. Powyższy kod nie jest analizowana w ogóle w pierwszej fazie. W drugiej fazie jest wystarczający kontekst, aby sprawdzić `T::Foo` jest szablon, a nie zmienną, dzięki czemu kompilator nie wymusza użycie słowa kluczowego.

To zachowanie można także zobaczyć, eliminując słowa kluczowego `typename` przed nazwy w treści szablonu funkcji, inicjatory, argumenty domyślne i noexcept argumentów. Na przykład:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Jeśli nie używasz słowa kluczowego `typename` w treści funkcji, ten kod jest kompilowany w obszarze **/Zc:twoPhase-**, ale nie w obszarze **/ permissive-**. `typename` — Słowo kluczowe jest wymagany w celu wskazania, że `TYPE` jest zależny. Ponieważ treść nie jest analizowana w obszarze **/Zc:twoPhase-**, kompilator hierarchyinfoguid nie jest wymagane słowa kluczowego. W **/ permissive-** tryb zgodności, kod bez `typename` — słowo kluczowe generuje błędy. Migrowanie kodu programu Visual Studio 2017 w wersji 15.3 i Wstaw, `typename` słowa kluczowego, w którym jest Brak.

Podobnie należy wziąć pod uwagę ten przykładowy kod:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

W obszarze **/Zc:twoPhase-** i w starszych kompilatory, kompilator wymaga on tylko `template` — słowo kluczowe w wierszu 2. Domyślnie, a w trybie zgodności, kompilator teraz wymaga również `template` — słowo kluczowe w wierszu 4, aby wskazać, że `T::X<T>` jest szablonem. Wyszukaj kod, który nie ma to słowo kluczowe i dostarczenia go do kodu są zgodne ze standardem.

Aby uzyskać więcej informacji na temat problemów ze zgodnością, zobacz [ulepszenia zgodności języka C++ w programie Visual Studio](../../cpp-conformance-improvements-2017.md) i [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc:twoPhase-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
