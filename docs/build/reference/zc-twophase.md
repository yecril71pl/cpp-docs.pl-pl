---
title: /Zc:twoPhase-(Wyłącz wyszukiwanie nazw dwufazowego) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5653959b25105f10ae98768217524dc0ff0cbe2a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389104"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(Wyłącz wyszukiwanie nazw dwufazowego)

Gdy **/Zc:twoPhase-** zostanie określona opcja, kompilator analizuje i tworzy wystąpienie klasy szablony i funkcji w taki sam sposób niezgodnych jako wersje programu Visual Studio przed Visual Studio 2017 wersji 15 ustęp 3. 

## <a name="syntax"></a>Składnia

> **/Zc:twoPhase-**

## <a name="remarks"></a>Uwagi

W Visual Studio 2017 wersji 15.3 i nowsze, domyślnie kompilator używa wyszukiwanie nazw dwufazowego do rozpoznawania nazw szablonu. Jeśli **/Zc:twoPhase-** jest określony, kompilator powraca do jego poprzedniego niezgodnych klasy szablonu i funkcja szablonu rozdzielczość i podstawienia nazw.

**/Zc:twoPhase-** nie ustawiono opcję, aby włączyć niezgodnych zachowanie domyślne. [/ Ograniczająca-](permissive-standards-conformance.md) opcji niejawnie ustawia zgodnych zachowanie kompilatora dwufazowego wyszukiwania, ale może być zastąpiona przy użyciu **/Zc:twoPhase-**.

Pliki nagłówka zestawu Windows SDK w wersji 10.0.15063.0 (twórców aktualizacji lub Redstone 2) i starszych wersji nie działają prawidłowo w trybie zgodności. Należy użyć **/Zc:twoPhase-** skompilować kod dla tych wersji zestawu SDK podczas korzystania z wersji programu Visual Studio 2017 15 ustęp 3 i nowszych wersjach. Wersje zestawu SDK systemu Windows, począwszy od wersji 10.0.15254.0 (Redstone 3 lub aktualizacji twórców spadek) działają prawidłowo w trybie zgodności i nie wymagają **/Zc:twoPhase-** opcji.

Użyj **/Zc:twoPhase-** Jeśli kod wymaga starego zachowania do poprawnej kompilacji. Zdecydowanie może być konieczna aktualizacja swój kod, aby był zgodny ze standardowego.

### <a name="compiler-behavior-under-zctwophase-"></a>Zachowanie kompilatora w obszarze /Zc:twoPhase-

W wersji kompilatora przed Visual Studio 2017 15 ustęp 3, wersja i kiedy **/Zc:twoPhase-** określono kompilator używa tego zachowania:

- Analizuje tylko deklaracji szablonu, head klasy i liście klas podstawowych. Treść szablonu jest przechwytywany jako strumień tokenu. Nie ciało funkcji, inicjatory, argumenty domyślne lub noexcept argumenty są parsowane. Szablon klasy jest tworzone pseudo w wstępnie typ, aby sprawdzić, czy deklaracje w szablonie klasy są poprawne. Należy wziąć pod uwagę tego szablonu klasy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Deklaracja szablonu `template <typename T`>, head klasy `class Derived`, liście klasy podstawowej i `public Base<T>` przeanalizować, ale treści szablonu jest przechwytywany jako strumień tokenu.

- Podczas analizowania szablonu funkcji, kompilator analizuje tylko sygnatura funkcji. Nigdy nie jest analizowana z treści funkcji. Zamiast tego jest przechwytywany jako strumień tokenu.

W związku z tym treści szablonu zawiera błędy składni szablonu nigdy nie zostanie uruchomiony, nigdy nie są zdiagnozowaniu błędów.

Inny wpływ to zachowanie jest rozpoznanie przeciążenia. Ze względu na sposób strumień tokenu jest rozwinięta w witrynie wystąpienia symbole, które nie były widoczne w deklaracji szablonu mogą być widoczne w punkcie wystąpienia i brać udziału w Rozpoznanie przeciążenia. Może to prowadzić do szablonów, które należy zmienić to zachowanie na podstawie kodu, który nie był widoczny, gdy szablon został zdefiniowany w przeciwieństwie do standardowego.

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

Podczas kompilacji w obszarze **/Zc:twoPhase-**, drukuje ten program "wywołanie jest rozpoznawana jako int". W trybie zgodności, w obszarze **/ ograniczająca-**, ten program drukuje "wywołanie jest rozpoznawany jako void *", ponieważ drugi przeciążenia z `func` nie jest widoczny, gdy kompilator napotka szablonu.

