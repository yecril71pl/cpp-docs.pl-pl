---
title: 'TN065: Obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE'
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 1508b5219f7bb7fd2e9c9a56c42c30bb99686804
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630393"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065: Obsługa podwójnego interfejsu w przypadku serwerów automatyzacji OLE

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

W tym artykule omówiono sposób dodawania obsługi podwójnego interfejsu do aplikacji serwera automatyzacji OLE opartej na bibliotece MFC. Przykład [ACDUAL](../overview/visual-cpp-samples.md) ilustruje obsługę dwóch interfejsów, a przykładowy kod w tej notatce jest pobierany z ACDUAL. Makra opisane w tej notatce, takie jak DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART i IMPLEMENT_DUAL_ERRORINFO, są częścią przykładu ACDUAL i znajdują się w MFCDUAL. C.

## <a name="dual-interfaces"></a>Podwójne interfejsy

Chociaż Automatyzacja OLE umożliwia implementację `IDispatch` interfejsu, interfejsu VTBL lub podwójnego interfejsu (co obejmuje obie te funkcje), firma Microsoft zdecydowanie zaleca zaimplementowanie podwójnych interfejsów dla wszystkich uwidocznionych obiektów automatyzacji OLE. Dwa interfejsy mają znaczące zalety tylko `IDispatch`w przypadku interfejsów VTBL lub tylko do odczytu:

- Powiązanie może odbywać się w czasie kompilacji za pomocą interfejsu VTBL lub w czasie `IDispatch`wykonywania.

- Kontrolery automatyzacji OLE, które mogą korzystać z interfejsu VTBL, mogą korzystać z ulepszonej wydajności.

- Istniejące kontrolery automatyzacji OLE, które używają `IDispatch` interfejsu, będą nadal działały.

- Interfejs VTBL jest łatwiejszy do wywołania z programu C++.

- Aby zapewnić zgodność z funkcjami obsługi obiektów Visual Basic, wymagane są dwa interfejsy.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Dodawanie obsługi podwójnego interfejsu do klasy opartej na CCmdTarget

Podwójny interfejs jest naprawdę tylko interfejsem niestandardowym pochodnym `IDispatch`. Najbardziej prostym sposobem implementacji obsługi podwójnego interfejsu w `CCmdTarget`klasie opartej na systemie jest najpierw wdrożenie normalnego interfejsu wysyłania w klasie za pomocą MFC i ClassWizard, a następnie dodanie interfejsu niestandardowego później. W większości przypadków implementacja interfejsu niestandardowego zostanie po prostu oddelegowana do implementacji MFC `IDispatch` .

Najpierw zmodyfikuj plik ODL dla serwera, aby zdefiniować podwójne interfejsy dla obiektów. Aby zdefiniować podwójny interfejs, należy użyć instrukcji interfejsu zamiast `DISPINTERFACE` instrukcji generowanej przez kreatorów wizualizacji. C++ Zamiast usuwać istniejącą `DISPINTERFACE` instrukcję, Dodaj nową instrukcję interfejsu. Zachowując `DISPINTERFACE` formularz, można nadal używać ClassWizard do dodawania właściwości i metod do obiektu, ale do instrukcji interfejsu należy dodać równoważne właściwości i metody.

Instrukcja interfejsu dla podwójnego interfejsu musi mieć *OleAutomation* i *podwójne* atrybuty, a interfejs musi pochodzić od `IDispatch`. Możesz użyć przykładu [Guidgen](../overview/visual-cpp-samples.md) , aby utworzyć **Identyfikator IID** dla podwójnego interfejsu:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Po umieszczeniu w miejscu instrukcji interfejsu Rozpocznij Dodawanie wpisów dla metod i właściwości. W przypadku podwójnych interfejsów należy ponownie rozmieścić listy parametrów, tak aby metody i metoda dostępu do właściwości w podwójnym interfejsie zwracały **wynik HRESULT** i przekazywać wartości zwracane jako parametry z `[retval,out]`atrybutami. Należy pamiętać, że w przypadku właściwości należy dodać funkcję dostępu Odczyt (`propget`) i zapis (`propput`) z tym samym identyfikatorem. Na przykład:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

Po zdefiniowaniu metod i właściwości należy dodać odwołanie do instrukcji Interface w instrukcji coclass. Na przykład:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

Po zaktualizowaniu pliku ODL Użyj mechanizmu mapy interfejsu MFC, aby zdefiniować klasę implementacji dla podwójnego interfejsu w klasie obiektu i wprowadzić odpowiednie wpisy w `QueryInterface` mechanizmie MFC. Musisz mieć jeden wpis w `INTERFACE_PART` bloku dla każdego wpisu w instrukcji interfejsu ODL oraz wpisy dla interfejsu wysyłania. Każdy wpis ODL z atrybutem *propput* wymaga funkcji o nazwie `put_propertyname`. Każdy wpis z atrybutem *propget* wymaga funkcji o nazwie `get_propertyname`.

