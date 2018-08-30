---
title: 'TN065: Obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 5ef599c99cc46c2014ee2d72c538b55e59122848
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209689"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga omówiono, jak dodać obsługę podwójnego interfejsu z aplikacją serwer oparty na bibliotece MFC automatyzacji OLE. [Acdual —](../visual-cpp-samples.md) przykładową Obsługa podwójnego interfejsu i przykładowy kod w ta notatka pochodzi z acdual —. Makra opisane w tym notatki, takich jak DECLARE_DUAL_ERRORINFO DUAL_ERRORINFO_PART i IMPLEMENT_DUAL_ERRORINFO, są częścią acdual — przykład i znajdują się w MFCDUAL. H.

## <a name="dual-interfaces"></a>Podwójne interfejsy

Mimo że automatyzacji pozwala na implementowanie `IDispatch` interfejsu, interfejs VTBL lub podwójnego interfejsu (co obejmuje zarówno), firma Microsoft zaleca, implementuje dwa interfejsy, dla wszystkich widoczne obiekty automatyzacji OLE. Podwójne interfejsy mają znaczące korzyści `IDispatch`— tylko lub tylko do VTBL interfejsów:

- Powiązanie może odbywać się w czasie kompilacji przez interfejs VTBL lub w czasie wykonywania za pomocą `IDispatch`.

- Kontrolery automatyzacji OLE, które można użyć interfejsu VTBL mogą korzystać ze zwiększoną wydajność.

- Istniejące kontrolery automatyzacji OLE, które używają `IDispatch` interfejsu będą nadal działać.

- Interfejs VTBL łatwiej jest wywołać z języka C++.

- Podwójne interfejsy są wymagane dla zachowania zgodności z funkcji obsługi obiektu języka Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Dodawanie Obsługa podwójnego interfejsu do klasy na podstawie CCmdTarget

Podwójnego interfejsu jest tylko niestandardowy interfejs pochodną `IDispatch`. Najprostszym sposobem realizowania Obsługa podwójnego interfejsu w `CCmdTarget`— na podstawie klasy jest zaimplementowanie pierwszego wysyłania normalne interfejsu na klasie za pomocą MFC i ClassWizard, a następnie dodaj niestandardowy interfejs później. W większości przypadków implementacji niestandardowego interfejsu po prostu delegowanie do MFC `IDispatch` implementacji.

Najpierw należy zmodyfikować plik ODL serwera zdefiniować dwa interfejsy do obiektów. Aby zdefiniować podwójnego interfejsu, należy użyć instrukcji interfejsu zamiast `DISPINTERFACE` instrukcji, które generują kreatorów Visual C++. Zamiast usuwając istniejący `DISPINTERFACE` instrukcji, Dodaj nowy raport interfejsu. Zachowując `DISPINTERFACE` formularza, będzie można kontynuować używanie ClassWizard można dodać właściwości i metody do obiektu, ale należy dodać do interface — instrukcja równoważne właściwości i metody.

Interface — instrukcja podwójnego interfejsu muszą mieć *oleautomation —* i *PODWÓJNĄ* atrybutów i interfejs musi pochodzić od `IDispatch`. Możesz użyć [GUIDGEN](../visual-cpp-samples.md) przykładu można utworzyć **IID** dla podwójnego interfejsu:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Po utworzeniu interface — instrukcja w miejscu Rozpocznij dodawanie wpisów do metod i właściwości. Podwójne interfejsy, musisz zmienić układ listy parametrów, tak, aby zwrócić swoje metody i funkcje metod dostępu właściwości w podwójnego interfejsu **HRESULT** i przekazywanie ich wartości zwracane jako parametry atrybutów `[retval,out]`. Należy pamiętać, że w przypadku właściwości będzie należy dodać zarówno podczas operacji odczytu (`propget`) i zapis (`propput`) dostęp do funkcji z tym samym identyfikatorze. Na przykład:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Po zdefiniowaniu właściwości i metody, należy dodać odwołanie do interface — instrukcja w instrukcji klasy coclass. Na przykład:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Po zaktualizowaniu pliku ODL używać mechanizmu mapowania interfejsu MFC do definiowania klasy implementacji dla podwójnego interfejsu w klasie obiektów i wprowadzić odpowiednie pozycje w MFC `QueryInterface` mechanizm. Należy w jeden wpis `INTERFACE_PART` blok dla każdego wpisu w zestawieniu interfejsu ODL, a także wpisy dla interfejs ekspedycji. Każdy wpis ODL z *propput* atrybut wymaga funkcję o nazwie `put_propertyname`. Każdy wpis z *propget* atrybut wymaga funkcję o nazwie `get_propertyname`.

