---
title: /Zc:ternary (wymuszanie zasad operator warunkowy) | Dokumentacja firmy Microsoft
ms.date: 1/12/2018
ms.technology: cpp-tools
ms.topic: article
f1_keywords: /Zc:ternary
dev_langs: C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2c4f4e17d3cf72284ec68cf10e75824722d5440
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (wymuszanie zasad operator warunkowy)

Włącz wymuszania reguł C++ Standard dla typów i const lub volatile kwalifikacji (cv), drugi i trzeci operandów w wyrażeniu operator warunkowy.

## <a name="syntax"></a>Składnia

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>Uwagi

Visual Studio w wersji 15 ustęp 3 umożliwia obsługę kompilatora C++ standardowy operator warunkowy (lub trójargumentowy) (**?:**) zachowanie. C++ Standard wymaga operandy tego samego typu i cv kwalifikacji lub tylko jeden operand być jednoznacznie do przekonwertowania na tym samym typie i cv kwalifikacji co inne lub jeden lub obydwa argumenty operacji jako wyrażenie throw. W wersjach przed Visual Studio wersja 15,5 cala kompilator może konwersje, które są traktowane jako niejednoznaczne przez standard. Gdy **/Zc:ternary** zostanie określona opcja, kompilator jest zgodny ze standardem i odrzuca kod, który nie spełnia warunków reguły pasujących typów i cv kwalifikacji drugiego i trzeciego argumentu operacji.

**/Zc:ternary** opcja jest domyślnie wyłączona. Użyj **/Zc:ternary** umożliwia zachowanie zgodnych lub **/Zc:ternary-** Aby jawnie określić poprzedniej zachowanie kompilatora niezgodnych. [/ Ograniczająca-](permissive-standards-conformance.md) powoduje włączenie **/Zc:ternary**. 

### <a name="examples"></a>Przykłady

W tym przykładzie pokazano, jak klasy, która zapewnia zarówno-Jawne inicjowanie z typu i konwersji do typu może prowadzić do konwersje niejednoznaczne. Ten kod jest akceptowane przez kompilator domyślnie, ale odrzucone podczas **/Zc:ternary** lub **/ ograniczająca-** jest określona.

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

Wymagane będzie jawnego rzutowania preferowany typ wspólnej lub uniemożliwić jeden kierunek konwersji z uczestnictwa w wyszukiwaniu kompilatora dopasowanie typu dokonując jawnej konwersji.

Wyjątek tego wspólnego wzorca ważne jest, gdy typ operandy to jeden z typów zerem ciągu, takich jak `const char*`, `const char16_t*`i tak dalej. Można to również odtworzyć z typami tablicy z typów wskaźnika, które są decay — do. Zachowanie podczas rzeczywistego drugiego i trzeciego argumentu?: jest literału ciągu odpowiedniego typu zależy od języka standardowe. C ++ 17 zmieniła semantyki dla tego przypadku C ++ 14. W związku z tym kod w poniższym przykładzie jest akceptowany w obszarze **/std:c ++ 14** (domyślnie kompilatora), ale jest odrzucone podczas **/std:c ++ 17** jest określona.

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

W obszarze **/Zc:ternary**, operatorów warunkowych odrzuca kompilatora, gdy jeden z argumentów jest typu void i innych nie jest wyrażeniem rzutowania. Typowym zastosowaniem tych ma makra przypominającej potwierdzenia:

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

Typowe rozwiązania jest po prostu zastąpić void() argument inny niż void.

W tym przykładzie pokazano kod, który generuje błąd w obu **/Zc:ternary** i **/Zc:ternary-**:

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

Z **/Zc:ternary** przyczynę niepowodzenia staje się jaśniejszy; na architektury, gdzie jedną z kilku zdefiniowane w implementacji konwencji wywoływania może służyć do wygenerowania każdego lambda, kompilator nie określa żadnych preferencji między nimi który może odróżnić podpisów możliwe lambda. Nowe dane wyjściowe wygląda następująco:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Wspólne źródło problemów związanych z przyjęcia **/Zc:ternary** pochodzi z użycia operator warunkowy w szablonie meta-programowania, jak zmienić niektóre typy wyników w obszarze ten przełącznik. W poniższym przykładzie pokazano dwa przypadki gdzie **/Zc:ternary** zmiany typu wyniku wyrażenia warunkowego w kontekście meta programowania:

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

Typowe rozwiązania w takich przypadkach stosuje się `std::remove_reference` cechy wyniku wpisz w razie potrzeby, aby zachować poprzednie działanie.

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:ternary** lub **/Zc:ternary-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)  
