---
title: 'TN065: Obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b066ac483de127e0ce469cf8aaf24991ae5f6ef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953041"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga omówiono sposób dodawania Obsługa podwójnego interfejsu do serwera aplikacji opartego na bibliotece MFC automatyzacji OLE. [Acdual —](../visual-cpp-samples.md) przykładową Obsługa podwójnego interfejsu, a przykładowy kod w tym notatki jest pobierana z acdual —. Makra opisane w tym notatki, takich jak DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART i IMPLEMENT_DUAL_ERRORINFO, są częścią acdual — przykład i znajdują się w MFCDUAL. H.  
  
## <a name="dual-interfaces"></a>Podwójne interfejsy  
 Mimo że automatyzacji OLE umożliwia wdrożenie `IDispatch` interfejsu, interfejs VTBL lub podwójnym interfejsu (obejmuje zarówno), firma Microsoft zaleca, wdrożenie podwójne interfejsy, dla wszystkich uwidocznione obiekty automatyzacji OLE. Podwójne interfejsy mają istotne korzyści `IDispatch`-tylko lub w trybie tylko do VTBL interfejsów:  
  
-   Powiązanie może odbywać się za pośrednictwem interfejsu VTBL w czasie kompilacji lub w czasie wykonywania za pośrednictwem `IDispatch`.  
  
-   Kontrolery automatyzacji OLE, których można użyć interfejsu VTBL mogą korzystać z lepszą wydajność.  
  
-   Istniejące kontrolery automatyzacji OLE, które używają `IDispatch` interfejsu będą nadal działać.  
  
-   Interfejs VTBL jest łatwiejsze do wywołania z C++.  
  
-   Podwójne interfejsy są wymagane do zapewnienia zgodności z funkcji obsługi obiektu Visual Basic.  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Dodawanie Obsługa podwójnego interfejsu na podstawie CCmdTarget — klasa  
 Podwójna interfejs jest naprawdę tylko niestandardowy interfejs pochodny `IDispatch`. Najbardziej oczywistym sposobem wykonania Obsługa podwójnego interfejsu w `CCmdTarget`— na podstawie klasy jest wdrożenie pierwszego wysyłania normalne interfejsu w klasie za pomocą MFC i ClassWizard, a następnie dodaj niestandardowy interfejs później. W większości przypadków implementacji niestandardowy interfejs po prostu delegować do MFC `IDispatch` implementacji.  
  
 Najpierw należy zmodyfikować plik ODL dla serwera zdefiniować dwa interfejsy dla obiektów. Aby zdefiniować dwa interfejsu, należy użyć instrukcji interfejsu zamiast `DISPINTERFACE` instrukcji, który generuje kreatorów Visual C++. Zamiast usuwania istniejących `DISPINTERFACE` instrukcji, Dodaj nowe oświadczenie interfejsu. Zachowując `DISPINTERFACE` formularza, można nadal używać ClassWizard można dodać właściwości i metody do obiektu, ale należy dodać równoważne właściwości i metod do instrukcji interfejsu.  
  
 Interface — instrukcja podwójną interfejsu muszą mieć *OLEAUTOMATION* i *PODWÓJNĄ* atrybutów i interfejs musi pochodzić z `IDispatch`. Można użyć [GUIDGEN](../visual-cpp-samples.md) przykład, aby utworzyć **IID** podwójną interfejsu:  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 Po utworzeniu interface — instrukcja w miejscu, należy uruchomić dodanie wpisów dla metody i właściwości. Podwójne interfejsy należy zmienić kolejność listy parametrów, aby powrócić metod, a funkcje metod dostępu właściwości w interfejsie podwójną **HRESULT** i ich zwracanych wartości przekazywane jako parametry atrybutów `[retval,out]`. Należy pamiętać, że dla właściwości, należy dodać zarówno do odczytu (`propget`) i zapisu (`propput`) dostęp do funkcji o tym samym identyfikatorze. Na przykład:  
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 Po zdefiniowaniu właściwości i metody, należy dodać odwołanie do interfejsu instrukcji w instrukcji coclass. Na przykład:  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 Po zaktualizowaniu pliku ODL, należy używać mechanizmu mapy interfejsu MFC, aby zdefiniować klasa implementacji interfejsu podwójna w klasie obiektów i ustaw odpowiednie pozycje w MFC `QueryInterface` mechanizmu. Potrzebujesz jednego wpisu w `INTERFACE_PART` blok dla każdego wpisu w instrukcji interfejsu ODL, a także wpisy dla wysyłania interfejsu. Każdy wpis ODL z *propput* atrybut wymaga funkcji o nazwie `put_propertyname`. Każdy wpis z *propget* atrybut wymaga funkcji o nazwie `get_propertyname`.  
  
 Aby zdefiniować klasa implementacji dla dwóch interfejsu, Dodaj `DUAL_INTERFACE_PART` bloku do definicji klasy obiektu. Na przykład:  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 Nawiązać dwie interfejsu MFC [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mechanizmu, Dodaj `INTERFACE_PART` wpisu do mapy interfejsu:  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 Następnie należy wypełnić implementacji interfejsu. W większości przypadków będzie można delegować do istniejących MFC `IDispatch` implementacji. Na przykład:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,  
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,  
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 Dla metody i funkcje metod dostępu właściwości do obiektu musisz wypełnić implementacji. Metody i właściwości funkcji ogólnie można delegować do metody wygenerowanych przy użyciu ClassWizard. Jednak jeśli skonfigurowano dostęp do zmiennych bezpośrednio właściwości należy napisać kod, aby get/put wartość do zmiennej. Na przykład:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
    pThis->m_str.SetSysString(retval);

 return NOERROR;  
}  
```  
  
## <a name="passing-dual-interface-pointers"></a>Przekazywanie wskaźniki podwójnego interfejsu  
 Przekazanie wskaźnika podwójnego interfejsu nie jest proste, zwłaszcza, jeśli należy wywołać `CCmdTarget::FromIDispatch`. `FromIDispatch` działa tylko na MFC `IDispatch` wskaźników. Aby obejść ten problem jest zapytania dla oryginalnej `IDispatch` zestaw wskaźnika Konfigurowanie przez MFC i że wskaźnikiem do funkcji, które go potrzebują. Na przykład:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp = NULL;  
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);

    pThis->SetPosition(lpDisp);

 lpDisp->Release();
return NOERROR;  
}  
```  
  
 Przed przekazaniem ich wskaźnik z powrotem przy użyciu metody podwójnego interfejsu, konieczne może być przekonwertować ją z MFC `IDispatch` wskaźnika do wskaźnika podwójnego interfejsu. Na przykład:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>Rejestrowanie biblioteki typów aplikacji  
 Kreatorami AppWizard nie generuje kod, aby zarejestrować biblioteki typów aplikację serwera automatyzacji OLE w systemie. Jeśli istnieją inne sposoby zarejestrować biblioteki typów, jest wygodne zgłoszenia zarejestrować biblioteki typów, podczas aktualizacji jego informacje o typie OLE, oznacza to, że przy każdym uruchomieniu aplikacji autonomicznej.  
  
 Aby zarejestrować autonomiczne biblioteki typów aplikacji przy każdym uruchomieniu aplikacji:  
  