Aby zdefiniować klasę implementacji dla podwójnego interfejsu, Dodaj `DUAL_INTERFACE_PART` bloku do swojej definicji klasy obiektu. Na przykład:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

Nawiązać podwójnego interfejsu MFC [QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object) mechanizmu, Dodaj `INTERFACE_PART` wpisu do mapy interfejsu:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Następnie należy wypełnić implementacji interfejsu. W większości przypadków można delegować do istniejących MFC `IDispatch` implementacji. Na przykład:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
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
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

Dla obiektu metody i funkcje metod dostępu właściwości należy wypełnić w implementacji. Powrót do metod wygenerowany za pomocą ClassWizard ogólnie delegować metod i właściwości funkcji. Jednakże jeśli skonfigurowano dostęp do zmiennych bezpośrednio właściwości należy napisać kod, aby get/put wartość do zmiennej. Na przykład:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>Przekazywanie wskaźników podwójnego interfejsu

Przekazanie wskaźnika podwójnego interfejsu nie jest proste, zwłaszcza, jeśli jest to potrzebne do wywoływania `CCmdTarget::FromIDispatch`. `FromIDispatch` działa tylko na MFC `IDispatch` wskaźników. Jest jednym ze sposobów, aby obejść ten problem do wykonywania zapytań w oryginalnym `IDispatch` zestaw wskaźnika w górę przez MFC i przekazać ten wskaźnik do funkcji, które go potrzebują. Na przykład:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

Przed przekazaniem wskaźnik wstecz za pośrednictwem metody podwójnego interfejsu, konieczne może być przekonwertować ją z MFC `IDispatch` wskaźnik do wskaźnika podwójnego interfejsu. Na przykład:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>Rejestrowania biblioteki typów aplikacji

Kreator AppWizard nie generuje kodu, można zarejestrować biblioteki typów aplikację serwera automatyzacji OLE w systemie. Gdy istnieją inne sposoby, aby zarejestrować bibliotekę typów, wygodne jest aplikacja zarejestrować biblioteki typów, podczas aktualizacji informacji o typie OLE, oznacza to, że przy każdym uruchomieniu aplikacji autonomicznej.

Aby zarejestrować autonomicznie biblioteki typów aplikacji przy każdym uruchomieniu aplikacji:

- Obejmują AFXCTL. H w standardowego zawiera STDAFX pliku nagłówka. Godz., aby dostęp do definicji `AfxOleRegisterTypeLib` funkcji.

- W Twojej aplikacji `InitInstance` funkcji, Znajdź wywołanie `COleObjectFactory::UpdateRegistryAll`. Po tym wywołaniu, dodaj wywołanie `AfxOleRegisterTypeLib`, określanie **LIBID** odpowiadający Twojej biblioteki typów, wraz z nazwą Twojej biblioteki typów:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modyfikowanie ustawień kompilacji projektu, aby uwzględnić zmiany w bibliotece typów

Aby zmodyfikować ustawienia kompilacji projektu, aby plik nagłówka zawierający **UUID** definicje są generowane przez z MkTypLib, zawsze wtedy, gdy zostanie odtworzony biblioteki typów:

1. Na **kompilacji** menu, kliknij przycisk **ustawienia**, a następnie wybierz plik ODL z listy plików dla każdej konfiguracji.

2. Kliknij przycisk **OLE typy** kartę i określ nazwę pliku w **nagłówku wyjściowym** pole nazwy pliku. Nazwa pliku, który nie jest już używany w projekcie, należy użyć, ponieważ z MkTypLib zastąpi istniejący plik. Kliknij przycisk **OK** zamknąć **ustawieniach kompilacji** okno dialogowe.

Aby dodać **UUID** definicje z pliku nagłówka wygenerowane z MkTypLib do projektu:

1. Obejmują wygenerowane z MkTypLib pliku nagłówka w standardowego zawiera STDAFX pliku nagłówka. H.

2. Utwórz nowy plik INITIIDS. CPP i dodaj go do projektu. W tym pliku należy uwzględnić plik nagłówka wygenerowane z MkTypLib po tym OLE2. H i INITGUID. GODZ.:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. Na **kompilacji** menu, kliknij przycisk **ustawienia**, a następnie wybierz pozycję INITIIDS. CPP z listy plików dla każdej konfiguracji.

4. Kliknij przycisk **C++** kartę, kliknij kategorię **prekompilowanych nagłówków**i wybierz **prekompilowane nagłówki nie są używane** przycisku radiowego. Kliknij przycisk OK, aby zamknąć **ustawieniach kompilacji** okno dialogowe.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Określenie nazwy klasy odpowiedni obiekt w bibliotece typów

