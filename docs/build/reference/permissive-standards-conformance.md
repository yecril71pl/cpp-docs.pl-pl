---
title: /permissive- (Zgodność ze standardami)
description: Przewodnik dotyczący opcji kompilatora Microsoft C++/permissive-(zgodność ze standardami).
ms.date: 06/04/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 69a6b413ec6d9d6897e5f11a11aac8c75db2cf5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217210"
---
# <a name="permissive--standards-conformance"></a>/permissive- (Zgodność ze standardami)

Określ tryb zgodności ze standardami do kompilatora. Użyj tej opcji, aby ułatwić identyfikowanie i rozwiązywanie problemów z zgodnością w kodzie, aby poprawić i zwiększyć liczbę urządzeń przenośnych.

## <a name="syntax"></a>Składnia

> **`/permissive-`**

## <a name="remarks"></a>Uwagi

Ta opcja jest obsługiwana w programie Visual Studio 2017 i nowszych.

Możesz użyć **`/permissive-`** opcji kompilatora, aby określić standardy — zgodność z kompilatorem. Ta opcja wyłącza zachowanie ograniczenia i ustawia [**`/Zc`**](zc-conformance.md) Opcje kompilatora dla ścisłej zgodności. W środowisku IDE ta opcja sprawia, że aparat IntelliSense podkreśla niezgodność kodu.

Domyślnie **`/permissive-`** opcja jest ustawiana w nowych projektach utworzonych przez program Visual Studio 2017 w wersji 15,5 i nowszych. Nie jest ona domyślnie ustawiona we wcześniejszych wersjach. Gdy opcja jest ustawiona, kompilator generuje błędy diagnostyczne lub ostrzeżenia, gdy w kodzie zostaną wykryte niestandardowe konstrukcje językowe. Te konstrukcje obejmują niektóre typowe usterki w kodzie poprzedzającym C + + 11.

