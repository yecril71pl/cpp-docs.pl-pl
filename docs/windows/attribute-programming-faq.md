---
title: Atrybut programowania w języku — często zadawane pytania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributed programming
- attributes [C++], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35b57c8813778cf0bbf8efbfcbee8466074b87f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862367"
---
# <a name="attribute-programming-faq"></a>Pogramowanie oparte na atrybutach - najczęściej zadawane pytania
Ten temat zawiera odpowiedzi na poniższe często zadawane pytania:  
  
-   [Co to jest HRESULT?](#vcconattributeprogrammmingfaqanchor1)  
  
-   [Gdy trzeba określać nazwy parametru atrybutu?](#vcconattributeprogrammmingfaqanchor2)  
  
-   [W bloku attribute można używać komentarze?](#vcconattributeprogrammmingfaqanchor3)  
  
-   [Jak atrybuty wchodzą w interakcje z dziedziczenia?](#vcconattributeprogrammmingfaqanchor4)  
  
-   [Jak używać atrybutów w nonattributed Projekt ATL](#vcconattributeprogrammmingfaqanchor5)  
  
-   [Jak używać pliku .idl w projekcie z atrybutami?](#vcconattributeprogrammmingfaqanchor6)  
  
-   [Można zmodyfikować kod, który jest wstrzyknięte przez atrybut?](#vcconattributeprogrammmingfaqanchor7)  
  
-   [Jak można użyć deklaracji interfejsu oparte na atrybutach?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [W klasie pochodnej z klasy, która używa również atrybuty można używać atrybutów?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a> Co to jest HRESULT?  
 `HRESULT` Jest typem proste danych, który jest często używane jako wartości zwracane przez atrybuty i ATL ogólnie. W poniższej tabeli opisano różne wartości. Więcej wartości znajdują się w pliku winerror.h pliku nagłówka.  
  
|Nazwa|Opis|Wartość|  
|----------|-----------------|-----------|  
|S_OK|Operacja ukończona pomyślnie|0x00000000|  
|E_UNEXPECTED|Nieoczekiwany błąd|0x8000FFFF|  
|E_NOTIMPL|Nie zaimplementowano|0x80004001|  
|E_OUTOFMEMORY|Nie można przydzielić potrzebnej pamięci|0x8007000E|  
|E_INVALIDARG|Jeden lub więcej argumentów są nieprawidłowe|0x80070057|  
|E_NOINTERFACE|Nie obsługuje interfejsu|0x80004002|  
|E_POINTER|Nieprawidłowy wskaźnik|0x80004003|  
|E_HANDLE|Nieprawidłowe dojście|0x80070006|  
|E_ABORT|Operacja została przerwana|0x80004004|  
|E_FAIL|Nieokreślony błąd|0x80004005|  
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu|0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a> Gdy trzeba określać nazwy parametru atrybutu?  
 W większości przypadków Jeśli atrybut ma jeden parametr, że parametr nosi nazwę. Ta nazwa nie jest wymagana przy wstawianiu atrybutu w kodzie. Na przykład następujące użycie [agregowaniu](../windows/aggregatable.md) atrybutu:  
  
```  
[coclass, aggregatable(value=allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 jest dokładnie taka sama jak:  
  
```  
[coclass, aggregatable(allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 Jednak następujące atrybuty mieć pojedynczą, bez nazwy parametrów:  
  
||||  
|-|-|-|  
|[call_as](../windows/call-as.md)|[Case](../windows/case-cpp.md)|[cpp_quote](../windows/cpp-quote.md)|  
|[default](../windows/default-cpp.md)|[defaultvalue](../windows/defaultvalue.md)|[defaultvtable](../windows/defaultvtable.md)|  
|[emitidl](../windows/emitidl.md)|[entry](../windows/entry.md)|[first_is](../windows/first-is.md)|  
|[helpcontext](../windows/helpcontext.md)|[helpfile](../windows/helpfile.md)|[helpstring](../windows/helpstring.md)|  
|[helpstringcontext](../windows/helpstringcontext.md)|[helpstringdll](../windows/helpstringdll.md)|[id](../windows/id.md)|  
|[iid_is](../windows/iid-is.md)|[import](../windows/import.md)|[importlib](../windows/importlib.md)|  
|[include](../windows/include-cpp.md)|[includelib —](../windows/includelib-cpp.md)|[last_is](../windows/last-is.md)|  
|[length_is](../windows/length-is.md)|[max_is](../windows/max-is.md)|[no_injected_text](../windows/no-injected-text.md)|  
|[pointer_default](../windows/pointer-default.md)|[pragma](../windows/pragma.md)|[restricted](../windows/restricted.md)|  
|[size_is](../windows/size-is.md)|[source](../windows/source-cpp.md)|[switch_is](../windows/switch-is.md)|  
|[switch_type](../windows/switch-type.md)|[transmit_as](../windows/transmit-as.md)|[wire_marshal](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a> W bloku attribute można używać komentarze?  
 Można użyć zarówno jeden wiersz i wielowierszowe komentarze bloku atrybutu. Jednak nie można użyć albo stylu komentarza wewnątrz nawiasów zawierający parametry do atrybutu.  
  
 Dozwolone jest:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 Zabronione jest:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a> Jak atrybuty wchodzą w interakcje z dziedziczenia?  
 Zarówno oparte na atrybutach i unattributed klasy mogą dziedziczyć innych klas, które mogą się być przypisywane lub nie. Wynik wynikających z atrybutami klasy jest taka sama jak wynikające z tej klasy po dostawcy atrybut ma przekształcone jego kod. Atrybuty nie są przesyłane do klasy poprzez dziedziczenie C++ pochodne. Dostawca atrybutu przekształca tylko kod w pobliżu jego atrybuty.  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a> Jak używać atrybutów w nonattributed Projekt ATL  
 Masz nonattributed Projekt ATL, który ma pliku .idl, i chcesz rozpocząć dodawanie obiektów oparte na atrybutach. W takim przypadku Kreator dodawania klasy do zapewnienia kodu.  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a> Jak używać pliku .idl w projekcie z atrybutami?  
 Masz pliku .idl, którego chcesz użyć w projekcie ATL przypisane. W takim przypadku należy użyć [importidl —](../windows/importidl.md) atrybutu, skompilować pliku .idl do pliku .h (zobacz [strony właściwości MIDL](../ide/midl-property-pages.md) w oknie dialogowym stron właściwości projektu), a następnie dołącz plik .h w projekcie .  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a> Można zmodyfikować kod, który jest wstrzyknięte przez atrybut?  
 Niektóre atrybuty iniekcję kodu do projektu. Wprowadzony kod można wyświetlić za pomocą [/Fx](../build/reference/fx-merge-injected-code.md) — opcja kompilatora. Istnieje również możliwość skopiować z pliku wprowadzony kod i wklej go do kodu źródłowego. Dzięki temu można zmodyfikować zachowanie atrybutu. Jednak należy zmodyfikować kod innych części.  
  
 Poniższy przykład jest wynikiem kopiowania wprowadzony kod do pliku kodu źródłowego:  
  
```  
// attr_injected.cpp  
// compile with: comsupp.lib  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[ module(name="MyLibrary") ];  
  
// ITestTest  
[   
   object,  
   uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"),  
   dual,  
   helpstring("ITestTest Interface"),  
   pointer_default(unique)  
]  
  
__interface ITestTest : IDispatch {  
   [id(1), helpstring("method DoTest")]   
   HRESULT DoTest([in] BSTR str);  
};  
  
// _ITestTestEvents  
[  
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"),  
   dispinterface,  
   helpstring("_ITestTestEvents Interface")  
]  
  
__interface _ITestTestEvents {  
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);  
};  
  
// CTestTest  
[  
   coclass,  
   threading(apartment),  
   vi_progid("TestATL1.TestTest"),  
   progid("TestATL1.TestTest.1"),  
   version(1.0),  
   uuid("D9632007-14FA-4679-9E1C-28C9A949E784"),  
   // this line would be commented out from original file  
   // event_source("com"),  
   // this line would be added to support injected code  
   source(_ITestTestEvents),  
   helpstring("TestTest Class")  
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
  
##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Jak można użyć deklaracji interfejsu oparte na atrybutach?  
 Jeśli ma być deklaracja przekazująca dalej oparte na atrybutach interfejsu należy zastosować takie same atrybuty do deklaracja przekazująca dalej, które są stosowane do deklaracji interfejsu rzeczywiste. Należy także zastosować [wyeksportować](../windows/export.md) atrybutu użytkownika deklaracja przekazująca dalej.  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> W klasie pochodnej z klasy, która używa również atrybuty można używać atrybutów?  
 Nie, za pomocą atrybutów w klasie pochodnej z klasy, który także używa atrybutów jest nieobsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../windows/attributed-programming-concepts.md)