Aby zdefiniować klasę implementacji dla podwójnego interfejsu, Dodaj `DUAL_INTERFACE_PART` blok do definicji klasy obiektu. Na przykład:

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

Aby nawiązać połączenie z mechanizmem [QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object) o podwójnym interfejsie `INTERFACE_PART` MFC, Dodaj wpis do mapy interfejsu:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Następnie musisz wypełnić implementację interfejsu. W większości przypadków będzie można delegować do istniejącej implementacji MFC `IDispatch` . Na przykład:

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

Dla metod obiektu i funkcji dostępu do właściwości należy uzupełnić implementację. Metody i funkcje właściwości mogą zwykle delegować do metod wygenerowanych za pomocą ClassWizard. Jeśli jednak właściwości są skonfigurowane do bezpośredniego dostępu do zmiennych, należy napisać kod w celu uzyskania/przełączenia wartości do zmiennej. Przykład:

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

Przekazywanie wskaźnika podwójnego interfejsu nie jest proste, zwłaszcza jeśli trzeba wywołać `CCmdTarget::FromIDispatch`. `FromIDispatch`działa tylko na `IDispatch` wskaźnikach MFC. Jednym ze sposobów obejścia tego problemu jest zapytanie o oryginalny `IDispatch` wskaźnik ustawiony przez MFC i przekazanie tego wskaźnika do funkcji, które go potrzebują. Na przykład:

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

Przed przekazaniem wskaźnika z powrotem za pośrednictwem metody podwójnego interfejsu, może być konieczne przekonwertowanie jej `IDispatch` ze wskaźnika MFC na wskaźnik podwójnego interfejsu. Przykład:

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

AppWizard nie generuje kodu w celu zarejestrowania biblioteki typów aplikacji serwera automatyzacji OLE w systemie. Chociaż istnieją inne sposoby zarejestrowania biblioteki typów, wygodnie jest, aby aplikacja rejestrował bibliotekę typów podczas aktualizowania informacji o typie OLE, to jest zawsze, gdy aplikacja jest uruchamiana autonomicznie.

Aby zarejestrować bibliotekę typów aplikacji za każdym razem, gdy aplikacja jest uruchamiana autonomicznie:

- Uwzględnij 'AFXCTL. H w standardzie obejmuje plik nagłówka, STDAFX. H, aby uzyskać dostęp do definicji `AfxOleRegisterTypeLib` funkcji.

- W `InitInstance` funkcji aplikacji Znajdź `COleObjectFactory::UpdateRegistryAll`wywołanie. Po tym wywołaniu Dodaj wywołanie do `AfxOleRegisterTypeLib`, określając **identyfikatora LIBID** odpowiadające bibliotece typów, wraz z nazwą biblioteki typów:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Modyfikowanie ustawień kompilacji projektu w celu uwzględnienia zmian w bibliotece typów

Aby zmodyfikować ustawienia kompilacji projektu, tak aby plik nagłówkowy zawierający definicje **UUID** był generowany przez MkTypLib za każdym razem, gdy biblioteka typów zostanie odbudowana:

1. W menu **kompilacja** kliknij pozycję **Ustawienia**, a następnie wybierz plik ODL z listy plików dla każdej konfiguracji.

2. Kliknij kartę **typy OLE** i określ nazwę pliku w polu Nazwa pliku **nagłówku danych wyjściowych** . Użyj nazwy pliku, która nie jest jeszcze używana przez projekt, ponieważ MkTypLib zastąpi istniejący plik. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia kompilacji** .

Aby dodać definicje **UUID** z MkTypLibego pliku nagłówkowego do projektu:

1. Dołącz plik nagłówka MkTypLib-generaty do pliku nagłówkowego w warstwie Standardowa, *stdafx. h*.

2. Utwórz nowy plik INITIIDS. CPP i dodaj go do projektu. W tym pliku Uwzględnij plik nagłówka MkTypLib, po uwzględnieniu OLE2. H i INITGUID. C

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. W menu **kompilacja** kliknij pozycję **Ustawienia**, a następnie wybierz pozycję INITIIDS. CPP z listy plików dla każdej konfiguracji.

4. Kliknij **C++** kartę, kliknij pozycję kategorie **prekompilowane nagłówki**, a następnie wybierz przycisk radiowy **nie używa prekompilowanych nagłówków** . Kliknij przycisk OK, aby zamknąć okno dialogowe **Ustawienia kompilacji** .

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Określanie prawidłowej nazwy klasy obiektu w bibliotece typów

