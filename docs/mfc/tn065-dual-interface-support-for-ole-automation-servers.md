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
ms.openlocfilehash: e30be46aeab92f63f1b4cba593cda52bf9aeef9a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122186"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE

> [!NOTE]
> Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.

Ta uwaga omówiono sposób dodawania Obsługa podwójnego interfejsu do serwera aplikacji opartego na bibliotece MFC automatyzacji OLE. [Acdual —](../visual-cpp-samples.md) przykładową Obsługa podwójnego interfejsu, a przykładowy kod w tym notatki jest pobierana z acdual —. Makra opisane w tym notatki, takich jak DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART i IMPLEMENT_DUAL_ERRORINFO, są częścią acdual — przykład i znajdują się w MFCDUAL. H.

## <a name="dual-interfaces"></a>Podwójne interfejsy

Mimo że automatyzacji OLE umożliwia wdrożenie `IDispatch` interfejsu, interfejs VTBL lub podwójnym interfejsu (obejmuje zarówno), firma Microsoft zaleca, wdrożenie podwójne interfejsy, dla wszystkich uwidocznione obiekty automatyzacji OLE. Podwójne interfejsy mają istotne korzyści `IDispatch`-tylko lub w trybie tylko do VTBL interfejsów:

- Powiązanie może odbywać się za pośrednictwem interfejsu VTBL w czasie kompilacji lub w czasie wykonywania za pośrednictwem `IDispatch`.

- Kontrolery automatyzacji OLE, których można użyć interfejsu VTBL mogą korzystać z lepszą wydajność.

- Istniejące kontrolery automatyzacji OLE, które używają `IDispatch` interfejsu będą nadal działać.

- Interfejs VTBL jest łatwiejsze do wywołania z C++.

- Podwójne interfejsy są wymagane do zapewnienia zgodności z funkcji obsługi obiektu Visual Basic.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Dodawanie Obsługa podwójnego interfejsu na podstawie CCmdTarget — klasa

Podwójna interfejs jest naprawdę tylko niestandardowy interfejs pochodny `IDispatch`. Najbardziej oczywistym sposobem wykonania Obsługa podwójnego interfejsu w `CCmdTarget`— na podstawie klasy jest wdrożenie pierwszego wysyłania normalne interfejsu w klasie za pomocą MFC i ClassWizard, a następnie dodaj niestandardowy interfejs później. W większości przypadków implementacji niestandardowy interfejs po prostu delegować do MFC `IDispatch` implementacji.

Najpierw należy zmodyfikować plik ODL dla serwera zdefiniować dwa interfejsy dla obiektów. Aby zdefiniować dwa interfejsu, należy użyć instrukcji interfejsu zamiast `DISPINTERFACE` instrukcji, który generuje kreatorów Visual C++. Zamiast usuwania istniejących `DISPINTERFACE` instrukcji, Dodaj nowe oświadczenie interfejsu. Zachowując `DISPINTERFACE` formularza, można nadal używać ClassWizard można dodać właściwości i metody do obiektu, ale należy dodać równoważne właściwości i metod do instrukcji interfejsu.

Interface — instrukcja podwójną interfejsu muszą mieć *OLEAUTOMATION* i *PODWÓJNĄ* atrybutów i interfejs musi pochodzić z `IDispatch`. Można użyć [GUIDGEN](../visual-cpp-samples.md) przykład, aby utworzyć **IID** podwójną interfejsu:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Po utworzeniu interface — instrukcja w miejscu, należy uruchomić dodanie wpisów dla metody i właściwości. Podwójne interfejsy należy zmienić kolejność listy parametrów, aby powrócić metod, a funkcje metod dostępu właściwości w interfejsie podwójną **HRESULT** i ich zwracanych wartości przekazywane jako parametry atrybutów `[retval,out]`. Należy pamiętać, że dla właściwości, należy dodać zarówno do odczytu (`propget`) i zapisu (`propput`) dostęp do funkcji o tym samym identyfikatorze. Na przykład:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Po zdefiniowaniu właściwości i metody, należy dodać odwołanie do interfejsu instrukcji w instrukcji coclass. Na przykład:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Po zaktualizowaniu pliku ODL, należy używać mechanizmu mapy interfejsu MFC, aby zdefiniować klasa implementacji interfejsu podwójna w klasie obiektów i ustaw odpowiednie pozycje w MFC `QueryInterface` mechanizmu. Potrzebujesz jednego wpisu w `INTERFACE_PART` blok dla każdego wpisu w instrukcji interfejsu ODL, a także wpisy dla wysyłania interfejsu. Każdy wpis ODL z *propput* atrybut wymaga funkcji o nazwie `put_propertyname`. Każdy wpis z *propget* atrybut wymaga funkcji o nazwie `get_propertyname`.