*Nazwy zależne*, nazwy, które są zależne od parametru szablonu, mają zachowanie wyszukiwania, która różni się również w obszarze **/Zc:twoPhase-**. W trybie zgodności nazwy zależne nie są powiązane w punkcie definicji szablonu. Zamiast tego te nazwy są wyszukiwane przy tworzeniu wystąpienia szablonu. Wywołania funkcji o nazwie funkcji zależnych nazwa jest powiązany zestaw funkcji, które są widoczne w punkcie połączenia w definicji szablonu, jak powyżej. Dodatkowe przeciążenia z wyszukiwania zależnego od argumentów są dodawane zarówno w punkt definicji szablonu, jak i w którym szablon zostanie uruchomiony punkt. Dwie fazy dwufazowego wyszukiwania są wyszukiwania dla nazwy zależne od innych niż w momencie definicja szablonu oraz wyszukiwania dla nazwy zależne w momencie utworzenie wystąpienia szablonu. W obszarze **/Zc:twoPhase-**, kompilator nie działa wyszukiwanie zależne od argumentów oddzielnie od zwykłej, niekwalifikowanych wyszukiwania (to znaczy nie wyszukiwania dwufazowego), więc wyniki Rozpoznanie przeciążenia mogą się różnić.

Innym przykładem jest następujący:

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

Podczas kompilacji bez **/Zc:twoPhase-**, drukowania

```Output
func(long)
NS::func(NS::S)
```

Gdy skompilowano z opcją **/Zc:twoPhase-**, drukowania

```Output
func(int)
NS::func(NS::S)
```

W trybie zgodności, w obszarze **/ ograniczająca-**, wywołanie `tfunc(1729)` jest rozpoznawana jako `void func(long)` przeciążenia nie `void func(int)` przeciążenia zgodnie z sekcją **/Zc:twoPhase-**, ponieważ niekwalifikowane `func(int)` jest zadeklarowany po definicji szablonu i nie można odnaleźć za pomocą wyszukiwania zależnego od argumentów. Ale `void func(S)` uczestniczyć w wyszukiwania zależnego od argumentów, aby dodać go do przeciążenia, ustaw dla wywołania `tfunc(s)` nawet, jeśli jest on zadeklarowany jako po funkcji szablonu.

### <a name="update-your-code-for-two-phase-conformance"></a>Zaktualizuj kod dla zgodność dwufazowego

Starsze wersje kompilatora nie wymagają słowa kluczowe `template` i `typename` wszędzie C++ Standard wymaga ich. Słowa kluczowe są potrzebne w niektórych pozycji do odróżniania jak przeanalizować zależna nazwa w pierwszej fazie wyszukiwania kompilatory. Na przykład:

`T::Foo<a || b>(c);`

Analizuje zgodnych kompilatora `Foo` jako zmiennej w zakresie `T`, co oznacza ten kod jest logiczną — lub wyrażenie z `T::foo < a` jako lewy operand i `b > (c)` jako prawy argument operacji. Jeśli chcesz użyć `Foo` jako szablon funkcji musi wskazać, że jest to szablon, dodając `template` — słowo kluczowe:

`T::template Foo<a || b>(c);`

W wersjach wcześniejszych niż Visual Studio 2017 15 ustęp 3, wersja i kiedy **/Zc:twoPhase-** określono kompilator umożliwia tego kodu bez `template` — słowo kluczowe i interpretuje ją jako wywołania z argumentem szablonufunkcji`a || b`, ponieważ analizuje szablonów w sposób bardzo ograniczone. Powyższy kod nie jest analizowana w ogóle w pierwszej fazie. W drugiej fazie jest wystarczający kontekst stwierdzić, że `T::Foo` jest szablonu, a nie w zmiennej, dlatego kompilator nie wymusza użycie słowa kluczowego.

To zachowanie można także znaleźć przez wyeliminowanie kluczowego `typename` przed nazwy w treści szablonu funkcji, inicjatory argumenty domyślne i noexcept argumentów. Na przykład:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Jeśli nie należy używać słowa kluczowego `typename` w treści funkcji ten kod kompiluje w obszarze **/Zc:twoPhase-**, ale nie w obszarze **/ ograniczająca-**. `typename` — Słowo kluczowe jest wymagany w celu wskazania, że `TYPE` jest zależna. Ponieważ treść nie jest analizowana w obszarze **/Zc:twoPhase-**, słowo kluczowe wymagają does't kompilatora. W **/ ograniczająca-** trybu zgodności, kod bez `typename` — słowo kluczowe generuje błędy. Aby przeprowadzić migrację kodu do programu Visual Studio 2017 wersji 15 ustęp 3 i nowszych, Wstaw `typename` — słowo kluczowe, gdy jest on niedostępny.

Podobnie należy wziąć pod uwagę ten przykład kodu:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

W obszarze **/Zc:twoPhase-** i w starszych kompilatory wymaga tylko kompilator `template` — słowo kluczowe w wierszu 2. Domyślnie, a w trybie zgodności, kompilator teraz wymaga również `template` — słowo kluczowe w wierszu 4, aby wskazać, że `T::X<T>` jest szablonem. Poszukaj kodu, który nie ma to słowo kluczowe i dostarczenia go do uczynienia kodu są zgodne ze standardem.

Aby uzyskać więcej informacji dotyczących zgodności, zobacz [ulepszenia zgodność języka C++ w programie Visual Studio](../../cpp-conformance-improvements-2017.md) i [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:twoPhase-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
