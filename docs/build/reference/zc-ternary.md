---
title: /Zc:ternary (Wymuszenie reguł operatora warunkowego)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 04bd0c49528d86ddd4d1e6c77804cf64278db188
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211882"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary`(Wymuszaj reguły operatora warunkowego)

Włącz wymuszanie standardowych reguł języka C++ dla kwalifikacji typów i const lub volatile (CV) dla drugiego i trzeciego operandu w wyrażeniu operatora warunkowego.

## <a name="syntax"></a>Składnia

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2017, kompilator obsługuje zachowanie *operatora warunkowego* standardowego języka C++ ( **`?:`** ). Jest on również znany jako *operator Trzyelementowy*. Standard języka C++ wymaga, aby argumenty operacji trójskładnikowych spełniały jeden z trzech warunków: operandy muszą być tego samego typu **`const`** i **`volatile`** kwalifikacji (CV-kwalifikacja) lub tylko jeden operand musi być jednoznacznie konwertowany na taki sam typ, jak i OKS. Lub, jeden lub oba operandy muszą być wyrażeniem throw. W wersjach wcześniejszych niż wersja 15,5 programu Visual Studio 2017 kompilator zezwolił na konwersje, które są uważane za niejednoznaczne przez Standard.

Gdy ta **`/Zc:ternary`** opcja jest określona, kompilator jest zgodny ze standardem. Odrzuci kod, który nie spełnia reguł dla dopasowanych typów oraz kwalifikacji CV dla drugiego i trzeciego operandu.

**`/Zc:ternary`** Opcja jest domyślnie wyłączona w programie Visual Studio 2017. Użyj **`/Zc:ternary`** , aby włączyć zgodność z zachowaniem lub **`/Zc:ternary-`** jawnie określić poprzednie zachowanie kompilatora niezgodnego. [`/permissive-`](permissive-standards-conformance.md)Opcja ta umożliwia niejawnie włączenie tej opcji, ale można ją zastąpić za pomocą polecenia **`/Zc:ternary-`** .

### <a name="examples"></a>Przykłady

Ten przykład pokazuje, jak Klasa, która zapewnia zarówno inicjalizację niejawną z typu, jak i konwersję na typ, może prowadzić do niejednoznacznych konwersji. Ten kod jest domyślnie akceptowany przez kompilator, ale jest odrzucany, gdy **/`Zc:ternary`** lub **`/permissive-`** jest określony.

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

Aby naprawić ten kod, należy jawnie rzutować na preferowany typ wspólny lub uniemożliwić jednokierunkową konwersję typu. Kompilator może być zgodny z konwersją typu, ponieważ konwersja jest jawna.

Ważnym wyjątkiem od tego wspólnego wzorca jest, gdy typ operandów jest jednym z typów ciągów zakończonych wartością null, takich jak `const char*` , `const char16_t*` , i tak dalej. Możesz również odtworzyć efekt przy użyciu typów tablic i typów wskaźnika, do których się zanikają. Zachowanie, gdy faktyczny drugi lub trzeci operand `?:` jest literałem ciągu odpowiadającego typu, zależy od użytego standardu języka. W języku c++ 17 zmieniono semantykę w tym przypadku w języku C++ 14. W związku z tym kompilator akceptuje kod w poniższym przykładzie pod wartością domyślną **`/std:c++14`** , ale odrzuca go po określeniu **`/std:c++17`** .

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

Aby naprawić ten kod, Rzutowanie jednego z operandów jawnie.

W obszarze **`/Zc:ternary`** , kompilator odrzuca operatory warunkowe, gdy jeden z argumentów jest typu **`void`** , a drugi nie jest **`throw`** wyrażeniem. Typowym zastosowaniem tego wzorca jest w makrach przypominających podobne:

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

Typowym rozwiązaniem jest zamienienie argumentu innego niż void na `void()` .

Ten przykład pokazuje kod, który generuje błąd w obu **`/Zc:ternary`** **`/Zc:ternary-`** :

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

Ten kod spowodował wcześniej ten błąd:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

W programie **`/Zc:ternary`** Przyczyna niepowodzenia zostaje wyczyszczona. Do wygenerowania każdego wyrażenia lambda można użyć dowolnej z kilku konwencji wywoływania zdefiniowanych w implementacji. Jednak kompilator nie ma reguły preferencji, aby odróżnić możliwe sygnatury lambda. Nowe dane wyjściowe wyglądają następująco:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Typowym źródłem problemów wykrytym przez program są **`/Zc:ternary`** Operatory warunkowe używane w ramach tworzenia meta-programistycznego szablonu. Niektóre typy wyników zmieniają się w ramach tego przełącznika. Poniższy przykład ilustruje dwa przypadki, **`/Zc:ternary`** w których zmiany typu wyniku wyrażenia warunkowego w kontekście niemeta-programowaniu:

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

Typowym rozwiązaniem jest zastosowanie `std::remove_reference` cech typu wyników, gdy jest to konieczne, aby zachować stare zachowanie.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **`/Zc:ternary`** lub **`/Zc:ternary-`** , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[`/Zc`Zgodności](zc-conformance.md)
