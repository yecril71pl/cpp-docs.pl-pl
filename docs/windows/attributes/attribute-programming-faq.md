---
title: Pogramowanie oparte na atrybutach - najczęściej zadawane pytania
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 70fbcc47884214fb998eb63ebfe50e445dbe95b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843147"
---
# <a name="attribute-programming-faq"></a>Pogramowanie oparte na atrybutach - najczęściej zadawane pytania

Ten temat zawiera odpowiedzi na następujące często zadawane pytania:

- [Co to jest HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Kiedy muszę określić nazwę parametru dla atrybutu?](#vcconattributeprogrammmingfaqanchor2)

- [Czy mogę używać komentarzy w bloku atrybutów?](#vcconattributeprogrammmingfaqanchor3)

- [Jak atrybuty współdziałają z dziedziczeniem?](#vcconattributeprogrammmingfaqanchor4)

- [Jak można używać atrybutów w nieatrybutowym projekcie ATL?](#vcconattributeprogrammmingfaqanchor5)

- [Jak mogę użyć pliku IDL w projekcie z atrybutami?](#vcconattributeprogrammmingfaqanchor6)

- [Czy mogę zmodyfikować kod, który jest wstrzykiwany przez atrybut?](#vcconattributeprogrammmingfaqanchor7)

- [Jak mogę zadeklarować interfejs z atrybutem "dalej"?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Czy można używać atrybutów klasy pochodnej z klasy, która również używa atrybutów?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a> Co to jest HRESULT?

HRESULT to prosty typ danych, który jest często używany jako wartość zwracana przez atrybuty i ATL w ogólności. W poniższej tabeli opisano różne wartości. Więcej wartości znajduje się w pliku nagłówkowym Winerror. h.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Operacja zakończona pomyślnie|0x00000000|
|E_UNEXPECTED|Nieoczekiwany błąd|0x8000FFFF|
|E_NOTIMPL|Nie zaimplementowano|0x80004001|
|E_OUTOFMEMORY|Nie można przydzielić potrzebnej pamięci|0x8007000E|
|E_INVALIDARG|Co najmniej jeden argument jest nieprawidłowy|0x80070057|
|E_NOINTERFACE|Brak obsługiwanego interfejsu|0x80004002|
|E_POINTER|Nieprawidłowy wskaźnik|0x80004003|
|E_HANDLE|Nieprawidłowy uchwyt|0x80070006|
|E_ABORT|Operacja przerwana|0x80004004|
|E_FAIL|Nieokreślony błąd|0x80004005|
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a> Kiedy muszę określić nazwę parametru dla atrybutu?

W większości przypadków, jeśli atrybut ma jeden parametr, ten parametr ma nazwę. Ta nazwa nie jest wymagana podczas wstawiania atrybutu w kodzie. Na przykład następujące użycie atrybutu [agregowanego](aggregatable.md) :

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

jest dokładnie taka sama jak:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Jednak następujące atrybuty mają pojedyncze, nienazwane parametry:

:::row:::
   :::column span="":::
      [`call_as`](call-as.md)\
      [`case`](case-cpp.md)\
      [`cpp_quote`](cpp-quote.md)\
      [`default`](default-cpp.md)\
      [`defaultvalue`](defaultvalue.md)\
      [`defaultvtable`](defaultvtable.md)\
      [`emitidl`](emitidl.md)\
      [`entry`](entry.md)\
      [`first_is`](first-is.md)
   :::column-end:::
   :::column span="":::
      [`helpcontext`](helpcontext.md)\
      [`helpfile`](helpfile.md)\
      [`helpstring`](helpstring.md)\
      [`helpstringcontext`](helpstringcontext.md)\
      [`helpstringdll`](helpstringdll.md)\
      [`id`](id.md)\
      [`iid_is`](iid-is.md)\
      [`import`](import.md)
   :::column-end:::
   :::column span="":::
      [`importlib`](importlib.md)\
      [`include`](include-cpp.md)\
      [`includelib`](includelib-cpp.md)\
      [`last_is`](last-is.md)\
      [`length_is`](length-is.md)\
      [`max_is`](max-is.md)\
      [`no_injected_text`](no-injected-text.md)\
      [`pointer_default`](pointer-default.md)
   :::column-end:::
   :::column span="":::
      [`pragma`](pragma.md)\
      [`restricted`](restricted.md)\
      [`size_is`](size-is.md)\
      [`source`](source-cpp.md)\
      [`switch_is`](switch-is.md)\
      [`switch_type`](switch-type.md)\
      [`transmit_as`](transmit-as.md)\
      [`wire_marshal`](wire-marshal.md)
   :::column-end:::
:::row-end:::

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a> Czy mogę używać komentarzy w bloku atrybutów?

W bloku atrybutu można używać zarówno komentarzy jednowierszowych, jak i wielu wierszy. Nie można jednak użyć żadnego stylu komentarza w nawiasach, które mają parametry do atrybutu.

Dozwolone są następujące elementy:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Następujące elementy są niedozwolone:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a> Jak atrybuty współdziałają z dziedziczeniem?

Można dziedziczyć zarówno klasy z atrybutami, jak i nieatrybutowymi z innych klas, które mogą być przypisana lub nie. Wynik pochodzący z klasy z atrybutami jest taki sam jak pochodny klasy, gdy dostawca atrybutów przeprowadził swój kod. Atrybuty nie są przekazywane do klas pochodnych za poorednictwem dziedziczenia języka C++. Dostawca atrybutu tylko przekształca kod w sąsiedztwie jego atrybutów.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a> Jak można używać atrybutów w nieatrybutowym projekcie ATL?

Może istnieć nieprzypisany Projekt ATL, który ma plik. idl, i można rozpocząć dodawanie obiektów z atrybutami. W takim przypadku należy użyć **Kreatora dodawania klasy** , aby podać kod.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a> Jak mogę użyć pliku IDL w projekcie z atrybutami?

Może istnieć plik. idl, który ma być używany w projekcie z atrybutami ATL. W takim przypadku należy użyć atrybutu [importidl](importidl.md) , skompilować plik. idl do pliku h (zobacz [stronę właściwości MIDL](../../build/reference/midl-property-pages.md) w oknie dialogowym **strony właściwości** projektu), a następnie dołączyć plik h do projektu.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a> Czy mogę zmodyfikować kod, który jest wstrzykiwany przez atrybut?

Niektóre atrybuty wsuwają kod do projektu. Wprowadzany kod można zobaczyć przy użyciu opcji kompilatora [/FX](../../build/reference/fx-merge-injected-code.md) . Możliwe jest również skopiowanie kodu z wstrzykniętego pliku i wklejenie go do kodu źródłowego. Pozwala to modyfikować zachowanie atrybutu. Jednak może być konieczne zmodyfikowanie również innych części kodu.

Poniższy przykład jest wynikiem kopiowania wstrzykniętego kodu do pliku kodu źródłowego:

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Jak mogę zadeklarować interfejs z atrybutem "dalej"?

Jeśli zamierzasz złożyć deklarację do przodu o przypisanym interfejsie, należy zastosować te same atrybuty do deklaracji do przodu, która jest stosowana do rzeczywistej deklaracji interfejsu. Należy również zastosować atrybut [eksportu](export.md) do deklaracji do przodu.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Czy można używać atrybutów klasy pochodnej z klasy, która również używa atrybutów?

Nie, Używanie atrybutów klasy pochodnej z klasy, która również używa atrybutów, nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)