Kreatorzy dostarczane z programem Visual C++ niepoprawnie Użyj nazwy klasy implementacji, aby określić wspólna w pliku ODL serwera OLE utworzone klasy. Gdy to będzie działać, nazwę klasy wykonania prawdopodobnie nie jest nazwą klasy, użytkownicy obiektu do użycia. Aby określić poprawną nazwę, otwórz plik ODL, zlokalizuj każdej instrukcji klasy coclass i zastąp nazwę klasy wykonania poprawną nazwę zewnętrznego.

Należy pamiętać, że po zmianie instrukcji coclass nazwy zmiennej **CLSID**s w pliku nagłówka wygenerowane z MkTypLib zostanie zmieniona. Należy zaktualizować kod, aby użyć nowej nazwy zmiennych.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Obsługa wyjątków i interfejsów błąd automatyzacji

Metody i funkcje metod dostępu właściwości obiektu automatyzacji może zgłaszać wyjątki. Jeśli tak, należy je obsłużyć w danej implementacji podwójnego interfejsu i przekazać informacje o wyjątku odsyłane do kontrolera korzystając z interfejsu obsługi błędów automatyzacji OLE, `IErrorInfo`. Ten interfejs zapewnia informacje o błędzie szczegółowe, kontekstowe za pośrednictwem zarówno `IDispatch` i VTBL interfejsów. Aby wskazać, że procedura obsługi błędów jest dostępna, należy zaimplementować `ISupportErrorInfo` interfejsu.

Do ilustrowania mechanizmu obsługi błędów, założono, że wygenerowany ClassWizard funkcji, używaną do zaimplementowania pomocy technicznej standard wysyłania zgłaszają wyjątki. Implementacja MFC `IDispatch::Invoke` zazwyczaj przechwytuje tych wyjątków i konwertuje je na strukturę EXCEPTINFO, która jest zwracana za pośrednictwem `Invoke` wywołania. Jednak w przypadku interfejsu VTBL odpowiedzialność za przechwytywanie wyjątków, samodzielnie. Na przykład chronić swoje metody podwójnego interfejsu:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` zajmuje się zwracając kod poprawny błąd, gdy wystąpi wyjątek. `CATCH_ALL_DUAL` Konwertuje wyjątek MFC do automatyzacji OLE obsługi błędów informacje przy użyciu `ICreateErrorInfo` interfejsu. (Przykład `CATCH_ALL_DUAL` makr znajduje się w pliku MFCDUAL. H w [acdual —](../visual-cpp-samples.md) próbki. Funkcji wywoływanych przez nią do obsługi wyjątków, `DualHandleException`, znajduje się w pliku MFCDUAL. CPP.) `CATCH_ALL_DUAL` określa wróć w oparciu o typ wyjątku, który wystąpił kod błędu:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) — w tym przypadku `HRESULT` jest tworzony przy użyciu następującego kodu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Spowoduje to utworzenie `HRESULT` specyficzne dla interfejsu, który spowodował wyjątek. Kod błędu jest przesunięty 0x200, aby uniknąć konfliktów z zdefiniowaną przez system `HRESULT`pod kątem standardowe interfejsy OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) — w tym przypadku `E_OUTOFMEMORY` jest zwracana.

- — W tym przypadku innych wyjątków `E_UNEXPECTED` jest zwracana.

Aby wskazać, że jest używana procedura obsługi błędów automatyzacji OLE, należy także zaimplementować `ISupportErrorInfo` interfejsu.

Najpierw należy dodać kod do swojej definicji klasy automatyzacji, aby pokazać, obsługuje on `ISupportErrorInfo`.

Po drugie, Dodaj kod do mapę interfejsu klasy automatyzacji, aby skojarzyć `ISupportErrorInfo` implementacji klasy z biblioteki MFC `QueryInterface` mechanizm. `INTERFACE_PART` Instrukcji odpowiada klasy zdefiniowanej dla `ISupportErrorInfo`.

Na koniec implementuje klasy zdefiniowane w celu obsługi `ISupportErrorInfo`.

( [Acdual —](../visual-cpp-samples.md) sample zawiera trzy makra, aby pomóc, wykonaj następujące trzy kroki `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, i `IMPLEMENT_DUAL_ERRORINFO`, wszystkie zawarte w MFCDUAL. H.)

Poniższy przykład implementuje klasy zdefiniowanej w celu obsługi `ISupportErrorInfo`. `CAutoClickDoc` jest nazwą klasy automatyzacji i `IID_IDualAClick` jest **IID** dla interfejsu, który jest źródłem błędów zgłoszonych przez obiekt automatyzacji OLE błąd:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
