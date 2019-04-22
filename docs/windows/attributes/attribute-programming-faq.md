---
title: Pogramowanie oparte na atrybutach - najczęściej zadawane pytania
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: fd4c24e3933738d128dffd41018466c33b419de8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025101"
---
# <a name="attribute-programming-faq"></a>Pogramowanie oparte na atrybutach - najczęściej zadawane pytania

W tym temacie odpowiedzi na następujące często zadawane pytania:

- [Co to jest wartość HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Gdy ma do określenia nazwy parametru atrybutu](#vcconattributeprogrammmingfaqanchor2)

- [Czy można użyć komentarze, w bloku atrybutów?](#vcconattributeprogrammmingfaqanchor3)

- [Jak atrybuty są powiązani z dziedziczenia?](#vcconattributeprogrammmingfaqanchor4)

- [Jak używać atrybutów w nonattributed Projekt ATL?](#vcconattributeprogrammmingfaqanchor5)

- [Jak używać pliku .idl w projekcie z atrybutami?](#vcconattributeprogrammmingfaqanchor6)

- [Można zmodyfikować kod, który jest wprowadzony przez atrybut?](#vcconattributeprogrammmingfaqanchor7)

- [Jak można dalej zadeklarować interfejsu opartego na atrybutach?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Na klasę pochodną klasę, która używa również atrybuty można używać atrybutów?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> Co to jest wartość HRESULT?

Wartość HRESULT to typ prosty danych, który jest często używana jako wartość zwracaną przez atrybuty i ATL ogólnie rzecz biorąc. W poniższej tabeli opisano różne wartości. Więcej wartości są zawarte w plikach winerror.h pliku nagłówka.

|Nazwa|Opis|Wartość|
|----------|-----------------|-----------|
|S_OK|Operacja zakończona powodzeniem|0x00000000|
|E_UNEXPECTED|Nieoczekiwany błąd|0x8000FFFF|
|E_NOTIMPL|Nie zaimplementowano|0x80004001|
|E_OUTOFMEMORY|Nie można przydzielić wymaganej ilości pamięci|0x8007000E|
|E_INVALIDARG|Jeden lub więcej argumentów są nieprawidłowe|0x80070057|
|E_NOINTERFACE|Taki interfejs nie jest obsługiwane|0x80004002|
|E_POINTER|Nieprawidłowy wskaźnik|0x80004003|
|E_HANDLE|Nieprawidłowe dojście|0x80070006|
|E_ABORT|Operacja została przerwana|0x80004004|
|E_FAIL|Nieokreślony błąd|0x80004005|
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu|0x80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> Gdy ma do określenia nazwy parametru atrybutu

W większości przypadków Jeśli ten atrybut ma jeden parametr, ten parametr nosi nazwę. Ta nazwa nie jest wymagane podczas wstawiania atrybutu w kodzie. Na przykład następujące użycie polecenia [się agregowaniu](aggregatable.md) atrybutu:

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

Jednak następujące atrybuty mają pojedynczą, bez nazwy parametrów:

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> Czy można użyć komentarze, w bloku atrybutów?

Można użyć jednowierszowego i wielowierszowe komentarze, w bloku attribute. Jednak nie można używać obu stylów komentarz w nawiasach zawierający parametry do atrybutu.

Dozwolone jest:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Niedozwolone jest:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> Jak atrybuty są powiązani z dziedziczenia?

Inne klasy, które mogą sami można przypisać lub nie może dziedziczyć unattributed i opartego na atrybutach klas. Wynik pochodząca z atrybutami klasy jest taka sama jak pochodząca z tej klasy po dostawca atrybucie został przekształcony swój kod. Atrybuty nie są przesyłane do klasy poprzez dziedziczenie C++ pochodne. Dostawca atrybucie tylko przekształca kod spowodowanych antyaliasingiem w pobliżu jego atrybuty.

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> Jak używać atrybutów w nonattributed Projekt ATL?

Masz nonattributed Projekt ATL, który ma pliku .idl, i chcesz rozpocząć dodawanie obiektów opartego na atrybutach. W takim przypadku należy użyć **Kreator dodawania klasy** zapewnienie kodu.

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> Jak używać pliku .idl w projekcie z atrybutami?

Może być pliku .idl, którego chcesz użyć w projekcie ATL opartego na atrybutach. W tym przypadku używasz [importidl —](importidl.md) atrybutu, skompilować pliku .idl, aby plik .h (zobacz [strony właściwości MIDL](../../build/reference/midl-property-pages.md) w projekcie **strony właściwości** okno dialogowe), a następnie dołącz plik .h klasy w projekcie.

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> Można zmodyfikować kod, który jest wprowadzony przez atrybut?

Niektóre atrybuty wstrzyknięcie kodu do projektu. Zobaczysz wprowadzonego kodu za pomocą [/Fx](../../build/reference/fx-merge-injected-code.md) — opcja kompilatora. Jest również możliwe, aby skopiować kod z pliku wprowadzony i wklej go w kodzie źródłowym. Umożliwia modyfikowanie zachowania atrybutu. Jednak trzeba zmodyfikować inne części kodu także.

Poniższy przykład jest wynikiem kopiowania wstrzyknięty kod do pliku kodu źródłowego:

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

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Jak można dalej zadeklarować interfejsu opartego na atrybutach?

Jeśli zamierzasz utworzyć deklaracja interfejsu opartego na atrybutach, należy zastosować te same atrybuty do deklaracją do przodu, które są stosowane do deklaracji rzeczywistego interfejsu. Należy również zastosować [wyeksportować](export.md) atrybutu z deklaracją do przodu.

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Na klasę pochodną klasę, która używa również atrybuty można używać atrybutów?

Nie, przy użyciu atrybutów na klasę pochodną klasę, która używa również atrybutów nie jest obsługiwana.

## <a name="see-also"></a>Zobacz także

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)