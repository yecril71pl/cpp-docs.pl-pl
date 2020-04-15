---
title: /permissive- (Zgodność ze standardami)
description: Przewodnik po opcji kompilatora Microsoft C++ /permissive- (Standards conformance).
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337400"
---
# <a name="permissive--standards-conformance"></a>/permissive- (Zgodność ze standardami)

Określ tryb zgodności standardów do kompilatora. Ta opcja ułatwia identyfikowanie i rozwiązywanie problemów z zgodnością w kodzie, aby uczynić go bardziej poprawne i bardziej przenośne.

## <a name="syntax"></a>Składnia

> **/permisywne-**

## <a name="remarks"></a>Uwagi

Ta opcja jest obsługiwana w programie Visual Studio 2017 i nowszych.

Można użyć **/permissive-kompilatora** opcji, aby określić zachowanie kompilatora zgodne ze standardami. Ta opcja wyłącza zachowania dopuszczalne i ustawia opcje kompilatora [/Zc](zc-conformance.md) dla ścisłej zgodności. W IDE ta opcja również sprawia, że aparat IntelliSense podkreślają niezgodny kod.

Domyślnie **/permissive-** opcja jest ustawiona w nowych projektach utworzonych przez visual studio 2017 w wersji 15.5 i nowszych wersjach. Nie jest ustawiona domyślnie we wcześniejszych wersjach. Gdy opcja jest ustawiona, kompilator generuje błędy diagnostyczne lub ostrzeżenia, gdy niestandardowe konstrukcje języka są wykrywane w kodzie, w tym niektóre typowe błędy w kodzie pre-C ++ 11.

