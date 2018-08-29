---
title: -permissive - (zgodność ze standardami) | Dokumentacja firmy Microsoft
ms.date: 06/21/2018
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
ms.openlocfilehash: 1f2f0b1ca5351fbf2cfa2ab4b3233f8e709fae44
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131219"
---
# <a name="permissive--standards-conformance"></a>/ permissive-(zgodność ze standardami)

Określ tryb zgodności standardów do kompilatora. Użyj tej opcji, aby ułatwić identyfikowanie i rozwiązywanie problemów ze zgodnością w kodzie, aby stał się bardziej poprawny i bardziej przenośny.

## <a name="syntax"></a>Składnia

> **/ permissive-**

## <a name="remarks"></a>Uwagi

Ta opcja jest obsługiwana w programie Visual Studio 2017 i nowszych wersjach.

Możesz użyć **/ permissive-** opcję kompilatora, aby określić zachowanie zgodne z normami kompilatora. Ta opcja powoduje wyłączenie warunki dotyczące zachowania i ustawia [/Zc](../../build/reference/zc-conformance.md) opcje kompilatora, aby uzyskać pełną zgodność. W środowisku IDE ta opcja sprawia, że aparat podkreślenie niezgodnych kodu IntelliSense.

Domyślnie **/ permissive-** opcja jest ustawiana w nowe projekty utworzone przez program Visual Studio 2017 w wersji 15.5 i nowszych wersjach. Nie ustawiono domyślne we wcześniejszych wersjach. Gdy opcja jest ustawiona, kompilator generuje błędy diagnostycznych lub ostrzeżenia podczas konstrukcji językowych niestandardowych są wykrywane w kodzie, w tym niektóre typowe błędy w pre-C ++ 11 kodu.

