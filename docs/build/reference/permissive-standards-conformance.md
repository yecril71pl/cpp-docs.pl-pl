---
title: -ograniczająca - (standardów zgodność) | Dokumentacja firmy Microsoft
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs:
- C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cfdcf20cf74244afe026a392759ac59616bbdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379318"
---
# <a name="permissive--standards-conformance"></a>/ ograniczająca-(standardów zgodność)

Określ tryb zgodności standardów do kompilatora. Użyj tej opcji, aby zidentyfikować i rozwiązać problemy z zgodność w kodzie, aby umożliwić zarówno więcej poprawne i przenośną.

## <a name="syntax"></a>Składnia

> **/ ograniczająca-**

## <a name="remarks"></a>Uwagi

Można użyć **/ ograniczająca-** opcję kompilatora, aby określić zachowanie kompilatora zgodnych standardów. Ta opcja powoduje wyłączenie ograniczająca zachowania i ustawia [/Zc](../../build/reference/zc-conformance.md) opcje kompilatora, aby uzyskać pełną zgodność. W środowisku IDE ta opcja powoduje aparat podkreślenie niezgodnych kodu IntelliSense.

Domyślnie **/ ograniczająca-** opcja jest ustawiona w nowych projektach utworzone przez wersji programu Visual Studio 2017 15,5 cala i nowszych wersji. Nie jest ustawiona domyślnie we wcześniejszych wersjach. Gdy ustawiono opcję, kompilator generuje diagnostycznych błędy lub ostrzeżenia, gdy język niestandardowej konstrukcje zostaną wykryte w kodzie, w tym niektórych typowych błędów w wersji pre-C ++ 11 kodu.

