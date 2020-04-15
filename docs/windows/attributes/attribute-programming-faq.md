---
title: Pogramowanie oparte na atrybutach - najczęściej zadawane pytania
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376063"
---
# <a name="attribute-programming-faq"></a>Pogramowanie oparte na atrybutach - najczęściej zadawane pytania

W tym temacie odpowiedziano na następujące często zadawane pytania:

- [Co to jest HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Kiedy muszę określić nazwę parametru dla atrybutu?](#vcconattributeprogrammmingfaqanchor2)

- [Czy mogę używać komentarzy w bloku atrybutów?](#vcconattributeprogrammmingfaqanchor3)

- [W jaki sposób atrybuty współdziałają z dziedziczeniem?](#vcconattributeprogrammmingfaqanchor4)

- [Jak używać atrybutów w nieprzypisanym projekcie ATL?](#vcconattributeprogrammmingfaqanchor5)

- [Jak korzystać z pliku .idl w projekcie przypisanym?](#vcconattributeprogrammmingfaqanchor6)

- [Czy mogę zmodyfikować kod, który jest wstrzykiwany przez atrybut?](#vcconattributeprogrammmingfaqanchor7)

- [Jak mogę przesłać dalej zadeklarować przypisany interfejs?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Czy mogę używać atrybutów w klasie pochodnej klasy, która również używa atrybutów?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>Co to jest HRESULT?

HRESULT to prosty typ danych, który jest często używany jako wartość zwracana przez atrybuty i ATL w ogóle. W poniższej tabeli opisano różne wartości. Więcej wartości znajduje się w pliku nagłówka winerror.h.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Operacja udana|0x00000000|
|E_unexpected|Nieoczekiwana awaria|0x8000FFFF|
|E_notimpl|Nie zaimplementowano|0x80004001|
|E_outofmemory|Nie można przydzielić niezbędnej pamięci|0x8007000E|
|E_invalidarg|Co najmniej jeden argument jest nieprawidłowy|0x80070057|
|E_nointerface|Żaden taki interfejs nie jest obsługiwany|0x80004002|
|E_pointer|Nieprawidłowy wskaźnik|0x80004003|
|E_HANDLE|Nieprawidłowy uchwyt|0x80070006|
|E_ABORT|Przerwana operacja|0x80004004|
|E_fail|Nieokreślona awaria|0x80004005|
|E_ACCESSDENIED|Błąd odmowy dostępu ogólnego|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>Kiedy muszę określić nazwę parametru dla atrybutu?

W większości przypadków, jeśli atrybut ma pojedynczy parametr, ten parametr jest nazwany. Ta nazwa nie jest wymagana podczas wstawiania atrybutu w kodzie. Na przykład następujące użycie [agregacji](aggregatable.md) atrybutu:

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

||||
|-|-|-|
|[call_as](call-as.md)|[Przypadku](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[Wpis](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[Identyfikator](id.md)|
|[iid_is](iid-is.md)|[Importu](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[Źródła](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>Czy mogę używać komentarzy w bloku atrybutów?

W bloku atrybutów można używać komentarzy jedno- i wielowierszowych. Jednak nie można użyć żadnego stylu komentarza w nawiasach przytrzymujących parametry do atrybutu.

Dozwolone są następujące elementy:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Niedozwolone są następujące elementy:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>W jaki sposób atrybuty współdziałają z dziedziczeniem?

Można dziedziczyć zarówno przypisane i nieprzypisane klasy z innych klas, które mogą być przypisane lub nie. Wynik wyprowadzania z przypisanej klasy jest taki sam jak pochodne z tej klasy po dostawcy atrybutu przekształciła swój kod. Atrybuty nie są przekazywane do klas pochodnych za pośrednictwem dziedziczenia języka C++. Dostawca atrybutów przekształca kod tylko w pobliżu jego atrybutów.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>Jak używać atrybutów w nieprzypisanym projekcie ATL?

Być może masz nieprzypisany projekt ATL, który ma plik .idl, i można rozpocząć dodawanie przypisanych obiektów. W takim przypadku użyj **Kreatora dodawania klasy,** aby podać kod.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>Jak korzystać z pliku .idl w projekcie przypisanym?

W projekcie przypisanym do atl może znajdować się plik .idl. W takim przypadku należy użyć [atrybutu importidl,](importidl.md) skompilować plik .idl do pliku .h (zobacz [strony właściwości MIDL](../../build/reference/midl-property-pages.md) w oknie dialogowym **Strony właściwości** projektu), a następnie dołączyć plik .h do projektu.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>Czy mogę zmodyfikować kod, który jest wstrzykiwany przez atrybut?

Niektóre atrybuty wstrzyknąć kod do projektu. Możesz zobaczyć wstrzyknięty kod przy użyciu opcji kompilatora [/Fx.](../../build/reference/fx-merge-injected-code.md) Istnieje również możliwość skopiowania kodu z wstrzykniętego pliku i wklejenia go do kodu źródłowego. Dzięki temu można zmodyfikować zachowanie atrybutu. Jednak może być jednak trzeba zmodyfikować inne części kodu, jak również.

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>Jak mogę przesłać dalej zadeklarować przypisany interfejs?

Jeśli zamierzasz dokonać deklaracji przesyłania dalej przypisanego interfejsu, należy zastosować te same atrybuty do deklaracji przesyłania dalej, która jest stosowana do deklaracji rzeczywistego interfejsu. Należy również zastosować atrybut [eksportu](export.md) do deklaracji przesyłania dalej.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>Czy mogę używać atrybutów w klasie pochodnej klasy, która również używa atrybutów?

Nie, przy użyciu atrybutów w klasie pochodną klasy, która również używa atrybutów nie jest obsługiwany.

## <a name="see-also"></a>Zobacz też

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)