**/ Permissive-** opcja jest zgodna z prawie wszystkie pliki nagłówkowe z najnowszych zestawów Windows, takich jak Software Development Kit (SDK) lub Windows Driver Kit (WDK), począwszy od Windows SDK Fall Creators Update (10.0.16299.0). Starsze wersje zestawu SDK może kompilacja nie powiedzie się w obszarze **/ permissive-** różne źródła przyczyny zgodność kodu. Kompilator i dostarczaj zestawów SDK na osiach czasu z różnych wersji, w związku z tym występują pewne problemy pozostałych. W przypadku określonego nagłówka pliku problemów, zobacz [problemów nagłówka Windows](#windows-header-issues) poniżej.

**/ Permissive-** zestawy opcji [/Zc: strictstrings](../../build/reference/zc-conformance.md) i [/Zc: rvaluecast](../../build/reference/zc-conformance.md) opcje do zachowania zgodności. Wartością domyślną niezgodnych zachowanie. Można przekazać określonego **/Zc** opcje po **/ permissive-** w wierszu polecenia, aby zastąpić to zachowanie.

W wersjach kompilatora, począwszy od programu Visual Studio 2017 w wersji 15.3 **/ permissive-** zestawy opcji [/Zc: ternary](../../build/reference/zc-ternary.md) opcji. Kompilator wykonuje kilka wymagań dotyczących nazwy dwufazowe wyszukiwanie. Gdy **/ permissive-** wyboru jest zaznaczone, w którym kompilator analizuje funkcji i klas definicjach szablonów, identyfikowanie nazwy zależne i zależne od innych niż używane w szablonach. W tej wersji odbywa się tylko nazwa analizy zależności.

Rozszerzenia specyficznymi dla środowiska i obszary języka standard pozostawia do wykonania nie dotyczy **/ permissive-**. Na przykład specyficzne dla firmy Microsoft `__declspec`, Konwencja wywoływania i obsługi słów kluczowych i dyrektyw pragma specyficznych dla kompilatora lub atrybutów wyjątków strukturalnych nie są oznaczone przez kompilator w **/ permissive-** trybu.

**/ Permissive-** opcja używa obsługi zgodności w bieżącej wersji kompilatora ustalenie konstrukcji języka, które są niezgodne. Opcja nie określa, czy kod jest zgodny z określoną wersją C++ standard. Aby włączyć wszystkie obsługa kompilatora zaimplementowane do najnowszego standardu projekt, należy użyć [/std:latest](../../build/reference/std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługa kompilatora do aktualnie wdrożonych standardzie C ++ 17, należy użyć [/STD: c ++ 17](../../build/reference/std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługę kompilatora, aby lepiej dopasować standard C ++ 14, należy użyć [/STD: c ++ 14](../../build/reference/std-specify-language-standard-version.md) opcji, co jest ustawieniem domyślnym.

Nie wszystkie C ++ 11, C ++ 14 lub C ++ 17 zgodne z normami kodu jest obsługiwana przez kompilator języka Visual C++ w programie Visual Studio 2017. W zależności od wersji programu Visual Studio **/ permissive-** opcji może nie wykryć problemy dotyczące niektóre aspekty dwufazowe wyszukiwanie nazw, powiązanie odwołanie niestałe do tymczasowej, traktowanie init kopię jako bezpośrednie init, umożliwiając wiele zdefiniowanych przez użytkownika konwersje inicjowania lub alternatywne tokenów dla operatorów logicznych i innych zagadnień-obsługiwany zgodność. Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md). Aby uzyskać najbardziej z **/ permissive-**, zaktualizować program Visual Studio do najnowszej wersji.

### <a name="how-to-fix-your-code"></a>Jak naprawić kod

Poniżej przedstawiono kilka przykładów kodu, który zostanie wykryte jako niezgodne, gdy używasz **/ permissive-**, wraz z sugerują sposoby rozwiązywania problemów.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Użyj domyślnej jako identyfikatora w kodzie natywnym

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Wyszukiwanie członków w podstawowym zależne

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Użyj kwalifikowanej nazwy w deklaracjach składowych

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicjowanie wielu składowych Unii w inicjatorze składowej

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

#### <a name="hidden-friend-name-lookup-rules"></a>Reguły wyszukiwania nazwy przyjazne ukryte

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Użyj Typy wyliczeniowe w granice tablicy

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Użycie dla każdego w kodzie natywnym

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

W wersjach kompilatora przed Visual Studio 2017 w wersji 15.3, kompilator zaakceptowane argumenty operator warunkowy (lub operator trójargumentowy) `?:` uwzględnianych niejednoznaczne przez Standard. W **/ permissive-** tryb, kompilator generuje teraz jeden lub więcej diagnostyki w przypadkach, w których skompilowany bez diagnostyki we wcześniejszych wersjach.

Błędy typowych, które mogą wynikać z tej zmiany obejmują:

- Błąd C2593: 'operator'? jest niejednoznaczny

- Błąd C2679: binarny '?': znaleziono żadnego operatora, który przyjmuje prawostronny operand typu "B" (lub nie jest dopuszczalne konwersja)

- Błąd C2678: binarny '?': znaleziono żadnego operatora, który przyjmuje lewostronny operand typu "A" (lub nie jest dopuszczalne konwersja)

- Błąd C2446: ":": Brak konwersji z 'B', 'A'

Wzorzec typowy kod, który może być przyczyną tego problemu jest, gdy niektóre klasy C zawiera zarówno niejawnego konstruktora z innego typu T, jak i operator-jawnej konwersji typu T. W takim przypadku zarówno konwersja 2nd argumentów na typ 3 i konwersji argumentu 3, typ 2. są prawidłowe konwersje niejednoznacznego zgodnie ze standardem.

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

Ma ważny wyjątek, aby ten typowy wzorzec, gdy T reprezentuje jeden z typów ciąg zakończony znakiem null (na przykład `const char *`, `const char16_t *`i tak dalej) i rzeczywisty argument `?:` jest ciągiem literału odpowiedniego typu. C ++ 17 zmianie uległa semantyki C ++ 14. W rezultacie kod w przykładzie 2 jest akceptowany w obszarze **/STD: c ++ 14** i odrzucone w obszarze **/STD: c ++ 17** podczas **/Zc: ternary** lub **/permissive-** jest używany.

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

Inny przypadek, w którym zostaną wyświetlone błędy znajduje się w operatorów warunkowych, z jednym argumentem typu `void`. Ten przypadek może być często używany w makra ASSERT podobne.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Ponadto mogą pojawić się błędy w szablonie metaprogramowanie, gdzie typy wyników operatora warunkowego mogą ulec zmianie w obszarze **/Zc: ternary** i **/ permissive-**. Jednym ze sposobów, aby rozwiązać ten problem, jest użycie [std::remove_reference](../../standard-library/remove-reference-class.md) wynikowy typu.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Nazwa dwufazowe wyszukiwanie

Gdy **/ permissive-** wyboru jest zaznaczone, w którym kompilator analizuje funkcji i klas definicjach szablonów, identyfikowanie nazwy zależne i zależne od innych niż używane w szablonach, zgodnie z wymaganiami dla nazwy dwufazowe wyszukiwanie. W programie Visual Studio 2017 w wersji 15.3 Nazwa zależności analiza jest wykonywana. W szczególności nazwy zależne od innych, które nie zostały zadeklarowane w kontekście definicji szablonu spowodować, że komunikat diagnostyczny zgodnie z wymogami normy ISO C++. W programie Visual Studio 2017 wersji 15.7 również odbywa się powiązania nazwy zależne od innych, które wymagają argumentów zależne odnośnika w kontekście definicji.

```cpp
// dependent base
struct B {
    void g() {}
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

Jeśli chcesz starsze zachowanie dwufazowe wyszukiwanie, ale w przeciwnym razie ma **/ permissive-** zachowanie, Dodaj **/Zc:twoPhase-** opcji.

### <a name="windows-header-issues"></a>Problemy z nagłówka Windows

**/ Permissive-** opcja jest zbyt restrykcyjny dla wersji zestawów Windows przed SDK Windows Fall Creators Update (10.0.16299.0) lub Windows Driver Kit (WDK) w wersji 1709. Firma Microsoft zaleca, zaktualizuj do najnowszej wersji zestawów Windows, aby można było używać **/ permissive-** w kodzie sterownika Windows lub urządzenia.

Niektóre pliki nagłówkowe w kwietniu Windows SDK z aktualizacją 2018 r. (10.0.17134.0), SDK Windows Fall Creators Update (10.0.16299.0) lub Windows Driver Kit (WDK) 1709, nadal masz problemy, które są zgodne z użyciem **/permissive-**. W celu obejścia tych problemów, firma Microsoft zaleca korzystanie z tych nagłówków można ograniczyć do tylko tych plików kodu źródłowego, które wymagają i Usuń **/ permissive-** opcję podczas kompilowania dla tych plików źródłowych określonego kodu.

Tych nagłówków biblioteki WRL WinRT, wydana w Windows kwietnia 2018 r. pakietu SDK aktualizacji (10.0.17134.0) nie są czyste z **/ permissive-**. Aby uniknąć tych problemów, nie należy używać **/ permissive-**, lub użyj **/ permissive-** z **/Zc:twoPhase-** podczas pracy z tych nagłówków:

- Problemy z winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Wysłać winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Tych nagłówków trybu użytkownika, wydana w Windows kwietnia 2018 r. pakietu SDK aktualizacji (10.0.17134.0) nie są czyste z **/ permissive-**. Aby obejść ten problem, nie należy używać **/ permissive-** podczas pracy z tych nagłówków:

- Problemy z um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Wysłać um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemy z um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Te problemy są specyficzne dla nagłówków trybu użytkownika w Windows SDK Fall Creators Update (10.0.16299.0):

- Wysłać um/Query.h

   Korzystając z **/ permissive-** przełącznika kompilatora `tagRESTRICTION` struktury nie kompiluje się z powodu case(RTOr) elementu członkowskiego "lub".

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

   Aby rozwiązać ten problem, skompiluj pliki, które zawierają Query.h bez **/ permissive-** opcji.

- Wysłać um/cellularapi_oem.h

   Korzystając z **/ permissive-** przełącznika kompilatora, deklaracja `enum UICCDATASTOREACCESSMODE` powoduje, że ostrzeżenia:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Deklaracja wyliczenia niewystępującego w zakresie jest rozszerzeniem firmy Microsoft. Aby rozwiązać ten problem, skompiluj pliki, które zawierają cellularapi_oem.h bez **/ permissive-** , lub użyć [/wd](../../build/reference/compiler-option-warning-level.md) możliwość wyciszyć ostrzeżenie C4471.

- Wysłać um/omscript.h

   W języku C ++ 03, konwersja z literału ciągu znaków na BSTR (czyli element typedef do "wchar_t *") jest przestarzałe, ale dozwolone. W języku C++ 11 konwersja nie jest już dozwolone.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Aby rozwiązać ten problem, skompiluj pliki, które zawierają omscript.h bez **/ permissive-** , lub użyć **/Zc:strictStrings-** zamiast tego.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

W programie Visual Studio 2017 w wersji 15.5 i nowszych wersjach wykonaj następującą procedurę:

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** stronę właściwości.

1. Zmiana **tryb zgodności** wartość właściwości **tak (/ permissive-)**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

W wersjach starszych niż program Visual Studio 2017 w wersji 15.5 wykonaj następującą procedurę:

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/ permissive-** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora](../../build/reference/compiler-options.md)
- [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