Opcja **/permissive-** jest zgodna z prawie wszystkimi plikami nagłówkowymi z najnowszych zestawów Windows, takimi jak Software Development Kit (SDK) lub Windows Driver Kit (WDK), począwszy od zestawu Windows Fall Creators SDK (10.0.16299.0). Starsze wersje zestawu SDK mogą nie zostać skompilowane w **obszarze /permissive-** z różnych powodów zgodności kodu źródłowego. Kompilator i zestaw SDK są dostarczane na różnych osiach czasu wydania, w związku z tym istnieją pewne pozostałe problemy. Aby uzyskać informacje o określonych problemach z plikami [nagłówkowymi nagłówka,](#windows-header-issues) zobacz Problemy z nagłówkiem systemu Windows poniżej.

Opcja **/permissive-** ustawia opcje [/Zc:referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc:strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)i [/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) opcje do zachowania zgodnego. Te opcje domyślnie są niezgodne zachowanie. Można przekazać określone **/Zc** opcje po **/permissive-** w wierszu polecenia, aby zastąpić to zachowanie.

W wersjach kompilatora począwszy od programu Visual Studio 2017 w wersji 15.3 **/permissive-** opcja ustawia [opcję /Zc:ternary.](zc-ternary.md) Kompilator implementuje również więcej wymagań dla dwufazowego wyszukiwania nazw. Po ustawieniu opcji **/permissive-** kompilator analizuje definicje funkcji i szablonów klas oraz identyfikuje nazwy zależne i nieoleżne używane w szablonach. W tej wersji jest wykonywana tylko analiza zależności nazwy.

Rozszerzenia specyficzne dla środowiska i obszary językowe, które standard pozostawia do realizacji nie są dotknięte **/permisywne-**. Na przykład specyficzne dla `__declspec`firmy Microsoft , konwencji wywoływania i strukturyzowane wyjątki obsługi słów kluczowych i kompilatora specyficzne dyrektywy pragma lub atrybuty nie są oflagowane przez kompilator w **trybie /permissive-.**

**/permissive-** opcja używa obsługi zgodności w bieżącej wersji kompilatora, aby określić, które konstrukcje języka są niezgodne. Opcja nie określa, czy kod jest zgodny z określoną wersją standardu C++. Aby włączyć wszystkie zaimplementowane wsparcie kompilatora dla najnowszego wzoru roboczego, należy użyć [/std:latest](std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługę kompilatora do aktualnie zaimplementowanego standardu C++17, należy użyć opcji [/std:c++17.](std-specify-language-standard-version.md) Aby ograniczyć obsługę kompilatora, aby ściślej odpowiadać standardowi C++14, należy użyć opcji [/std:c++14,](std-specify-language-standard-version.md) która jest wartością domyślną.

Nie wszystkie C++ 11, C++ 14 lub C++ 17 kod zgodny ze standardami jest obsługiwany przez kompilator MSVC we wszystkich wersjach programu Visual Studio 2017. W zależności od wersji programu Visual Studio opcja **/permissive-** może nie wykrywać problemów dotyczących niektórych aspektów wyszukiwania nazw dwufazowych, wiązanie odwołania nieprzeciętnego z tymczasowym, traktowanie copy init jako bezpośredniego init, zezwalanie na wiele konwersji zdefiniowanych przez użytkownika podczas inicjowania lub alternatywnych tokenów dla operatorów logicznych i innych nieobsługujących się obszarów zgodności. Aby uzyskać więcej informacji na temat problemów z zgodnością w programie Visual C++, zobacz [Niestandardowe zachowanie](../../cpp/nonstandard-behavior.md). Aby w pełni wykorzystać **/permissive-**, zaktualizuj program Visual Studio do najnowszej wersji.

### <a name="how-to-fix-your-code"></a>Jak naprawić kod

Oto kilka przykładów kodu, który jest wykrywany jako niezgodny podczas korzystania **z /permissive-**, wraz z sugerowanymi sposobami rozwiązania problemów.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Używanie domyślnego identyfikatora jako identyfikatora w kodzie macierzystym

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Szukaj członków w bazie zależnej

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Używanie kwalifikowanych nazw w deklaracjach elementów członkowskich

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicjowanie wielu członków związku w inicjatorze członkostwa

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

#### <a name="hidden-friend-name-lookup-rules"></a>Ukryte reguły wyszukiwania nazw znajomych

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
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Używanie wyliczenia z zakresem w granicach tablicy

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Użyj dla każdego w kodzie macierzystym

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Niejednoznaczne argumenty operatora warunkowego

W wersjach kompilatora przed visual studio 2017 w wersji 15.3 kompilator akceptowane argumenty `?:` do operatora warunkowego (lub operator trójskładnikowy), które są uważane za niejednoznaczne przez standard. W **trybie /permissive-** kompilator wystawia teraz jedną lub więcej diagnostyki w przypadkach, które skompilowane bez diagnostyki we wcześniejszych wersjach.

Typowe błędy, które mogą wynikać z tej zmiany obejmują:

- błąd C2593: 'operator?' jest niejednoznaczna

- błąd C2679: binary '?': nie znaleziono operatora, który przyjmuje po prawej stronie operand typu "B" (lub nie ma dopuszczalnej konwersji)

- błąd C2678: binary '?': nie znaleziono operatora, który przyjmuje leworęczny operand typu "A" (lub nie ma dopuszczalnej konwersji)

- błąd C2446: ':': brak konwersji z 'B' na 'A'

Typowy wzorzec kodu, który może spowodować ten problem jest, gdy niektóre klasy C zapewnia zarówno jawne konstruktora z innego typu T i operatora konwersji jawne typu T. W tym przypadku zarówno przeliczenie drugiego argumentu na typ trzeciego argumentu, jak i przeliczenie trzeciego argumentu na typ drugiego argumentu są prawidłowymi konwersjami. Ponieważ oba są ważne, jest niejednoznaczny zgodnie ze standardem.

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

Istnieje ważny wyjątek od tego wspólnego wzorca, gdy T reprezentuje jeden z `const char *` `const char16_t *`typów ciągów zakończonych z `?:` wartością null (na przykład , i tak dalej), a rzeczywisty argument jest literałem ciągu odpowiedniego typu. C++17 zmienił semantycę z C++14. W rezultacie kod w przykładzie 2 jest akceptowany w **obszarze /std:c++14** i odrzucany w obszarze **/std:c++17,** gdy używany jest **/Zc:ternary** lub **/permissive-.**

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

Innym przypadkiem, w którym mogą pojawić się błędy, `void`są operatory warunkowe z jednym argumentem typu . Ten przypadek może być powszechne w assert-jak makra.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Mogą również pojawić się błędy w metaprogramowaniu szablonu, gdzie typy wyników operatora warunkowego mogą ulec zmianie w obszarze **/Zc:ternary** i **/permissive-**. Jednym ze sposobów rozwiązania tego problemu jest użycie [std::remove_reference](../../standard-library/remove-reference-class.md) na typ wynikowy.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Dwufazowe odszukiwanie nazw

Po ustawieniu opcji **/permissive-** kompilator analizuje definicje funkcji i szablonów klas, identyfikując nazwy zależne i nieoleżne używane w szablonach, zgodnie z wymaganiami dla dwufazowego wyszukiwania nazw. W programie Visual Studio 2017 w wersji 15.3 jest wykonywana analiza zależności nazw. W szczególności nazwy niesie zależne, które nie są zadeklarowane w kontekście definicji szablonu, powodują komunikat diagnostyczny zgodnie ze standardami ISO C++. W programie Visual Studio 2017 w wersji 15.7 jest również wykonywane powiązanie nazw nieoleżnych, które wymagają wyszukiwania zależnego od argumentów w kontekście definicji.

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

Jeśli chcesz starsze zachowanie dla wyszukiwania dwufazowego, ale w przeciwnym razie chcesz **/permissive-** zachowanie, dodaj **/Zc:twoPhase-** opcja.

### <a name="windows-header-issues"></a>Problemy z nagłówkiem systemu Windows

Opcja **/permissive-** jest zbyt ścisła dla wersji zestawów Windows przed zestawem Windows Fall Creators Update SDK (10.0.16299.0) lub windows driver kit (WDK) w wersji 1709. Zalecamy aktualizację do najnowszych wersji zestawów Windows w celu użycia **/permissive-** w kodzie sterownika systemu Windows lub urządzenia.

Niektóre pliki nagłówkowe w zestawie Windows April 2018 Update SDK (10.0.17134.0), zestawie SDK windows fall creators update (10.0.16299.0) lub Windows Driver Kit (WDK) 1709 nadal mają problemy, które sprawiają, że są niezgodne z używaniem **/permissive-**. Aby obejść te problemy, zaleca się ograniczyć użycie tych nagłówków tylko do tych plików kodu źródłowego, które ich wymagają, i usunąć **/permissive-** opcja podczas kompilowania tych plików kodu źródłowego.

Te nagłówki WinRT WRL wydane w kole SDK aktualizacji aktualizacji systemu Windows z kwietnia 2018 r. (10.0.17134.0) nie są czyste z **/permissive-**. Aby obejść te problemy, podczas pracy z tymi nagłówkami nie należy używać **/permissive-** lub **/permissive-** z **/Zc:twoPhase:**

- Problemy w winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problem w winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Te nagłówki trybu użytkownika wydane w koleżu Windows April 2018 Update SDK (10.0.17134.0) nie są czyste za pomocą **/permissive-**. Aby obejść te problemy, nie należy używać **/permissive-** podczas pracy z tymi nagłówkami:

- Problemy w um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problem w um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemy w um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Te problemy są specyficzne dla nagłówków trybu użytkownika w sdk Windows Fall Creators Update (10.0.16299.0):

- Problem w umio/Query.h

   Podczas korzystania z przełącznika kompilatora **/permissive,** `tagRESTRICTION` struktura nie kompiluje się z powodu elementu członkowskiego case(RTOr) 'or'.

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

   Aby rozwiązać ten problem, skompiluj pliki, które zawierają Query.h bez **opcji /permissive-.**

- Emisja w umm/cellularapi_oem.h

   Podczas korzystania **z przełącznika /permissive-** kompilatora, forward deklaracji `enum UICCDATASTOREACCESSMODE` powoduje ostrzeżenie:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Forward deklaracji unscoped wyliczenia jest rozszerzenie firmy Microsoft. Aby rozwiązać ten problem, skompiluj pliki, które zawierają cellularapi_oem.h bez opcji **/permissive-** lub użyj opcji [/wd,](compiler-option-warning-level.md) aby wyciszyć ostrzeżenie C4471.

- Problem w umm/omscript.h

   W języku C++ 03 konwersja z literału ciągu do BSTR (który jest typedef do 'wchar_t *') jest przestarzała, ale dozwolona. W języku C++11 konwersja nie jest już dozwolona.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Aby rozwiązać ten problem, skompiluj pliki zawierające omscript.h bez opcji **/permissive-** lub użyj **/Zc:strictStrings-** zamiast tego.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

W programie Visual Studio 2017 w wersji 15.5 i nowszych wersjach należy użyć tej procedury:

1. Otwórz okno dialogowe **Strony właściwości** projektu.

1. Wybierz stronę właściwości **Właściwości** > języka**konfiguracji C/C++.** > **Language**

1. Zmień wartość właściwości **mode conformance** na **Tak (/permisywne-)**. Wybierz **przycisk OK** lub **Zastosuj,** aby zapisać zmiany.

W wersjach przed programem Visual Studio 2017 w wersji 15.5 należy użyć tej procedury:

1. Otwórz okno dialogowe **Strony właściwości** projektu.

1. Wybierz stronę właściwości**wiersza polecenia** **Właściwości** > konfiguracji**C/C++.** > 

1. Wprowadź opcję **/permissive-** kompilator w polu **Opcje dodatkowe.** Wybierz **przycisk OK** lub **Zastosuj,** aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
