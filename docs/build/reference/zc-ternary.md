---
title: '/ Zc: ternary (wymuszenie reguł operatora warunkowego)'
ms.date: 3/06/2018
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: cb9a4f8468a9cb57af711cdca36ee343e5092493
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816493"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/ Zc: ternary (wymuszenie reguł operatora warunkowego)

Włącz wymuszanie reguły C++ Standard dla typów i const lub volatile kwalifikacji (cv) drugiego i trzeciego operandu w wyrażeniu operator warunkowy.

## <a name="syntax"></a>Składnia

> **/ Zc: ternary**[**-**]

## <a name="remarks"></a>Uwagi

Visual Studio w wersji 15.3 włączenie obsługi kompilatora C++ standardowy operator warunkowy (lub trójargumentowy) (**?:**) zachowanie. C++ Standard wymaga argumentów tego samego typu i stałych nietrwałych kwalifikacji lub tylko jeden argument jako jednoznacznie konwertowane do tego samego typu i stałych nietrwałych kwalifikacji, co inne lub jeden lub obydwa operandy jako wyrażenie throw. W wersjach starszych niż wersja 15.5 programu Visual Studio kompilator może konwersje, które są traktowane jako niejednoznaczny przez standard. Gdy **/Zc: ternary** opcja zostanie określona, kompilator jest zgodny ze standardem i odrzuca kod, który nie spełnia warunków reguły dla typów dopasowane i stałych nietrwałych kwalifikacji drugi i trzeci operand.

**/Zc: ternary** opcja jest domyślnie wyłączona. Użyj **/Zc: ternary** Aby włączyć odpowiadające zachowanie lub **/Zc:ternary-** jawnie określić poprzednie zachowanie kompilatora niezgodnych. [/ Permissive-](permissive-standards-conformance.md) opcji niejawnie włączy tę opcję, ale może być zastąpiona przy użyciu **/Zc:ternary-**.

### <a name="examples"></a>Przykłady

Niniejszy przykład pokazuje, jak klasa, która zawiera zarówno inicjowania niejawnego typu i konwersji do typu może prowadzić do niejednoznaczne. Ten kod jest akceptowany przez kompilator domyślnie, ale kiedy odrzucone **/Zc: ternary** lub **/ permissive-** jest określony.

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

Wymaganej poprawce jest dokonać jawnego rzutowania preferowany typ wspólny lub uniemożliwić jeden kierunek konwersji z uczestnictwa w polu wyszukiwania kompilatora dopasowanie typu, wprowadzając jawnej konwersji.

Wyjątek ważne, aby ten typowy wzorzec jest, gdy typ operandu to jeden z typów ciąg zakończony znakiem null, takie jak `const char*`, `const char16_t*`i tak dalej. Można również odtworzyć to typy tablic i typy wskaźników, które one decay do. Zachowanie podczas rzeczywistego drugi lub trzeci operand do?: jest odpowiedni typ literału ciągu jest zależna od standardowy język używany. C ++ 17 zmianie uległa semantyki dla tego przypadku C ++ 14. W rezultacie kod w poniższym przykładzie jest akceptowany w obszarze **/STD: c ++ 14** (domyślna wartość kompilatora), ale jest odrzucane, gdy **/STD: c ++ 17** jest określony.

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

Aby rozwiązać ten kod, oddać jeden z argumentów jawnie.

W obszarze **/Zc: ternary**, operatorów warunkowych odrzutów kompilatora, gdy jeden z argumentów jest typu void, a druga nie jest wyrażeniem throw. Typowym zastosowaniem tych znajduje się w makra ASSERT podobne:

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

Typowym rozwiązaniem jest po prostu zastąpić argumentów niż void void().

W tym przykładzie przedstawiono kod, który generuje błąd w obu **/Zc: ternary** i **/Zc:ternary-**:

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

Ten kod wydał wcześniej ten błąd:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Za pomocą **/Zc: ternary** przyczynę niepowodzenia staje się bardziej zrozumiały; w architekturach, gdzie dowolnego z kilku konwencji wywoływania zdefiniowanych w implementacji może służyć do generowania każdego lambda, kompilator określa Brak preferencji między nimi który można odróżnić podpisów możliwe lambda. Nowe dane wyjściowe wyglądają następująco:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Wspólne źródło problemy związane z przyjęcia **/Zc: ternary** pochodzi z użycia operatora warunkowego w szablonie meta-programowania, jak zmienić się niektóre typy wyników w ramach tego przełącznika. W poniższym przykładzie pokazano dwa przypadki gdzie **/Zc: ternary** zmieni typ wyniku wyrażenia warunkowego, w kontekście meta programowania:

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

Typowe rozwiązania w takich przypadkach polega na zastosowaniu `std::remove_reference` cech dla wyniku typu w przypadku, gdy spełnione, aby zachować stare zachowanie.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: ternary** lub **/Zc:ternary-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
