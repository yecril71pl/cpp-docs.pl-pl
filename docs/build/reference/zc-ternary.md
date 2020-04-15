---
title: /Zc:ternary (Wymuszenie reguł operatora warunkowego)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335675"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (Wymuszenie reguł operatora warunkowego)

Włącz wymuszanie reguł standardu C++ dla typów i konsytów lub zmiennych (cv) kwalifikacji drugiego i trzeciego argumentów w wyrażeniu operatora warunkowego.

## <a name="syntax"></a>Składnia

> **/Zc:ternary****-**[ ]

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2017 kompilator obsługuje zachowanie standardowego *operatora warunkowego* języka C++ (**?:**). Jest również znany jako *operator trójskładnikowy.* Standard C++ wymaga, aby trójskładniowe operandy spełniały jeden z trzech warunków: argumenty muszą być tego samego typu i **zgodne** lub **niestabilne** kwalifikacje (kwalifikacje cv) lub tylko jeden operand musi być jednoznacznie zamienicjonowany na ten sam typ i kwalifikację CV co drugi. Lub jeden lub oba argumenty muszą być wyrażeniem rzutu. W wersjach przed Visual Studio 2017 w wersji 15.5 kompilator dozwolone konwersje, które są uważane za niejednoznaczne przez standard.

Po określeniu opcji **/Zc:ternary** kompilator jest zgodny ze standardem. Odrzuca kod, który nie spełnia reguł dla dopasowanych typów i cv kwalifikacji drugiego i trzeciego argumentów.

**/Zc:ternary** opcja jest domyślnie wyłączona w programie Visual Studio 2017. Użyj **/Zc:ternary,** aby włączyć zachowanie zgodne lub **/Zc:ternary-** jawnie określić poprzednie zachowanie kompilatora niezgodnego. Opcja [/permissive-](permissive-standards-conformance.md) niejawnie włącza tę opcję, ale można ją zastąpić za pomocą **/Zc:ternary-**.

### <a name="examples"></a>Przykłady

W tym przykładzie pokazano, jak klasa, która zapewnia zarówno jawne inicjowanie z typu, jak i konwersję na typ, może prowadzić do niejednoznacznych konwersji. Ten kod jest domyślnie akceptowany przez kompilator, ale odrzucany, gdy określono **wartość /Zc:ternary** lub **/permissive.This** code is accepted by the compiler by default, but rejected when /Zc:ternary or /permissive- is specified.

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

Aby naprawić ten kod, należy jawnie rzutować do preferowanego typu wspólnego lub zapobiec jeden kierunek konwersji typu. Kompilator można zachować z dopasowania konwersji typu przez konwersji jawne.

Ważnym wyjątkiem od tego wspólnego wzorca jest, gdy typ argumentów jest jednym z `const char*`typów `const char16_t*`ciągów zakończonych z wartością null, takich jak , i tak dalej. Można również odtworzyć efekt z typów tablic i typów wskaźników, które rozpadają się do. Zachowanie, gdy rzeczywisty drugi lub `?:` trzeci operand jest literał ciągu odpowiedniego typu zależy od standardu języka używane. C++ 17 zmienił semantykę w tym przypadku z C++14. W rezultacie kompilator akceptuje kod w poniższym przykładzie w obszarze domyślny **/std:c++14**, ale odrzuca go po określeniu **/std:c++17**.

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

Aby naprawić ten kod, należy wyraźnie odrzucić jeden z argumentów.

W **obszarze /Zc:ternary**kompilator odrzuca operatory warunkowe, w których jeden z argumentów jest **typu void**, a drugi nie jest wyrażeniem throw. Typowe zastosowanie tego wzorca jest w makrach podobnych do ASSERT:

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

Typowym rozwiązaniem jest zastąpienie argumentu `void()`nieustąpkią argumentem .

W tym przykładzie pokazano kod, który generuje błąd w obszarze **/Zc:ternary** i **/Zc:ternary-**:

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

Ten kod wcześniej dał ten błąd:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Z **/Zc:ternary**, przyczyna awarii staje się jaśniejsza. Dowolna z kilku konwencji wywołujących zdefiniowanych w implementacji może służyć do generowania każdego lambda. Jednak kompilator nie ma reguły preferencji, aby odróżnić możliwe podpisy lambda. Nowe dane wyjściowe wyglądają następująco:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Typowe źródło problemów znalezionych przez **/Zc:ternary** pochodzi z operatorów warunkowych używanych w meta-programowania szablonu. Niektóre typy wyników zmieniają się w ramach tego przełącznika. W poniższym przykładzie przedstawiono dwa przypadki, w których **/Zc:ternary** zmienia typ wyniku wyrażenia warunkowego w kontekście nie-meta-programowania:

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

Typową poprawką jest `std::remove_reference` zastosowanie cechy na typ wyniku, gdzie jest to konieczne, aby zachować stare zachowanie.

Aby uzyskać więcej informacji na temat problemów z zgodnością w programie Visual C++, zobacz [Niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę właściwości**wiersza polecenia** **Właściwości** > konfiguracji**C/C++.** > 

1. Zmodyfikuj właściwość **Opcje dodatkowe,** aby uwzględnić **/Zc:ternary** lub **/Zc:ternary-** a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[/Zc (Zgodność)](zc-conformance.md)