Kreatory dostarczone z wizualizacją C++ nieprawidłowo wykorzystują nazwę klasy implementacji, aby określić klasę coclass w pliku ODL serwera dla klas, które umożliwiają tworzenie OLE. Chociaż ta funkcja będzie działała, nazwa klasy implementacji prawdopodobnie nie jest nazwą klasy, która ma być używana przez użytkowników obiektu. Aby określić poprawną nazwę, Otwórz plik ODL, Znajdź każdą instrukcję coclass i zastąp nazwę klasy implementacji poprawną nazwą zewnętrzną.

Należy zauważyć, że po zmianie instrukcji coclass, nazwy zmiennych **identyfikatora CLSID**s w pliku nagłówkowym MkTypLib. Musisz zaktualizować swój kod, aby użyć nowych nazw zmiennych.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Obsługa wyjątków i interfejsów błędów automatyzacji

Metody obiektu automatyzacji i funkcje metody dostępu do właściwości mogą generować wyjątki. Jeśli tak, należy je obsłużyć w implementacji o podwójnym interfejsie i przekazać informacje o wyjątku z powrotem do kontrolera za pomocą interfejsu `IErrorInfo`obsługi błędów automatyzacji OLE. Ten interfejs zapewnia szczegółowe, kontekstowe informacje o błędzie za `IDispatch` poorednictwem obu interfejsów i VTBL. Aby wskazać, że program obsługi błędów jest dostępny, należy zaimplementować `ISupportErrorInfo` interfejs.

Aby zilustrować mechanizm obsługi błędów, należy założyć, że funkcje wygenerowane przez ClassWizard służące do implementowania standardowych wyjątków do obsługi wysyłania. Implementacja `IDispatch::Invoke` MFC zwykle przechwytuje te wyjątki i konwertuje je na strukturę EXCEPTINFO, która jest zwracana `Invoke` przez wywołanie. Jeśli jednak używany jest interfejs VTBL, użytkownik jest odpowiedzialny za przechwycenie wyjątków samodzielnie. Jak na przykład chronić metody podwójnego interfejsu:

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

`CATCH_ALL_DUAL`w przypadku wystąpienia wyjątku należy zwrócić uwagę na zwrócenie poprawnego kodu błędu. `CATCH_ALL_DUAL`Konwertuje wyjątek MFC na informacje o obsłudze błędów automatyzacji OLE przy użyciu `ICreateErrorInfo` interfejsu. (Przykładowe `CATCH_ALL_DUAL` makro znajduje się w pliku MFCDUAL. H w próbce [ACDUAL](../overview/visual-cpp-samples.md) . Funkcja, która wywołuje do obsługi wyjątków, `DualHandleException`jest w pliku MFCDUAL. CPP). `CATCH_ALL_DUAL` określa kod błędu, który ma zostać zwrócony na podstawie typu wyjątku, który wystąpił:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) — w tym przypadku `HRESULT` jest konstruowany przy użyciu następującego kodu:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   Spowoduje to utworzenie `HRESULT` określonego interfejsu, który spowodował wyjątek. Kod błędu jest przesunięty przez 0x200, aby uniknąć konfliktów ze zdefiniowanym `HRESULT`przez system elementem s dla standardowych interfejsów OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) — w tym przypadku `E_OUTOFMEMORY` jest zwracany.

- Każdy inny wyjątek — w tym przypadku `E_UNEXPECTED` jest zwracany.

Aby wskazać, że jest używany program obsługi błędów automatyzacji OLE, należy również zaimplementować `ISupportErrorInfo` interfejs.

Najpierw Dodaj kod do definicji klasy automatyzacji, aby go `ISupportErrorInfo`wyświetlić.

Następnie Dodaj kod do mapy interfejsu klasy automatyzacji, aby skojarzyć `ISupportErrorInfo` klasę implementacji z `QueryInterface` mechanizmem MFC. Instrukcja pasuje do klasy zdefiniowanej dla `ISupportErrorInfo`. `INTERFACE_PART`

Na koniec Zaimplementuj klasę zdefiniowaną do `ISupportErrorInfo`obsługi.

( [ACDUAL](../overview/visual-cpp-samples.md) próbka zawiera trzy makra, które pomagają wykonać te trzy kroki `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`,, `IMPLEMENT_DUAL_ERRORINFO`i, wszystkie zawarte w MFCDUAL. H)

W poniższym przykładzie przedstawiono implementację klasy zdefiniowanej `ISupportErrorInfo`do obsługi. `CAutoClickDoc`jest nazwą klasy automatyzacji i `IID_IDualAClick` jest identyfikatorem **IID** dla interfejsu, który jest źródłem błędów raportowanych za pośrednictwem obiektu błędu automatyzacji OLE:

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

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