**`/permissive-`** Opcja jest zgodna z niemal wszystkimi plikami nagłówkowymi z najnowszych zestawów Windows, takich jak zestaw SDK (Software Development Kit) lub Windows Driver Kit (WDK), począwszy od zestawu SDK programu Windows Recreators (10.0.16299.0). Kompilowanie starszych wersji zestawu SDK może zakończyć się niepowodzeniem pod **`/permissive-`** kątem różnych przyczyn zgodności z kodem źródłowym. Kompilator i zestawy SDK znajdują się na różnych osiach czasu wydania, więc istnieją inne problemy. Aby uzyskać informacje o określonych problemach z plikiem nagłówka, zobacz poniższe [zagadnienia dotyczące nagłówków systemu Windows](#windows-header-issues) .

**`/permissive-`** Opcja ustawia [**`/Zc:referenceBinding`**](zc-referencebinding-enforce-reference-binding-rules.md) [**`/Zc:strictStrings`**](zc-strictstrings-disable-string-literal-type-conversion.md) Opcje,, i [**`/Zc:rvalueCast`**](zc-rvaluecast-enforce-type-conversion-rules.md) na zgodność z zachowaniem. Te opcje są domyślne dla zachowania niezgodnego. **`/Zc`** W wierszu polecenia można przekazać określone opcje **`/permissive-`** , aby przesłonić to zachowanie.

W wersjach kompilatora rozpoczynających się w programie Visual Studio 2017 w wersji 15,3, **`/permissive-`** opcja ustawia [**`/Zc:ternary`**](zc-ternary.md) opcję. Kompilator implementuje również więcej wymagań dotyczących dwufazowych nazw. Gdy **`/permissive-`** opcja jest ustawiona, kompilator analizuje definicje funkcji i szablonów klas oraz identyfikuje zależne i niezależne nazwy używane w szablonach. W tej wersji jest wykonywana tylko analiza zależności nazw.

Rozszerzenia specyficzne dla środowiska i obszary języka, które w standardzie opuszczają się do implementacji, nie mają na nie wpływ **`/permissive-`** . Na przykład słowa kluczowe "specyficzny dla firmy Microsoft" **`__declspec`** i "strukturalna obsługa wyjątków" i dyrektywy pragma specyficzne dla kompilatora nie są oflagowane przez kompilator w **`/permissive-`** trybie.

**`/permissive-`** Opcja korzysta z wsparcia zgodności w bieżącej wersji kompilatora, aby określić, które konstrukcje językowe nie są zgodne. Opcja nie określa, czy kod jest zgodny z określoną wersją standardu C++. Aby włączyć obsługę wszystkich wdrożonych kompilatorów dla najnowszej wersji standardu, użyj [**`/std:c++latest`**](std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługę kompilatora do aktualnie zaimplementowanego standardu C++ 17, użyj [**`/std:c++17`**](std-specify-language-standard-version.md) opcji. Aby ograniczyć obsługę kompilatora do bardziej dokładnej zgodności ze standardem C++ 14, użyj [**`/std:c++14`**](std-specify-language-standard-version.md) opcji, która jest wartością domyślną.

Nie wszystkie standardy C++ 11, C++ 14 i C++ 17 — zgodność kodu jest obsługiwana przez kompilator MSVC we wszystkich wersjach programu Visual Studio 2017. W zależności od wersji programu Visual Studio, **`/permissive-`** opcja może nie wykrywać problemów w niektórych aspektach dwufazowego przeszukiwania nazw, powiązania niestałego odwołania do tymczasowego, traktowanie funkcji init jako bezpośredniego init, zezwalającej na wiele zdefiniowanych przez użytkownika konwersji lub alternatywne tokeny operatorów logicznych oraz inne nieobsługiwane obszary zgodności. Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md). Aby maksymalnie wykorzystać zalety programu **`/permissive-`** , zaktualizuj program Visual Studio do najnowszej wersji.

### <a name="how-to-fix-your-code"></a>Jak naprawić kod

Poniżej przedstawiono kilka przykładów kodu, które są wykrywane jako niezgodne podczas korzystania **`/permissive-`** z programu, wraz z sugerowanymi sposobami rozwiązywania problemów.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Użyj domyślnego jako identyfikatora w kodzie natywnym

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Wyszukiwanie elementów członkowskich w zależności od podstaw

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Używanie nazw kwalifikowanych w deklaracjach składowych

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Zainicjuj wiele elementów członkowskich Unii w inicjatorze składowej

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

#### <a name="hidden-friend-name-lookup-rules"></a>Reguły wyszukiwania ukrytych nazw zaprzyjaźnionych

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Użyj typów wyliczeniowych w zakresie w granicach tablicy

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Użyj dla każdego w kodzie natywnym

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

W wersjach kompilatora przed Visual Studio 2017 w wersji 15,3, kompilator zaakceptował argumenty operatora warunkowego (lub operatora "Trzyelementowy"), `?:` który jest uznawany za niejednoznaczny przez Standard. W **`/permissive-`** trybie w tym kompilator wystawia teraz co najmniej jedną diagnostykę w przypadkach, w których skompilowano bez diagnostyki we wcześniejszych wersjach.

Typowe błędy, które mogą wynikać z tej zmiany, obejmują:

- **`error C2593`**`: 'operator ?' is ambiguous`

- **`error C2679`**`: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- **`error C2678`**`: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- **`error C2446`**`: ':': no conversion from 'B' to 'A'`

Typowy wzorzec kodu, który może spowodować ten problem, występuje, gdy Klasa C zawiera zarówno Konstruktor niejawny z innego typu T, jak i operator konwersji niejawnej na typ T. W takim przypadku zarówno konwersja drugiego argumentu na typ trzeciego argumentu, jak i konwersja trzeciego argumentu na typ drugiego argumentu, są prawidłowymi konwersjemi. Ponieważ oba są prawidłowe, jest niejednoznaczne według standardu.

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

Istnieje ważny wyjątek dla tego wspólnego wzorca, gdy T reprezentuje jeden z typów ciągów zakończonych znakiem null (na przykład, `const char *` , `const char16_t *` i tak dalej), a rzeczywisty argument do `?:` jest literałem ciągu odpowiadającego typu. W języku c++ 17 zmieniono semantykę z C++ 14. W związku z tym kod w przykładzie 2 jest akceptowany w obszarze **`/std:c++14`** i odrzucone **`/std:c++17`** w **`/Zc:ternary`** przypadku **`/permissive-`** użycia lub.

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

Innym przypadkiem, gdzie mogą pojawić się błędy, są operatory warunkowe z jednym argumentem typu **`void`** . Ten przypadek może być typowy w makrach przypominających podobne.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Mogą również pojawić się błędy w programowaniu szablonu, gdzie typy wyniku operatora warunkowego mogą ulec zmianie w obszarze **`/Zc:ternary`** i **`/permissive-`** . Jednym ze sposobów rozwiązania tego problemu jest użycie [`std::remove_reference`](../../standard-library/remove-reference-class.md) na typ wyników.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Nazwa dwufazowego wyszukiwania

Gdy **`/permissive-`** opcja jest ustawiona, kompilator analizuje definicje funkcji i szablonów klas, identyfikując zależne i niezależne nazwy używane w szablonach, które są wymagane do przeszukiwania nazw dwufazowych. W programie Visual Studio 2017 w wersji 15,3 jest wykonywana analiza zależności nazw. W szczególności nazwy niezależne, które nie są zadeklarowane w kontekście definicji szablonu, powodują komunikat diagnostyczny wymagany przez standardy ISO C++. W programie Visual Studio 2017 w wersji 15,7 powiązania nazw niezależnych, które wymagają wyszukiwania zależnego od argumentów w kontekście definicji, również są wykonywane.

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

Jeśli chcesz mieć starsze zachowanie w przypadku wyszukiwania dwuetapowego, ale w przeciwnym razie Zażądaj **`/permissive-`** zachowania, Dodaj **`/Zc:twoPhase-`** opcję.

### <a name="windows-header-issues"></a>Problemy z nagłówkiem systemu Windows

**`/permissive-`** Opcja jest zbyt ścisła dla wersji zestawów Windows, zanim system Windows jest w wersji Update SDK (10.0.16299.0) lub Windows Driver Kit (WDK), wersja 1709. Zalecamy aktualizację do najnowszych wersji zestawów Windows, które mają być używane **`/permissive-`** w kodzie systemu Windows lub sterownika urządzenia.

W przypadku niektórych plików nagłówkowych w systemie Windows kwiecień 2018 Update SDK (10.0.17134.0), Windows jesień Creators Update SDK (10.0.16299.0) lub Windows Driver Kit (WDK) 1709 nadal występują problemy, które sprawiają, że nie są one niezgodne z użyciem programu **`/permissive-`** . Aby obejść te problemy, zalecamy ograniczenie użycia tych nagłówków tylko do tych plików kodu źródłowego, które ich wymagają, i usunięcie **`/permissive-`** opcji podczas kompilowania tych określonych plików kodu źródłowego.

Te nagłówki WRL WinRT wydane w zestawie SDK aktualizacji systemu Windows w wersji 2018 (10.0.17134.0) nie są czyste przy użyciu programu **`/permissive-`** . Aby obejść te problemy, nie używaj ich **`/permissive-`** ani nie używaj **`/permissive-`** z **`/Zc:twoPhase-`** nimi podczas pracy z tymi nagłówkami:

- Problemy w WinRT/WRL/Async. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problem w programie WinRT/WRL/Implements. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Te nagłówki trybu użytkownika wydane w zestawie SDK aktualizacji systemu Windows kwiecień 2018 (10.0.17134.0) nie są czyste przy użyciu programu **`/permissive-`** . Aby obejść te problemy, nie należy używać **`/permissive-`** podczas pracy z tymi nagłówkami:

- Problemy w UM/dostrajania. h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problem w programie UM/spddkhlp. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problemy w UM/refptrco. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Te problemy są specyficzne dla nagłówków trybu użytkownika w zestawie SDK aktualizacji z systemem Windows (10.0.16299.0):

- Problem w programie UM/Query. h

   W przypadku korzystania z **`/permissive-`** przełącznika kompilatora, `tagRESTRICTION` Struktura nie kompiluje ze względu na element członkowski "or" Case (RTOr).

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

   Aby rozwiązać ten problem, skompiluj pliki, które zawierają zapytanie. h bez **`/permissive-`** opcji.

- Problem w programie UM/cellularapi_oem. h

   W przypadku korzystania z **`/permissive-`** przełącznika kompilatora, Deklaracja do przodu `enum UICCDATASTOREACCESSMODE` powoduje ostrzeżenie:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Deklaracja do przodu wyliczenia nienależącego do zakresu jest rozszerzeniem firmy Microsoft. Aby rozwiązać ten problem, skompiluj pliki zawierające cellularapi_oem. h bez **`/permissive-`** opcji lub Użyj [**`/wd`**](compiler-option-warning-level.md) opcji, aby wyciszyć ostrzeżenie C4471.

- Problem w programie UM/omscript. h

   W języku C++ 03 konwersja z literału ciągu na BSTR (który jest elementem TypeDef na "wchar_t *") jest przestarzała, ale dozwolona. W języku C++ 11 konwersja nie jest już dozwolona.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Aby rozwiązać ten problem, skompiluj pliki, które zawierają omscript. h bez **`/permissive-`** opcji, lub Użyj **`/Zc:strictStrings-`** zamiast tego.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

W programie Visual Studio 2017 w wersji 15,5 i nowszych należy wykonać następującą procedurę:

1. Otwórz okno dialogowe **strony właściwości** projektu.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja języka**C/C++**  >  **Language** .

1. Zmień wartość właściwości **tryb zgodności** na **tak (/permissive-)**. Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

W wersjach wcześniejszych niż wersja 15,5 programu Visual Studio 2017 Użyj tej procedury:

1. Otwórz okno dialogowe **strony właściwości** projektu.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź opcję kompilatora **/permissive-** w polu **dodatkowe opcje** . Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