Aby zdefiniować klasa implementacji dla dwóch interfejsu, Dodaj `DUAL_INTERFACE_PART` bloku do definicji klasy obiektu. Na przykład:

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

Nawiązać dwie interfejsu MFC [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) mechanizmu, Dodaj `INTERFACE_PART` wpisu do mapy interfejsu:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Następnie należy wypełnić implementacji interfejsu. W większości przypadków będzie można delegować do istniejących MFC `IDispatch` implementacji. Na przykład:

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

Dla metody i funkcje metod dostępu właściwości do obiektu musisz wypełnić implementacji. Metody i właściwości funkcji ogólnie można delegować do metody wygenerowanych przy użyciu ClassWizard. Jednak jeśli skonfigurowano dostęp do zmiennych bezpośrednio właściwości należy napisać kod, aby get/put wartość do zmiennej. Na przykład:

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

## <a name="passing-dual-interface-pointers"></a>Przekazywanie wskaźniki podwójnego interfejsu

Przekazanie wskaźnika podwójnego interfejsu nie jest proste, zwłaszcza, jeśli należy wywołać `CCmdTarget::FromIDispatch`. `FromIDispatch` działa tylko na MFC `IDispatch` wskaźników. Aby obejść ten problem jest zapytania dla oryginalnej `IDispatch` zestaw wskaźnika Konfigurowanie przez MFC i że wskaźnikiem do funkcji, które go potrzebują. Na przykład:

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

Przed przekazaniem ich wskaźnik z powrotem przy użyciu metody podwójnego interfejsu, konieczne może być przekonwertować ją z MFC `IDispatch` wskaźnika do wskaźnika podwójnego interfejsu. Na przykład:

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

## <a name="registering-the-applications-type-library"></a>Rejestrowanie biblioteki typów aplikacji

Kreatorami AppWizard nie generuje kod, aby zarejestrować biblioteki typów aplikację serwera automatyzacji OLE w systemie. Jeśli istnieją inne sposoby zarejestrować biblioteki typów, jest wygodne zgłoszenia zarejestrować biblioteki typów, podczas aktualizacji jego informacje o typie OLE, oznacza to, że przy każdym uruchomieniu aplikacji autonomicznej.

Aby zarejestrować autonomiczne biblioteki typów aplikacji przy każdym uruchomieniu aplikacji:

- Obejmują AFXCTL. H w użytkownika standardowego zawiera plik nagłówka, STDAFX. H, do definicji `AfxOleRegisterTypeLib` funkcji.

- W aplikacji `InitInstance` funkcji, Znajdź wywołanie `COleObjectFactory::UpdateRegistryAll`. Po to wywołanie, dodaj wywołanie do `AfxOleRegisterTypeLib`, określania **identyfikatora LIBID** odpowiadającego do biblioteki typów, oraz nazwę biblioteki typów:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modyfikowanie ustawień kompilacji projektu, w zależności od typu biblioteki zmian

Aby zmodyfikować ustawienia kompilacji projektu, aby plik nagłówka zawierający **UUID** definicje jest generowany przez mktyplib — odbudowaniu biblioteki typów:

1. Na **kompilacji** menu, kliknij przycisk **ustawienia**, a następnie wybierz plik ODL z listy plików dla każdej konfiguracji.

2. Kliknij przycisk **typy OLE** i określ nazwę pliku w **nagłówku wyjściowym** pola nazwy pliku. Nazwa pliku, który nie jest już używany w projekcie, należy użyć, ponieważ mktyplib — zastąpią wszystkie istniejące pliki. Kliknij przycisk **OK** zamknąć **ustawieniach kompilacji** okno dialogowe.

Aby dodać **UUID** definicje z pliku nagłówka wygenerowane mktyplib — do projektu:

1. Obejmują generowanych mktyplib — plik nagłówka w użytkownika standardowego zawiera plik nagłówka, STDAFX. H.

2. Utwórz nowy plik INITIIDS. CPP i dodaj go do projektu. W tym pliku należy uwzględnić plik nagłówka wygenerowane mktyplib — po dołączeniu OLE2. H i INITGUID. H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. Na **kompilacji** menu, kliknij przycisk **ustawienia**, a następnie wybierz INITIIDS. CPP z listy plików dla każdej konfiguracji.

4. Kliknij przycisk **C++** , kliknij pozycję kategorii **prekompilowanych nagłówków**i wybierz **prekompilowane nagłówki nie są używane** przycisk radiowy. Kliknij przycisk OK, aby zamknąć **ustawieniach kompilacji** okno dialogowe.

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Określenie nazwy klasy prawidłowy obiekt w bibliotece typów