**/ Ograniczająca-** opcji jest zgodny z prawie wszystkie pliki nagłówka z najnowszą Kit systemu Windows, takich jak Software Development Kit (SDK) lub Windows Driver Kit (WDK), począwszy od systemu Windows spadek twórców SDK (10.0.16299.0). Starsze wersje zestawu SDK może zakończyć się niepowodzeniem do skompilowania w obszarze **/ ograniczająca-** różne źródła kodu zgodność powodów. Kompilator i zestawy SDK wysyłki na osiach czasu inną wersję, w związku z tym istnieją problemy, pozostałe. Dla określonego nagłówka pliku problemów, zobacz [problemy nagłówka Windows](#windows-header-issues) poniżej.

**/ Ograniczająca-** opcję zestawy [/Zc: strictstrings](../../build/reference/zc-conformance.md) i [/Zc: rvaluecast](../../build/reference/zc-conformance.md) opcje do zachowania zgodności. One domyślne zachowanie niezgodnych. Można przekazać określonego **/Zc** opcje po **/ ograniczająca-** w wierszu polecenia, aby zmienić to zachowanie.

W wersji kompilatora, począwszy od programu Visual Studio 2017 wersji 15 ustęp 3 **/ ograniczająca-** opcję zestawy [/Zc:ternary](../../build/reference/zc-ternary.md) opcji. Kompilator implementuje więcej wymagania dotyczące dwufazowego nazwę wyszukiwania. Gdy **/ ograniczająca-** jest ustawiona opcja, kompilator analizuje funkcji i klasa definicje szablonów identyfikacji nazwy zależne i zależne od innych niż używane w szablonach. W tej wersji odbywa się tylko nazwa analizy zależności.

Rozszerzenia określonego środowiska i obszary języka standardowego pozostawia do wykonania nie dotyczy **/ ograniczająca-**. Na przykład specyficzne dla firmy Microsoft `__declspec`, konwencja wywołania i wyjątków strukturalnych obsługi słów kluczowych i dyrektywy pragma specyficznych dla kompilatora lub atrybutów nie są oznaczone za pomocą kompilatora w **/ ograniczająca-** tryb.

**/ Ograniczająca-** opcja używa Obsługa zgodności ze standardem w bieżącej wersji kompilatora w celu określenia, które konstrukcji języka są niezgodne. Opcja nie określa, jeśli kod jest zgodny z określoną wersją C++ standard. Aby włączyć wszystkie zaimplementowane kompilatora obsługę standardu najnowszą wersję roboczą, należy użyć [/std:latest](../../build/reference/std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługa kompilatora do aktualnie zaimplementowana standardzie C ++ 17, użyj [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługa kompilatora, aby lepiej dopasować 14 standardu C ++, użyj [/std:c ++ 14](../../build/reference/std-specify-language-standard-version.md) opcja, która jest ustawiona domyślnie.

Nie wszystkie C ++ 11, języka C ++ 14 lub C ++ 17 zgodnych standardów kodu jest obsługiwana przez kompilator języka Visual C++ w programie Visual Studio 2017 r. **/ Ograniczająca-** opcji mogą nie zostać wykryte problemy dotyczące niektórych aspektów wyszukiwanie nazw dwufazowego, powiązanie z systemem innym niż stała odwołanie do tymczasowej, traktowanie init kopiowania jako bezpośrednie init, umożliwiającą wielu konwersje zdefiniowane przez użytkownika w Inicjowanie lub alternatywne tokeny dla operatorów logicznych i innych obszarach zgodność z systemem innym niż obsługiwany. Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="how-to-fix-your-code"></a>Jak rozwiązać kodu

Oto kilka przykładów kodu, który zostanie wykryte niezgodnych korzystając z **/ ograniczająca-**, wraz z sugerowanych sposobów, aby rozwiązać problemy.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Użyj domyślnej jako identyfikatora w kodzie natywnym

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Elementy członkowskie wyszukiwania w podstawowym zależne

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Użyj nazwy kwalifikowane w deklaracji elementu członkowskiego

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicjowanie wielu elementów członkowskich Unii w inicjatorze elementu członkowskiego

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Ukryte przyjazne nazwy wyszukiwania reguł

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Użyj wyliczenia w zakresie w granice tablicy

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Użyj dla każdej z nich w kodzie natywnym

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Korzystanie z atrybutów ATL

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be 
// used to automatically obtain a *.idl file for the interfaces with 
// annotation. Second, add a midl step to your build system to make 
// sure that the C++ interface definitions are outputted. 
// Last, adjust your existing code to use ATL directly as shown in 
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Niejednoznaczny operator warunkowy argumentów

W wersjach kompilatora przed Visual Studio 2017 wersji 15 ustęp 3, kompilator zaakceptowane argumenty operator warunkowy (lub trójargumentowy) `?:` uznane niejednoznaczne przez Standard. W **/ ograniczająca-** trybie kompilator generuje teraz co najmniej jeden diagnostyki w przypadkach, w których skompilowany bez diagnostyki we wcześniejszych wersjach.

Typowych błędów, które mogą być wynikiem tej zmiany obejmują:

- Błąd C2593: "operator"? jest niejednoznaczny

- Błąd C2679: binarny '?': nie znaleziono żadnych operatora, który przyjmuje prawostronny operand typu "B" (lub nie jest dopuszczalne konwersja)

- Błąd C2678: binarny '?': nie znaleziono żadnych operatora, który przyjmuje lewostronny operand typu "A" (lub nie jest dopuszczalne konwersja)

- Błąd C2446: ":": Brak konwersji z "B" na "A"

Wzorzec typowy kod, który może być przyczyną tego problemu jest niektóre klasy C zapewniał i niejawnego konstruktora z innego typu T i operator niejawnej konwersji do typu T. W takim przypadku zarówno konwersja 2 argumentu typu 3rd i konwersji argumentu 3 na typ 2 są prawidłowe konwersje niejednoznacznego zgodnie ze standardowego.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Jeśli T reprezentuje jeden z typów zerem ciągu jest wyjątek ważne tego wspólnego wzorca (na przykład `const char *`, `const char16_t *`i tak dalej) i rzeczywisty argument `?:` jest ciągiem literału odpowiedniego typu. C ++ 17 zmieniła semantykę języka C ++ 14. W związku z tym kod w przykładzie 2 jest akceptowany w obszarze **/std:c ++ 14** i odrzucone w obszarze **/std:c ++ 17** podczas **/Zc:ternary** lub **/permissive-** jest używany.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s; 
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Inny przypadek, w której mogą zostać wyświetlone błędy trwa operatorów warunkowych z jednym argumentem typu `void`. Ten przypadek może być typowe w przypadku makra przypominającej potwierdzenia.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Mogą również zostać wyświetlone błędy w szablonie metaprogramowania, których typy wyników operator warunkowy mogą ulec zmianie w obszarze **/Zc:ternary** i **/ ograniczająca-**. Jednym ze sposobów rozwiązania tego problemu jest użycie [std::remove_reference](../../standard-library/remove-reference-class.md) na wynikowy typ.

```cpp
// Example 4: different result types 
extern bool cond;
extern int count;
char  a = 'A'; 
const char  b = 'B'; 
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary 
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary 
```

#### <a name="two-phase-name-look-up-partial"></a>Sprawdź nazwę dwufazowego (częściowe)

Gdy **/ ograniczająca-** opcja jest ustawiona w Visual Studio 2017 wersji 15 ustęp 3, kompilator analizuje funkcji i klasa definicje szablonów identyfikacji nazwy zależne i zależne od innych niż używane w szablonach zgodnie z wymaganiami dla nazwy dwufazowego wyszukiwania. W tej wersji odbywa się tylko nazwa analizy zależności. W szczególności z systemem innym niż zależne od nazw, które nie są zadeklarowane w kontekście definicji szablonu spowodować diagnostycznych komunikatu jako wymaganego normy ISO C++. Jednak powiązania z systemem innym niż zależne od nazw, które wymaga argumentu zależnych wyszukiwanie w kontekście definicji nie została wykonana.

```cpp
// dependent base
struct B {
    void g();
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

### <a name="windows-header-issues"></a>Problemy z nagłówka systemu Windows

**/ Ograniczająca-** opcji jest zbyt restrykcyjny wersji zestawów Windows przed Windows spadek twórców aktualizacji SDK (10.0.16299.0) lub wersji systemu Windows Driver Kit (WDK) 1709. Firma Microsoft zaleca, zaktualizuj do najnowszej wersji zestawów Windows, aby można było używać **/ ograniczająca-** w kodzie sterowników systemu Windows lub urządzenia.

Niektóre pliki nagłówkowe Windows spadek twórców aktualizacji SDK (10.0.16299.0) lub Windows Driver Kit (WDK) 1709, nadal mieć problemy, które były niezgodne z użyciem **/ ograniczająca-**. Aby obejść ten problem, zaleca się ograniczyć stosowanie tych nagłówków można tylko te pliki kodu źródłowego, które wymagają i Usuń **/ ograniczająca-** podczas kompilowania dla tych plików źródłowych określonego kodu. Następujące problemy są specyficzne dla systemu Windows spadek twórców aktualizacji SDK (10.0.16299.0):

#### <a name="issue-in-umqueryh"></a>Problem z programu um\Query.h

Korzystając z **/ ograniczająca-** przełącznika kompilatora `tagRESTRICTION` struktury nie kompiluje się ze względu na element członkowski case(RTOr) "lub".

```cpp
struct tagRESTRICTION
    {
    ULONG rt;
    ULONG weight;
    /* [switch_is][switch_type] */ union _URes
        {
        /* [case()] */ NODERESTRICTION ar;
        /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
        /* [case()] */ NODERESTRICTION pxr;
        /* [case()] */ VECTORRESTRICTION vr;
        /* [case()] */ NOTRESTRICTION nr;
        /* [case()] */ CONTENTRESTRICTION cr;
        /* [case()] */ NATLANGUAGERESTRICTION nlr;
        /* [case()] */ PROPERTYRESTRICTION pr;
        /* [default] */  /* Empty union arm */
        } res;
    };
```

Aby rozwiązać ten problem, skompiluj plików zawierających Query.h bez **/ ograniczająca-** opcji.

#### <a name="issue-in-umcellularapioemh"></a>Problem z programu um\cellularapi_oem.h

Korzystając z **/ ograniczająca-** przełącznika kompilatora, deklaracja przekazująca dalej `enum UICCDATASTOREACCESSMODE` powoduje, że ostrzeżenia:

```cpp
typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
```

Deklaracja przekazana wyliczenia niewystępującego w zakresie to rozszerzenie firmy Microsoft. Aby rozwiązać ten problem, skompiluj plików zawierających cellularapi_oem.h bez **/ ograniczająca-** opcji lub użyj [/wd](../../build/reference/compiler-option-warning-level.md) opcja o wyłączeniu ostrzeżenie C4471.

#### <a name="issue-in-umomscripth"></a>Problem z programu um\omscript.h

W języku C ++ 03, konwersja z literału ciągu znaków na BSTR (który jest typem typedef do "wchar_t *") jest przestarzały, ale dozwolone. W języku C ++ 11 konwersja nie jest dozwolony.

```cpp
virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
    /* [in] */ __RPC__in BSTR propname,
    /* [in] */ __RPC__in BSTR expression,
    /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
```

Aby rozwiązać ten problem, skompiluj plików zawierających omscript.h bez **/ ograniczająca-** opcji lub użyj **/Zc:strictStrings-** zamiast tego.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

W wersji Visual Studio 2017 15,5 cala i nowszych wersji wykonaj następującą procedurę:

1. Otwórz projekt w **strony właściwości** okno dialogowe.

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **języka** strony właściwości.

1. Zmień **tryb zgodności** wartości właściwości do **tak (/ ograniczająca —)**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

W wersjach przed Visual Studio 2017 wersji 15,5 cala wykonaj następującą procedurę:

1. Otwórz projekt w **strony właściwości** okno dialogowe.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Wprowadź **/ ograniczająca-** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
