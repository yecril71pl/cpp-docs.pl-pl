---
title: 'TN038: Implementacja interfejsu MFC / OLE IUnknown'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 0722ce294e6a088446b8ba681810cf3f7885f122
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571434"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: implementacja interfejsu MFC/OLE IUnknown

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Istotą OLE 2 jest "OLE Component Object Model" lub model COM. COM zdefiniowano standard dla obiektów współpracujących, jak mają komunikować się ze sobą. Obejmuje to szczegóły "obiektu" wygląda podobnie, w tym jak metody są wysyłane do obiektu. COM definiuje również klasę bazową, z której pochodzą wszystkie zgodne klasy COM. Ta klasa bazowa jest [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Mimo że [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfejsu nosi nazwę klasy języka C++, COM nie jest specyficzny dla żadnego poszczególnego języka — może być implementowana w języku C, PASCAL lub dowolnym innym języku, który może obsługiwać układ binarny obiektu COM.

Mechanizmie OLE wszystkie klasy pochodne od [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) nazywane "interfejsami". Jest to istotna różnica, gdyż "interfejs" taki jak [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) niesie ze sobą implementacji. Po prostu definiuje protokół, przez którą komunikują się obiekty, nie szczegóły tego, co zrobią te implementacje. Ma to uzasadnienie dla systemu, który pozwala, aby zapewnić maksymalną elastyczność. To zadanie biblioteki MFC, aby zaimplementować domyślne zachowanie dla programów MFC/C++.

Aby zrozumieć implementację MFC [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) musisz najpierw zrozumieć, jaka jest tego interfejsu. Uproszczoną wersję [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) określono poniżej:

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> Niektóre niezbędne szczegóły konwencji wywoływania, takie jak `__stdcall` pozostawiono na tej ilustracji.

[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) funkcji elementów członkowskich kontrolują zarządzanie pamięcią obiektu. COM używa schematu obliczeń odwołania do śledzenia obiektów. Nigdy nie odwołuje się do obiektu bezpośrednio, tak jak w języku C++. Zamiast tego obiekty COM zawsze są wywoływane za pomocą wskaźnika. Aby zwolnić obiekt, gdy właściciel jest wykonywane przy użyciu jego, obiekt [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) wywołaniu elementu członkowskiego (w przeciwieństwie do używania operatora Usuń, jak dla tradycyjnego obiektu języka C++). Mechanizm zliczania odwołań zezwala na wiele odwołań do jednego obiektu, mają być zarządzane. Implementacja [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) przechowuje licznik odwołań obiektu — obiekt nie zostanie usunięty, dopóki jego licznik odwołań osiągnie zero.

[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) działa dość prosto z punktu widzenia wdrażania. Oto prosta implementacja:

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkcja członkowska jest nieco bardziej interesująca. Nie jest to bardzo interesujące mieć obiekt, którego jedynymi funkcjami Członkowskimi są [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) — dobrze byłoby powiedzieć obiektowi, aby zrobił coś więcej niż [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) udostępnia. Jest to miejsce [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) przydaje się. Umożliwia uzyskanie innego "interfejsu" dla tego samego obiektu. Te interfejsy są zazwyczaj uzyskiwane z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) i dodają dodatkową funkcję, dodając nowe funkcje Członkowskie. Interfejsy COM nigdy nie mają zmiennych zadeklarowanych w interfejsie, a wszystkie funkcje składowe są deklarowane jako czysto wirtualne. Na przykład

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Aby uzyskać IPrintInterface, jeśli masz tylko [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), wywołaj [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) przy użyciu `IID` z `IPrintInterface`. `IID` Jest 128-bitową liczbą, która unikatowo identyfikuje interfejs. Brak `IID` dla każdego interfejsu, który definiuje użytkownik lub OLE. Jeśli *pUnk* jest wskaźnikiem do [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) obiektu może być kod, aby pobrać obiekt IPrintInterface z niego:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Wydaje się to dość proste, ale jak zaimplementujesz obiekt, który obsługuje zarówno interfejs IPrintInterface i [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfejs w tym przypadku jest proste, ponieważ interfejs IPrintInterface pochodzi bezpośrednio z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) — implementując interfejs iprintinterface, interfejs [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) jest obsługiwana automatycznie. Na przykład:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Implementacje [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) będą dokładnie takie same jak te implementowane powyżej. `CPrintObj::QueryInterface` będzie to wyglądać mniej więcej tak:

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

Jak widać, jeśli identyfikator interfejsu (IID) jest rozpoznawany, wskaźnik jest zwracany do obiektu; w przeciwnym razie wystąpi błąd. Należy również zauważyć, że pomyślny [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) powoduje skutkują domniemanymi [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Oczywiście można również musi zostać zaimplementowany obiekt CEditObj::Print. To proste, ponieważ interfejs IPrintInterface pochodzi bezpośrednio od [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfejsu. Jednakże, jeśli chce się obsługiwać dwa różne interfejsy, oba pochodzące z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), Uwzględnij następujące kwestie:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

Chociaż istnieje wiele różnych sposobów wdrażania klasy pomocniczej zarówno IEditInterface, jak i IPrintInterface, w tym przy użyciu języka C++ wielokrotnego dziedziczenia, ta notatka koncentruje się na korzystanie z klas zagnieżdżonych w celu zaimplementowania tej funkcji.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

Cała implementacja znajduje się poniżej:

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

Należy zauważyć, że większość [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implementacja jest umieszczany w klasie CEditPrintObj a nie powiela kod w obiektach CEditPrintObj::CEditObj i CEditPrintObj::CPrintObj. Zmniejsza ilość kodu i pozwala uniknąć błędów. Kluczowym punktem tutaj jest, że z interfejsu IUnknown jest możliwe do wywołania [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) Aby pobrać dowolny interfejs może obsługiwać obiekt, i z każdego z tych interfejsów można robić to samo. Oznacza to, że wszystkie [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkcje, które są dostępne z każdego interfejsu muszą zachowywać się dokładnie tak samo. Aby te obiekty osadzone wywoływały implementację w "obiekcie zewnętrznym" wskaźnik jest używane zwrotny (m_pParent). Wskaźnik m_pParent jest inicjowany podczas konstruktora CEditPrintObj. Następnie możesz również zaimplementować ceditprintobj::ceditobj:: Editobject i ceditprintobj::cprintobj:: printobject. Znacznej kodu została dodana w celu dodania jednej funkcji — możliwość edycji obiektu. Na szczęście jest dość rzadko interfejsy mają tylko pojedynczą funkcję członkowską (choć zdarza się to), a w tym przypadku funkcje EditObject i PrintObject byłyby zwykle połączone w pojedynczy interfejs.

To dużo wyjaśnień i duża ilość kodu dla tak prostego scenariusza. Klasy MFC/OLE zapewniają prostszą alternatywę. Implementacja MFC wykorzystuje technikę podobną to sposobu Windows wiadomości zostaną opakowane z mapami wiadomości. Ten obiekt jest nazywany *mapy interfejsu* i jest omówiona w następnej sekcji.

## <a name="mfc-interface-maps"></a>Mapy interfejsów biblioteki MFC

MFC/OLE zawiera implementację "Map interfejsów" podobną do "Map komunikatów" i "Map wysyłania" MFC w koncepcji i wykonywania. Podstawowe funkcje map interfejsu MFC są następujące:

- Standardowa implementacja [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), zbudowana w `CCmdTarget` klasy.

- Konserwacja licznika odwołań zmodyfikowanego przez [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wydania](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)

- Implementacja danych [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))

Ponadto mapy interfejsu obsługują następujące zaawansowane funkcje:

- Obsługa tworzenia kumulowane obiektów COM

- Obsługa korzystania z obiektów agregacji w implementacji obiektu COM

- Implementacja jest możliwość bycia wywoływaną i rozszerzalny

Aby uzyskać więcej informacji na temat agregacji, zobacz [agregacji](/windows/desktop/com/aggregation) tematu.

Obsługa mapy interfejsu biblioteki MFC jest ścieżką w `CCmdTarget` klasy. `CCmdTarget` "*ma a*" odwoływać się do liczby, a także wszystkie funkcje składowe związane z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implementacji (liczba odwołań na przykład znajduje się w `CCmdTarget`). Aby utworzyć klasę, która obsługuje OLE COM, należy wyprowadzić klasę z `CCmdTarget` i korzystać z różnych makr oraz funkcji Członkowskich z `CCmdTarget` Aby zaimplementować pożądane interfejsy. Implementacja biblioteki MFC używa klas zagnieżdżonych do definiowania każdej implementacji interfejsu, podobnie jak w powyższym przykładzie. To jest łatwiejsze dzięki standardowej implementacji IUnknown, a także wielu makr, które eliminują część powtarzającego się kodu.

## <a name="interface-map-basics"></a>Podstawowe informacje o mapie interfejsu

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Aby zaimplementować klasę przy użyciu interfejsu MFC mapy

1. Pochodną klasę bezpośrednio lub pośrednio `CCmdTarget`.

2. Użyj `DECLARE_INTERFACE_MAP` funkcji w definicji klasy pochodnej.

3. Dla każdego interfejsu, którą chcesz obsługiwać użyj makra BEGIN_INTERFACE_PART i END_INTERFACE_PART w definicji klasy.

4. W pliku implementacji Użyj makr BEGIN_INTERFACE_MAP i END_INTERFACE_MAP zdefiniować mapę interfejsu klasy.

5. Dla każdego obsługiwanego identyfikatora IID użyj makra INTERFACE_PART między BEGIN_INTERFACE_MAP i END_INTERFACE_MAP makra do zmapowania tego identyfikatora IID na określoną "część" klasy.

6. Zaimplementuj każdą z klas zagnieżdżonych, które reprezentują interfejsów, które obsługujesz.

7. Umożliwia dostęp do elementu nadrzędnego, METHOD_PROLOGUE — makro `CCmdTarget`-pochodnych obiektu.

8. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) delegować `CCmdTarget` implementacji tych funkcji (`ExternalAddRef`, `ExternalRelease`, i `ExternalQueryInterface`).

Powyższy przykład CPrintEditObj może być wdrażany w następujący sposób:

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

Powyższa deklaracja tworzy klasę pochodną `CCmdTarget`. DECLARE_INTERFACE_MAP — makro informuje szablon, że ta klasa posiadać będzie mapę interfejsu niestandardowego. Ponadto makra BEGIN_INTERFACE_PART i END_INTERFACE_PART definiują klasy zagnieżdżone, w tym przypadku o nazwach CEditObj i CPrintObj (X jest używana tylko do odróżnienia klas zagnieżdżonych od klas globalnych, który rozpoczyna się od "C" i klas, które Zacznij od "I"). Są tworzone dwa elementy zagnieżdżone tych klas: m_CEditObj i m_CPrintObj, odpowiednio. Makra automatycznie deklarują [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkcje; dlatego należy deklarować tylko funkcje specyficzne dla tego interfejsu: Funkcje EditObject i PrintObject (makro OLE STDMETHOD jest używany, aby **_stdcall** i wirtualne słowa kluczowe są dostarczane jako właściwe dla platformy docelowej).

Aby zaimplementować mapę interfejsu dla tej klasy:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Zostanie utworzone połączenie IID_IPrintInterface IID z m_CPrintObj a IID_IEditInterface z m_CEditObj odpowiednio. `CCmdTarget` Implementacji [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) (`CCmdTarget::ExternalQueryInterface`) używa tej mapy do zwracania wskaźników do m_CPrintObj i m_CEditObj, gdy wymagane. Nie jest konieczne dołączyć wpis dla `IID_IUnknown`; środowisko użyje pierwszego interfejsu w mapie (w tym przypadku m_CPrintObj) po `IID_IUnknown` żądania.

Mimo że BEGIN_INTERFACE_PART — makro automatycznie deklaruje [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkcje, możesz nadal trzeba je zaimplementować:

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

Implementacja dla CEditPrintObj::CPrintObj, będzie podobna do powyższych definicji dla CEditPrintObj::CEditObj. Mimo że będzie można utworzyć makro, który może służyć do automatycznego generowania tych funkcji (ale wcześniej w przypadku rozwoju MFC/OLE to miało miejsce), trudno ustawić punkty przerwania, gdy makro generuje więcej niż jeden wiersz kodu. Z tego powodu ten kod jest rozwinięty ręcznie.

Za pomocą implementacji środowiska mapy komunikatów, istnieje kilka rzeczy, które nie były konieczne w celu:

- Implementacja funkcji QueryInterface

- Implementacja funkcji AddRef i Release

- Zadeklaruj jedną z tych metod wbudowanych w obu interfejsów sieci

Ponadto środowisko wykorzystuje mapy komunikatów wewnętrznie. Umożliwia to pochodzi od klasy framework, powiedzmy `COleServerDoc`, która już obsługuje niektóre interfejsy oraz udostępnia zamiany lub dodatki do interfejsów dostarczanych przez szablon. Można to zrobić, ponieważ szablon w pełni obsługuje dziedziczenie mapy interfejsu z klasy bazowej. To jest powód, dlaczego przyjmuje BEGIN_INTERFACE_MAP w jako drugi parametr nazwę klasy bazowej.

> [!NOTE]
> Ogólnie nie jest możliwe ponowne wykorzystanie implementacji wbudowanych implementacji interfejsów OLE MFC tylko przez dziedziczenie osadzonych specjalizacji tego interfejsu z wersji biblioteki MFC. Nie jest to możliwe ponieważ użycie METHOD_PROLOGUE — makro, aby uzyskać dostęp do zawartego `CCmdTarget`— oznacza obiekt pochodnej *stałego przesunięcia* osadzonego obiektu z `CCmdTarget`-pochodzi z obiektu. Oznacza to, na przykład, nie możesz wywodzić osadzonego XMyAdviseSink z implementacji MFC w `COleClientItem::XAdviseSink`, ponieważ XAdviseSink opiera się na byciu w szczególnym przesunięciu od góry `COleClientItem` obiektu.

> [!NOTE]
> Możesz jednak delegować do implementacji MFC dla wszystkich funkcji ma zachowanie domyślne biblioteki MFC. Jest to realizowane w implementacji MFC `IOleInPlaceFrame` (XOleInPlaceFrame) w `COleFrameHook` klasy (przekazuje do m_xOleInPlaceUIWindow dla wielu funkcji). Ten projekt został wybrany do zmniejszenia środowiska uruchomieniowego obiektów, w których zaimplementowano wiele interfejsów; Eliminuje to potrzebę wskaźnik (takie jak sposób w jaki m_pParent został użyty w poprzedniej sekcji).

### <a name="aggregation-and-interface-maps"></a>Agregacja i mapy interfejsu

Oprócz obsługi autonomicznych obiektów COM, biblioteka MFC obsługuje agregację. Agregacja sama w sobie jest zbyt złożonym tematem do omawiania w tym miejscu; Zapoznaj się [agregacji](/windows/desktop/com/aggregation) tematu, aby uzyskać więcej informacji na temat agregacji. Uwaga ta po prostu opisze obsługę agregacji wbudowanej w ramy i mapy interfejsu.

Istnieją dwa sposoby użycia agregacji: (1) za pomocą obiektu COM, który obsługuje agregację i (2) poprzez implementację obiektu, który może być agregowany przez inny. Te możliwości mogą określane jako "za pomocą obiektu agregacji" i "obiekt skumulowany". Biblioteka MFC obsługuje obie.

### <a name="using-an-aggregate-object"></a>Używanie obiektu agregacji

Aby użyć obiektu agregacji, musi być jakiś sposób, aby powiązać agregację z mechanizmem QueryInterface. Innymi słowy obiekt agregacji musi zachowywać się tak, jakby to natywną częścią obiektu. W jaki sposób jest to do mechanizmu mapy interfejsu biblioteki MFC, oprócz INTERFACE_PART — makro, w przypadku, gdy zagnieżdżony obiekt jest mapowany do identyfikatora IID, można również zadeklarować obiekt agregacji jako część Twojego `CCmdTarget` klasy pochodnej. Aby to zrobić, makra INTERFACE_AGGREGATE jest używany. Pozwala na określenie zmiennej członkowskiej (która musi być wskaźnikiem do [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) lub wywodzącej się klasy), który ma zostać włączona do mechanizmu mapy interfejsu. Jeżeli wskaźnik nie ma wartości NULL podczas `CCmdTarget::ExternalQueryInterface` jest wywoływana, środowisko będzie automatycznie wywoływać obiektu agregacji [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkcję członkowską, jeśli `IID` zażądano nie jest jednym z natywnych `IID`s obsługiwane przez `CCmdTarget` sam obiekt.

#### <a name="to-use-the-interfaceaggregate-macro"></a>Aby użyć makra interface_aggregate

1. Zadeklaruj zmienną członkowską ( `IUnknown*`) zawierający wskaźnik do obiektu agregacji.

2. Dołącz makra INTERFACE_AGGREGATE mapę interfejsu, który odnosi się do zmiennej elementu członkowskiego według nazwy.

3. W pewnym momencie (zwykle w ciągu `CCmdTarget::OnCreateAggregates`), zainicjować zmienną członkowską na coś innego niż NULL.

Na przykład:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

Zmienna m_lpAggrInner jest inicjowana w Konstruktorze w wartości NULL. Szablon ignoruje zmienną członkowską NULL w implementacji domyślnej [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). `OnCreateAggregates` jest dobrym miejscem do faktycznie tworzenia obiektów agregacji. Musisz wywołać ją jawnie, jeśli tworzysz obiekt poza implementacją MFC `COleObjectFactory`. Przyczyny tworzenia agregatów w `CCmdTarget::OnCreateAggregates` oraz użycie `CCmdTarget::GetControllingUnknown` staną się jasne po omówieniu tworzenia obiektów kumulowanych omówiono.

Ta technika nada Twojemu obiektowi, wszystkie interfejsy, które obiekt agregacji obsługuje plus jego interfejsy macierzyste. Jeśli chcesz tylko podzbioru interfejsów, które obsługuje agregacja, można zastąpić `CCmdTarget::GetInterfaceHook`. Dzięki temu można bardzo niski poziom możliwości wywoływania, podobny do [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). Zazwyczaj chcesz, aby wszystkie interfejsy, które obsługuje agregat.

### <a name="making-an-object-implementation-aggregatable"></a>Co się agregowaniu implementacji obiektu

Aby uzyskać obiekt można było agregować, implementacja [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) musi delegować do "kontrolowanie nieznane". Innymi słowy, go jako część obiektu, to musi delegować [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) do innego obiektu, również pochodzącego z [ IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). To "kontrolowanie nieznane" jest dostarczana do obiektu podczas jego tworzenia, czyli jest udostępniana wykonania `COleObjectFactory`. Zaimplementowanie tego prowadzi do niewielkiej ilości obciążenia, a w niektórych przypadkach nie jest pożądane, więc MFC sprawia, że jest to opcjonalne. Aby włączyć agregowanie obiektu, należy wywołać `CCmdTarget::EnableAggregation` z konstruktora obiektu.

Jeśli obiekt korzysta również z agregatów, również należy przekazywać poprawny się, że "kontrolowanie nieznane" do obiektów agregacji. Zazwyczaj ten [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) wskaźnik jest przekazywany do obiektu, gdy tworzony jest agregat. Na przykład parametrem pUnkOuter jest "kontrolowanie nieznane" dla obiektów utworzonych za pomocą `CoCreateInstance`. Poprawny wskaźnik "kontrolowanie nieznane" może być pobierany przez wywołanie `CCmdTarget::GetControllingUnknown`. Wartość zwracana z tej funkcji, jednak nie jest prawidłowy podczas konstruktora. Z tego powodu zaleca się tworzyć swoje agregaty tylko w zastąpieniu obiektu `CCmdTarget::OnCreateAggregates`, gdzie wartość zwracana z `GetControllingUnknown` jest wiarygodna, nawet jeśli utworzone na podstawie `COleObjectFactory` implementacji.

Jest również ważne, aby obiekt manipulował licznikiem odwołań poprawnych przy dodawaniu lub zwalnianiu zliczania odwołań sztucznych. Aby upewnić się, jest to możliwe, zawsze wywołuj `ExternalAddRef` i `ExternalRelease` zamiast `InternalRelease` i `InternalAddRef`. To rzadkość, aby wywołać `InternalRelease` lub `InternalAddRef` dla klasy, która obsługuje agregację.

## <a name="reference-material"></a>Materiały referencyjne

Zaawansowane wykorzystanie OLE, takich jak Definiowanie własnych interfejsów lub zastępowanie ramowych implementacji interfejsów OLE wymaga użycia podstawowego mechanizmu mapowania interfejsu.

W tej sekcji omówiono każde makro i interfejs API, które służy do wdrażania tych zaawansowanych funkcji.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation — Opis funkcji

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w konstruktorze klasy pochodnej, jeśli chcesz obsługiwać agregację OLE dla obiektów tego typu. Wykonanie tych kroków przygotowuje to specjalną implementację IUnknown, która jest wymagana dla obiektów kumulowanych.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface — Opis funkcji

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parametry

*lpIID*<br/>
Daleki wskaźnik IID (pierwszy argument funkcji QueryInterface)

*ppvObj*<br/>
Wskaźnik IUnknown * (drugi argument funkcji QueryInterface)

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w danej implementacji IUnknown dla każdego interfejsu, klasa implementuje. Ta funkcja udostępnia standardowa opartych na danych implementację QueryInterface bazującą na mapie interfejsu użytkownika obiektu. Jest niezbędne rzutowanie zwracanej wartości HRESULT. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływać "Kontrolowanie IUnknown" zamiast używać lokalnej mapy interfejsów.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef — Opis funkcji

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w danej implementacji IUnknown::AddRef dla każdego interfejsu, klasa implementuje. Wartość zwracana jest nowym licznikiem odwołań dla obiektu CCmdTarget. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływać "Kontrolowanie IUnknown" zamiast operować na liczniku odwołań lokalnych.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease — Opis funkcji

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w danej implementacji IUnknown::Release dla każdego interfejsu, klasa implementuje. Zwracana wartość wskazuje nowy licznik odwołań obiektu. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływać "Kontrolowanie IUnknown" zamiast operować na liczniku odwołań lokalnych.

### <a name="declareinterfacemap--macro-description"></a>DECLARE_INTERFACE_MAP — Opis makra

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Uwagi

Użyj tego makra w dowolnej klasie pochodnej `CCmdTarget` będą mieć mapy interfejsu. Używane w taki sam sposób, jak DECLARE_MESSAGE_MAP. To wywołanie makro powinny być umieszczone w definicji klasy, zazwyczaj w nagłówku (. H) pliku. Klasa z DECLARE_INTERFACE_MAP musi zdefiniować mapę interfejsu w pliku implementacji (. CPP) z makrami BEGIN_INTERFACE_MAP i END_INTERFACE_MAP.

### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>BEGIN_INTERFACE_PART i END_INTERFACE_PART — opisy makra

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parametry

*localClass*<br/>
Nazwa klasy, która implementuje interfejs

*iface*<br/>
Nazwa interfejsu, który implementuje ta klasa

#### <a name="remarks"></a>Uwagi

Dla każdego interfejsu, który będzie implementowany przez klasę musisz mieć parę BEGIN_INTERFACE_PART i END_INTERFACE_PART. Te makra definiują lokalną klasę pochodzącą od interfejsu OLE, który zdefiniujesz, jak również osadzoną zmienną elementu członkowskiego tej klasy. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), i [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) elementy członkowskie są zgłaszane automatycznie. Musisz dołączyć deklaracje dla innych funkcji Członkowskich, będących częścią implementowanego interfejsu (deklaracje te są umieszczane między makra BEGIN_INTERFACE_PART i END_INTERFACE_PART).

*Iface* argument jest interfejsem OLE, który chcesz wdrożyć, takim jak `IAdviseSink`, lub `IPersistStorage` (lub innym niestandardowym interfejsem).

*LocalClass* argument jest nazwą klasy lokalnej, która zostanie zdefiniowana. "X" zostanie automatycznie być dołączona do nazwy. Tę konwencję nazewnictwa jest używany w celu uniknięcia kolizji z klasami globalnymi o tej samej nazwie. Ponadto Nazwa osadzonego elementu członkowskiego, taka sama jak *localClass* nazwy z wyjątkiem, że jest poprzedzona przez wyrażenie "m_x".

Na przykład:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

zdefiniuje klasę lokalną o nazwie XMyAdviseSink pochodzącą od IAdviseSink, oraz członka klasy, w której jest zadeklarowana o nazwie m_xMyAdviseSink.Note:

> [!NOTE]
> Wiersze rozpoczynające się od `STDMETHOD`_ są zasadniczo kopiowane z OLE2. Godz. i nieco modyfikowane. Kopiując je z OLE2. H zmniejszyć liczbę błędów, które są trudne do rozwiązania.

### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>BEGIN_INTERFACE_MAP i END_INTERFACE_MAP — opisy makra

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasy, w którym ma zostać określona mapy interfejsu

*baseClass*<br/>
Klasa, z której *theClass* pochodzi od klasy.

#### <a name="remarks"></a>Uwagi

BEGIN_INTERFACE_MAP i END_INTERFACE_MAP makra są używane w pliku implementacji do definiowania mapy interfejsu. Dla każdego interfejsu, który jest implementowany ma jeden lub więcej wywołań makra INTERFACE_PART. Dla każdej agregacji, z której korzysta ta klasa jest jedno wywołanie makra INTERFACE_AGGREGATE.

### <a name="interfacepart--macro-description"></a>INTERFACE_PART — Opis makra

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu.

*IID*<br/>
`IID` Który ma być mapowane na klasie osadzonej.

*localClass*<br/>
Nazwa klasy lokalnej (mniej "X").

#### <a name="remarks"></a>Uwagi

To makro jest używane między makro BEGIN_INTERFACE_MAP i END_INTERFACE_MAP — makro dla każdego interfejsu, który jaki obsługiwał będzie obiekt. Umożliwia mapowania identyfikatora IID do elementu członkowskiego klasy wskazanego przez *theClass* i *localClass*. 'm_x' zostanie dodany do *localClass* automatycznie. Należy pamiętać, że więcej niż jeden `IID` może być skojarzony z jednym elementem członkowskim. Jest to bardzo przydatne, gdy wdrażają "tylko najbardziej pochodnego" interfejsu i chcesz zapewnić wszystkie interfejsy pośrednie. Dobrym przykładem jest `IOleInPlaceFrameWindow` interfejsu. Jego hierarchia wygląda następująco:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Jeśli obiekt implementuje interfejs `IOleInPlaceFrameWindow`, klient może `QueryInterface` na każdym z tych interfejsów: `IOleUIWindow`, `IOleWindow`, lub [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), poza "najbardziej pochodnym" interfejsem `IOleInPlaceFrameWindow` (znajdujący się w rzeczywistości Implementowanie). Aby to obsłużyć umożliwia więcej niż jeden INTERFACE_PART — makro mapować każdy interfejs podstawowy do `IOleInPlaceFrameWindow` interfejsu:

w pliku definicji klasy:

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

w pliku implementacji klasy:

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

Szablon dba o IUnknown, ponieważ jest zawsze wymagana.

### <a name="interfacepart--macro-description"></a>INTERFACE_PART — Opis makra

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu

*theAggr*<br/>
Nazwa zmiennej członkowskiej, która ma zostać zagregowana.

#### <a name="remarks"></a>Uwagi

To makro jest używane, aby poinformować szablon, że klasa korzysta z obiektu agregacji. Musi się znajdować między BEGIN_INTERFACE_PART i END_INTERFACE_PART makra. Obiekt agregacji jest oddzielnym obiektem, pochodzącym z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Za pomocą agregacji i makra INTERFACE_AGGREGATE, możesz wprowadzać wszystkie interfejsy, które obsługuje agregacja, wyglądały na bezpośrednio obsługiwane przez obiekt. *TheAggr* argument jest po prostu nazwą zmiennej członka klasy wywodzącej się od [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) (bezpośrednio lub pośrednio). Wszystkie makra INTERFACE_AGGREGATE należy wykonać makra INTERFACE_PART umieszczone na mapie interfejsu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