Kreatorów niepoprawnie dostarczanego z programem Visual C++ Użyj nazwy klasy implementacji, aby określić klasy coclass w pliku ODL serwera dla klas możliwość utworzenia OLE. Gdy to będzie działać, nazwa klasy implementacji prawdopodobnie nie jest nazwą klasy, użytkownicy obiektu do użycia. Podaj poprawną nazwę Otwórz plik ODL, każda instrukcja coclass Znajdź i zastąp nazwę klasy implementacji z poprawną nazwą zewnętrznego.

Należy pamiętać, że po zmianie instrukcji coclass nazwy zmiennej **CLSID**s w pliku nagłówka wygenerowane mktyplib — zostanie zmieniona. Musisz zaktualizować kod, aby używał nowej nazwy zmiennych.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Obsługa wyjątków i interfejsów błąd automatyzacji

Metody i właściwości funkcje obiektu automatyzacji może zgłaszać wyjątków. Jeśli tak, należy je obsłużyć w implementacji podwójnego interfejsu i przekazywania informacji o wyjątku do kontrolera za pomocą interfejsu obsługi błędów automatyzacji OLE, `IErrorInfo`. Ten interfejs zawiera szczegółowe, kontekstowe błąd informacji za pomocą obu `IDispatch` i VTBL interfejsy. Aby wskazać, że program obsługi błędów jest dostępna, należy zaimplementować `ISupportErrorInfo` interfejsu.

Aby zilustrować mechanizm obsługi błędów, założono zgłaszają wyjątki, że funkcje generowane ClassWizard używaną do zaimplementowania pomocy technicznej standard wysyłania. Implementacja interfejsu MFC `IDispatch::Invoke` zwykle przechwytuje te wyjątki i konwertuje je na strukturę EXCEPTINFO, który jest zwracany za pomocą `Invoke` wywołania. Jednak w przypadku interfejsu VTBL jest odpowiedzialny za przechwytywanie wyjątków samodzielnie. Na przykład ochrony metody podwójnego interfejsu:

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

`CATCH_ALL_DUAL` odpowiada on za zwróciło kod Napraw błąd, po wystąpieniu wyjątku. `CATCH_ALL_DUAL` Konwertuje wyjątek MFC do automatyzacji OLE obsługi błędów informacje przy użyciu `ICreateErrorInfo` interfejsu. (Przykład `CATCH_ALL_DUAL` znajduje się w pliku MFCDUAL. H w [acdual —](../visual-cpp-samples.md) próbki. Funkcja wywołuje do obsługi wyjątków, `DualHandleException`, znajduje się w pliku MFCDUAL. CPP.) `CATCH_ALL_DUAL` określa do zwrócenia oparte na typ wyjątku, który wystąpił kod błędu:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) — w takim przypadku `HRESULT` jest tworzony przy użyciu następującego kodu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     Spowoduje to utworzenie `HRESULT` specyficzne dla interfejsu, który spowodował wyjątek. Kod błędu zostanie przesunięty o 0x200 w celu uniknięcia konfliktów z zdefiniowana w systemie `HRESULT`s dla standardowych interfejsów OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) — w takim przypadku `E_OUTOFMEMORY` jest zwracany.

- Inne wyjątek — w tym przypadku `E_UNEXPECTED` jest zwracany.

Aby wskazać, że używany jest program obsługi błędów automatyzacji OLE, powinny również implementować `ISupportErrorInfo` interfejsu.

Najpierw dodaj kod do definicji klasy automatyzacji do wyświetlenia, obsługuje on `ISupportErrorInfo`.

Po drugie, Dodaj kod do mapy interfejsu klasy automatyzacji do skojarzenia `ISupportErrorInfo` implementacji klasy MFC `QueryInterface` mechanizmu. `INTERFACE_PART` Instrukcji odpowiada zdefiniowanej dla klasy `ISupportErrorInfo`.

Na koniec zaimplementować klasa zdefiniowana do obsługi `ISupportErrorInfo`.

( [Acdual —](../visual-cpp-samples.md) próbka zawiera trzy makra, wykonaj następujące trzy kroki, aby `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, i `IMPLEMENT_DUAL_ERRORINFO`, wszystkie zawarte w MFCDUAL. H)

Poniższy przykład implementuje klasy zdefiniowanej do obsługi `ISupportErrorInfo`. `CAutoClickDoc` Nazwa klasy automatyzacji i `IID_IDualAClick` jest **IID** dla interfejsu, który jest źródłem błędów zgłaszanych przez obiekt automatyzacji OLE błąd:

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