-   Obejmują AFXCTL. H w użytkownika standardowego zawiera plik nagłówka, STDAFX. H, do definicji `AfxOleRegisterTypeLib` funkcji.  
  
-   W aplikacji `InitInstance` funkcji, Znajdź wywołanie `COleObjectFactory::UpdateRegistryAll`. Po to wywołanie, dodaj wywołanie do `AfxOleRegisterTypeLib`, określania **identyfikatora LIBID** odpowiadającego do biblioteki typów, oraz nazwę biblioteki typów:  
  
 "" * / / Gdy aplikacja serwera jest uruchamiana autonomicznej, dobrym pomysłem jest * / / aby zaktualizować rejestr systemu w przypadku, gdy został uszkodzony.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll(); * / / DUAL_SUPPORT_START * / / upewnij się, że biblioteka typów jest zarejestrowana lub podwójnym interfejsu nie będzie działać.  
AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB")); *// DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c: definiuje IID podwójne interfejsy  
    Nie, to muszą zostać skompilowane z prekompilowanym nagłówkiem.  
      #<a name="include-ole2h"></a>obejmują < ole2.h >  
      #<a name="include-initguidh"></a>obejmują < pliku initguid.h >  
      #<a name="include-acdualh"></a>obejmują "acdual.h"  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, `IErrorInfo`. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the `ISupportErrorInfo` interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of `IDispatch::Invoke` typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    Method_prologue — (CAutoClickDoc, DualAClick)  
    TRY_DUAL(IID_IDualAClick) {* / / MFC powoduje automatyczną konwersję z BSTR Unicode do * / / cstring — Ansi, w razie potrzeby...  
    pThis -> m_str = newText;  
    Zwraca brak błędu;  
 }  
    CATCH_ALL_DUAL }  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the `ICreateErrorInfo` interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e->m_wCode + 0x200));

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the `ISupportErrorInfo` interface.  
  
 First, add code to your automation class definition to show it supports `ISupportErrorInfo`.  
  
 Second, add code to your automation class's interface map to associate the `ISupportErrorInfo` implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for `ISupportErrorInfo`.  
  
 Finally, implement the class defined to support `ISupportErrorInfo`.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support `ISupportErrorInfo`. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    Method_prologue — (CAutoClickDoc, SupportErrorInfo)   
    zwracany pThis -> ExternalAddRef();

}   
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    Method_prologue — (CAutoClickDoc, SupportErrorInfo)   
    zwracany pThis -> ExternalRelease();

}   
CAutoClickDoc::XSupportErrorInfo::QueryInterface STDMETHODIMP (REFIID iid, ppvObj LPVoid — *)   
{   
    Method_prologue — (CAutoClickDoc, SupportErrorInfo)   
    zwracany pThis -> ExternalQueryInterface (moszczu & świeżego iid gronowego z, ppvObj);

}   
CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo STDMETHODIMP (REFIID iid)   
{   
    Method_prologue — (CAutoClickDoc, SupportErrorInfo)   
    Zwraca (iid == IID_IDualAClick) S_OK: wartości S_FALSE;   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

