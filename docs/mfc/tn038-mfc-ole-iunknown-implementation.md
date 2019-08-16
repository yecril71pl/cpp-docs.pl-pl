---
title: 'TN038: Implementacja MFC-OLE IUnknown'
ms.date: 06/28/2018
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
ms.openlocfilehash: fb5ddf7fbbf2b59a8e0434e4b097284e309c918d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511051"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: Implementacja MFC/OLE IUnknown

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

W przypadku interfejsu OLE 2 jest to "OLE Component Object Model" lub COM. COM definiuje standard, w jaki obiekty współpracujące komunikują się ze sobą. Obejmuje to szczegółowe informacje o tym, jak wygląda "obiekt", w tym sposób wysyłania metod do obiektu. Model COM definiuje również klasę bazową, z której są wyprowadzane wszystkie klasy zgodne z modelem COM. Tą klasą bazową jest [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Chociaż Interfejs [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest nazywany C++ klasą, com nie jest specyficzny dla żadnego z języków — może być zaimplementowany w języku C, Pascal lub innym, który może obsługiwać układ binarny obiektu com.

Mechanizm OLE odwołuje się do wszystkich klas pochodnych klasy [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jako "interfejsy". Jest to ważna różnica, ponieważ "interfejs", taki jak [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , nie ma żadnej implementacji. Po prostu definiuje protokół, za pomocą którego obiekty komunikują się, a nie z konkretnymi implementacjami tych implementacji. Jest to rozsądne dla systemu umożliwiającego maksymalną elastyczność. Jest to zadanie MFC do implementowania domyślnego zachowania dla MFC/C++ programów.

Aby zrozumieć implementację interfejsu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) MFC, należy najpierw zrozumieć, czym jest ten interfejs. Poniżej określono uproszczoną wersję elementu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) :

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
> Niektóre niezbędne szczegóły konwencji wywoływania, takie jak `__stdcall` są pozostawione dla tej ilustracji.

Funkcja elementów członkowskich [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) kontroluje zarządzanie pamięcią obiektu. COM używa schematu zliczania odwołań do śledzenia obiektów. Obiekt nigdy nie jest przywoływany bezpośrednio, jak C++w. Zamiast tego obiekty COM zawsze są przywoływane przez wskaźnik. Aby zwolnić obiekt, gdy jest on używany przez właściciela, zostanie wywołany element członkowski [wydania](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) obiektu (w przeciwieństwie do użycia operatora delete, tak jak w przypadku tradycyjnego C++ obiektu). Mechanizm zliczania odwołań umożliwia zarządzanie wieloma odwołaniami do pojedynczego obiektu, który ma być zarządzany. Implementacja [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) utrzymuje liczbę odwołań dla obiektu — obiekt nie zostanie usunięty, dopóki jego licznik odwołań osiągnie wartość zero.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) są dość proste w przypadku wdrożenia punktu widzenia. Oto prosta implementacja:

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

Funkcja członkowska [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) jest nieco bardziej interesująca. Nie jest bardzo interesujący, aby mieć obiekt, którego jedyne funkcje składowe są [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [wersja](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) — warto poinformować obiekt, aby wykonał więcej elementów niż zapewnia wartość [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Jest to miejsce, w którym funkcja [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) jest przydatna. Umożliwia uzyskanie innego "interfejsu" w tym samym obiekcie. Te interfejsy są zwykle wyprowadzane z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) i dodają dodatkowe funkcje, dodając nowe funkcje członkowskie. Interfejsy COM nigdy nie mają zmiennych składowych zadeklarowanych w interfejsie, a wszystkie funkcje składowe są deklarowane jako czyste-wirtualne. Na przykład

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Aby uzyskać IPrintInterface, jeśli masz tylko element [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), wywołaj polecenie [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) przy `IID` użyciu elementu `IPrintInterface`. `IID` Jest to numer 128-bitowy, który jednoznacznie identyfikuje interfejs. `IID` Dla każdego interfejsu, który został zdefiniowany przez użytkownika lub OLE. Jeśli *punkt* jest wskaźnikiem do obiektu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , kod umożliwiający pobranie IPrintInterface z niego może być:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Jest to dość proste, ale jak zaimplementować obiekt obsługujący interfejs IPrintInterface i [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) w tym przypadku jest to proste, ponieważ IPrintInterface jest wyprowadzany bezpośrednio z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) — przez implementację IPrintInterface, [Interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest automatycznie obsługiwany. Przykład:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Implementacje [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) będą dokładnie takie same, jak te zaimplementowane powyżej. `CPrintObj::QueryInterface`będzie wyglądać następująco:

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

Jak widać, jeśli identyfikator interfejsu (IID) jest rozpoznawany, wskaźnik jest zwracany do obiektu; w przeciwnym razie wystąpi błąd. Zwróć również uwagę, że pomyślne wyniki [polecenia QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) to implikowane [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Oczywiście trzeba również zaimplementować CEditObj::P rukuj. Jest to proste, ponieważ IPrintInterface został bezpośrednio uzyskany z interfejsu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Jeśli jednak chcesz obsługiwać dwa różne interfejsy, oba pochodne od [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), weź pod uwagę następujące kwestie:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

Chociaż istnieją różne sposoby implementacji klasy obsługującej zarówno IEditInterface, jak i IPrintInterface, w tym przy użyciu C++ wielokrotnego dziedziczenia, ta Uwaga koncentruje się na używaniu klas zagnieżdżonych do zaimplementowania tej funkcji.

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

Poniżej znajduje się cała implementacja:

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

Należy zauważyć, że większość implementacji [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest umieszczana w klasie CEditPrintObj zamiast duplikowania kodu w CEditPrintObj:: CEditObj i CEditPrintObj:: CPrintObj. Zmniejsza to ilość kodu i pozwala uniknąć błędów. Kluczowym punktem jest to, że z interfejsu IUnknown możliwe jest wywołanie [polecenia QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) w celu pobrania dowolnego interfejsu, który obiekt może obsługiwać, i z każdego z tych interfejsów możliwe jest takie samo. Oznacza to, że wszystkie funkcje [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) dostępne w każdym interfejsie muszą zachowywać się dokładnie tak samo. Aby te obiekty osadzone wywołują implementację w obiekcie zewnętrznym, używany jest wskaźnik wsteczny (m_pParent). Wskaźnik m_pParent jest inicjowany podczas konstruktora CEditPrintObj. Następnie należy zaimplementować CEditPrintObj:: CPrintObj::P rintObject i CEditPrintObj:: CEditObj:: EditObject. Zbyt wiele kodu dodano do dodawania jednej funkcji — możliwość edytowania obiektu. Na szczęście zdarza się, że interfejsy mają tylko jedną funkcję członkowską (chociaż zdarza się), a w tym przypadku, funkcja EditObject i PrintObject zwykle jest łączona do jednego interfejsu.

To wiele wyjaśnień i wiele kodów dla takiego prostego scenariusza. Klasy MFC/OLE zapewniają uproszczoną alternatywę. Implementacja MFC używa techniki podobnej do sposobu zawijania komunikatów systemu Windows przy użyciu map komunikatów. Ta funkcja jest nazywana *mapami interfejsów* i została omówiona w następnej sekcji.

## <a name="mfc-interface-maps"></a>Mapy interfejsu MFC

MFC/OLE zawiera implementację "map interfejsu" podobną do "mapy komunikatów" i "mapy wysyłania" w koncepcji i wykonywaniu. Podstawowe funkcje map interfejsów MFC są następujące:

- Standardowa implementacja elementu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), wbudowana w `CCmdTarget` klasę.

- Obsługa liczby odwołań zmodyfikowanych przez [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [wydanie](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)

- Implementacja funkcji [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) oparta na danych

Ponadto mapy interfejsów obsługują następujące funkcje zaawansowane:

- Obsługa tworzenia agregowanych obiektów COM

- Obsługa używania obiektów agregujących w implementacji obiektu COM

- Implementacja jest podłączana i rozszerzalna

Aby uzyskać więcej informacji na temat agregacji [](/windows/win32/com/aggregation) , zobacz temat agregacja.

Obsługa mapy interfejsu MFC jest umieszczana w `CCmdTarget` klasie. `CCmdTarget`liczba odwołań "*ma-a*", a także wszystkie funkcje składowe skojarzone z implementacją [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (licznik odwołań na przykład jest w `CCmdTarget`). Aby utworzyć klasę, która obsługuje OLE com, Klasa `CCmdTarget` jest pochodną i używa różnych makr, a także funkcji składowych programu `CCmdTarget` w celu zaimplementowania odpowiednich interfejsów. Implementacja MFC używa zagnieżdżonych klas do definiowania każdej implementacji interfejsu podobnie jak powyżej. Jest to łatwiejsze dzięki standardowej implementacji IUnknown, a także kilku makr, które eliminują niektóre powtarzające się kod.

## <a name="interface-map-basics"></a>Mapa interfejsu — podstawy

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Aby zaimplementować klasę przy użyciu map interfejsu MFC

1. Wyprowadzanie klasy bezpośrednio lub pośrednio z `CCmdTarget`.

2. `DECLARE_INTERFACE_MAP` Użyj funkcji w definicji klasy pochodnej.

3. Dla każdego interfejsu, który ma być obsługiwany, użyj makr BEGIN_INTERFACE_PART i END_INTERFACE_PART w definicji klasy.

4. W pliku implementacji Użyj makr BEGIN_INTERFACE_MAP i END_INTERFACE_MAP, aby zdefiniować mapę interfejsu klasy.

5. Dla każdego obsługiwanego identyfikatora IID Użyj makra INTERFACE_PART między makrami BEGIN_INTERFACE_MAP i END_INTERFACE_MAP, aby zmapować ten identyfikator IID do określonej części "część" klasy.

6. Zaimplementuj każdą z klas zagnieżdżonych, które reprezentują obsługiwane interfejsy.

7. Użyj makra METHOD_PROLOGUE, aby uzyskać dostęp do obiektu `CCmdTarget`nadrzędnego,-pochodnego.

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) mogą `CCmdTarget` delegować do implementacji tych funkcji (`ExternalAddRef`, `ExternalRelease`i `ExternalQueryInterface`).

Przykład CPrintEditObj można zaimplementować w następujący sposób:

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

Powyższa deklaracja tworzy klasę pochodną `CCmdTarget`. Makro DECLARE_INTERFACE_MAP informuje platformę, że ta klasa będzie miała niestandardową mapę interfejsu. Ponadto makra BEGIN_INTERFACE_PART i END_INTERFACE_PART definiują klasy zagnieżdżone, w tym przypadku z nazwami CEditObj i CPrintObj (X jest używany tylko do odróżniania klas zagnieżdżonych od klas globalnych, które zaczynają się od "C" i klas interfejsów, które Zacznij od "I"). Tworzone są dwa zagnieżdżone elementy członkowskie tych klas: odpowiednio m_CEditObj i m_CPrintObj. Makra automatycznie deklarują funkcje [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) ; w związku z tym tylko deklaruje funkcje specyficzne dla tego interfejsu: EditObject i PrintObject (STDMETHOD makro OLE jest używany, aby **_stdcall** i wirtualne słowa kluczowe były odpowiednie dla platformy docelowej).

Aby zaimplementować mapę interfejsu dla tej klasy:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

Spowoduje to połączenie identyfikatora IID IID_IPrintInterface z m_CPrintObj i IID_IEditInterface z m_CEditObj. Implementacja polecenia`CCmdTarget::ExternalQueryInterface`QueryInterface () używa tej mapy do zwracania wskaźników do m_CPrintObj i m_CEditObj na żądanie. [](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) `CCmdTarget` Nie trzeba dołączać wpisu dla `IID_IUnknown`; platforma będzie używać pierwszego interfejsu w mapie (w tym przypadku m_CPrintObj), gdy `IID_IUnknown` jest to wymagane.

Mimo że makro BEGIN_INTERFACE_PART automatycznie deklaruje funkcje [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) , nadal trzeba je zaimplementować:

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

Implementacja elementu CEditPrintObj:: CPrintObj jest podobna do powyższych definicji dla CEditPrintObj:: CEditObj. Mimo że można utworzyć makro, którego można użyć do automatycznego generowania tych funkcji (ale wcześniej w przypadku programowania MFC/OLE jest to przypadek), gdy makro generuje więcej niż jeden wiersz kodu, trudno ustawić punkty przerwania. Z tego powodu ten kod jest rozwinięty ręcznie.

Korzystając z implementacji struktury map komunikatów, istnieje kilka rzeczy, które nie są konieczne do wykonania:

- Zaimplementuj interfejs QueryInterface

- Zaimplementuj AddRef i zwolnij

- Zadeklaruj jedną z tych wbudowanych metod na obu interfejsach

Ponadto struktura używa wewnętrznie map komunikatów. Dzięki temu można wyprowadzić z klasy Framework, powiedzmy `COleServerDoc`, która już obsługuje pewne interfejsy i udostępnia zamienniki lub dodatki do interfejsów dostarczonych przez platformę. Można to zrobić, ponieważ struktura w pełni obsługuje dziedziczenie mapy interfejsu z klasy bazowej. Jest to powód, dla którego BEGIN_INTERFACE_MAP przyjmuje jako drugi parametr nazwę klasy bazowej.

> [!NOTE]
> Zwykle nie jest możliwe ponowne użycie implementacji wbudowanych implementacji MFC interfejsów OLE tylko przez dziedziczenie osadzonej specjalizacji tego interfejsu z wersji MFC. Nie jest to możliwe, ponieważ użycie makra METHOD_PROLOGUE w celu uzyskania dostępu do obiektu zawierającego `CCmdTarget`pochodne oznacza *stałe przesunięcie* `CCmdTarget`osadzonego obiektu z obiektu pochodnego. Oznacza to, na przykład, nie można utworzyć osadzonej XMyAdviseSink z implementacji MFC w `COleClientItem::XAdviseSink`, ponieważ XAdviseSink opiera się na określonym przesunięciu od góry `COleClientItem` obiektu.

> [!NOTE]
> Można jednak delegować do implementacji MFC dla wszystkich funkcji, które mają być zachowaniem domyślnym MFC. Jest to realizowane w implementacji `IOleInPlaceFrame` MFC systemu (XOleInPlaceFrame) `COleFrameHook` w klasie (deleguje do m_xOleInPlaceUIWindow dla wielu funkcji). Ten projekt został wybrany w celu zmniejszenia rozmiaru środowiska uruchomieniowego obiektów, które implementują wiele interfejsów; Eliminuje to konieczność użycia wskaźnika zaplecza (takiego jak m_pParent w poprzedniej sekcji).

### <a name="aggregation-and-interface-maps"></a>Agregacja i mapy interfejsu

Oprócz obsługi autonomicznych obiektów COM, MFC obsługuje również agregację. Samo agregowanie jest zbyt złożone, aby można było omówić ten temat. Aby uzyskać więcej [](/windows/win32/com/aggregation) informacji na temat agregacji, zapoznaj się z tematem agregacji. Ta Uwaga po prostu zawiera opis obsługi agregacji wbudowanej w struktury i mapy interfejsu.

Istnieją dwa sposoby użycia agregacji: (1) użycie obiektu COM, który obsługuje agregację, oraz (2) implementowanie obiektu, który może być agregowany przez inny. Te możliwości mogą być określane jako "przy użyciu obiektu zagregowanego" i "do agregowania obiektu". MFC obsługuje oba te elementy.

### <a name="using-an-aggregate-object"></a>Używanie obiektu agregacji

Aby użyć obiektu agregacji, musi istnieć jakiś sposób powiązania agregacji z mechanizmem QueryInterface. Innymi słowy, obiekt zagregowany musi zachowywać się tak, jakby jest natywną częścią obiektu. Tak więc jak jest to zgodne z mechanizmem mapy interfejsu MFC oprócz makra INTERFACE_PART, gdzie zagnieżdżony obiekt jest mapowany na identyfikator IID, można także zadeklarować obiekt zagregowany jako część `CCmdTarget` klasy pochodnej. W tym celu używane jest makro INTERFACE_AGGREGATE. Pozwala to określić zmienną członkowską (która musi być wskaźnikiem do klasy [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) lub klasą pochodną), która ma zostać zintegrowana z mechanizmem mapy interfejsu. Jeśli wskaźnik nie ma wartości null, `CCmdTarget::ExternalQueryInterface` gdy jest wywoływana, platforma automatycznie wywoła `IID` funkcję członkowską [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) obiektu agregacji, jeśli żądana nie jest jednym z natywnych `IID`, obsługiwanych przez `CCmdTarget`sam obiekt.

#### <a name="to-use-the-interface_aggregate-macro"></a>Aby użyć makra INTERFACE_AGGREGATE

1. Zadeklaruj zmienną członkowską ( `IUnknown*`), która będzie zawierać wskaźnik do obiektu zagregowanego.

2. Dołącz makro INTERFACE_AGGREGATE do mapy interfejsu, która odwołuje się do zmiennej składowej według nazwy.

3. W pewnym momencie (zwykle w `CCmdTarget::OnCreateAggregates`trakcie) zainicjuj zmienną członkowską inną niż null.

Przykład:

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

Zmienna m_lpAggrInner jest inicjowana w konstruktorze do wartości NULL. Struktura ignoruje zmienną członkowską NULL w domyślnej implementacji [polecenia QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). `OnCreateAggregates`jest dobrym miejscem do rzeczywistego tworzenia obiektów agregujących. Musisz jawnie wywołać ten element, jeśli tworzysz obiekt poza implementacją `COleObjectFactory`MFC. Powód tworzenia agregatów w `CCmdTarget::OnCreateAggregates` , jak również `CCmdTarget::GetControllingUnknown` użycie, będzie widoczny podczas tworzenia agregowanych obiektów.

Ta technika daje obiektowi wszystkie interfejsy, które obsługuje obiekt zagregowany oraz interfejsy natywne. Jeśli potrzebujesz tylko podzestawu interfejsów, które obsługuje agregacja, można przesłonić `CCmdTarget::GetInterfaceHook`. Pozwala to na bardzo niskie poziomu zaczepienia, podobnie jak w przypadku [polecenia QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). Zwykle wszystkie interfejsy obsługiwane przez funkcję zagregowaną.

### <a name="making-an-object-implementation-aggregatable"></a>Wprowadzanie agregowania implementacji obiektu

Aby obiekt mógł być agregowany, implementacja [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) musi delegować do "kontrolowanie nieznane". Innymi słowy, aby było częścią obiektu, musi on delegować [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) do innego obiektu, również pochodzący od [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). "Kontrolowanie nieznane" jest dostarczane do obiektu podczas jego tworzenia, czyli jest ono udostępniane implementacji `COleObjectFactory`. Wdrożenie tej składa się z niewielkiej ilości obciążenia, a w niektórych przypadkach nie jest to pożądane, dlatego MFC umożliwia to opcjonalne. Aby umożliwić agregowanie obiektu, należy wywołać `CCmdTarget::EnableAggregation` z konstruktora obiektu.

Jeśli obiekt używa również agregacji, należy również przekazać poprawne "kontrolowanie nieznane" do obiektów agregujących. Zazwyczaj ten wskaźnik [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jest przenoszona do obiektu podczas tworzenia agregacji. Na przykład parametr pUnkOuter jest "kontrolowanie nieznane" dla obiektów utworzonych za pomocą `CoCreateInstance`. Poprawny wskaźnik "kontrolowanie nieznane" może być pobierany `CCmdTarget::GetControllingUnknown`przez wywołanie. Wartość zwrócona przez tę funkcję, ale nie jest prawidłowa w konstruktorze. Z tego powodu sugerowane jest utworzenie wartości zagregowanych tylko w przesłonięciu `CCmdTarget::OnCreateAggregates`, w którym wartość zwracana z `GetControllingUnknown` jest niezawodna, `COleObjectFactory` nawet jeśli została utworzona na podstawie implementacji.

Należy również pamiętać, że obiekt manipuluje poprawną liczbę odwołań przy dodawaniu lub zwalnianiu sztucznych liczb referencyjnych. Aby upewnić się, że jest to przypadek `ExternalAddRef` , `ExternalRelease` zawsze Wywołaj `InternalAddRef`i zamiast `InternalRelease` i. Jest rzadkim wywołaniem `InternalRelease` lub `InternalAddRef` na klasie, która obsługuje agregację.

## <a name="reference-material"></a>Materiały referencyjne

Zaawansowane użycie OLE, takie jak Definiowanie własnych interfejsów lub zastępowanie implementacji struktury interfejsów OLE wymaga użycia mechanizmu mapy interfejsu.

W tej sekcji omówiono każde makro i interfejsy API, które są używane do implementowania tych zaawansowanych funkcji.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget:: EnableAggregation — opis funkcji

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w konstruktorze klasy pochodnej, jeśli chcesz obsługiwać agregację OLE dla obiektów tego typu. Przygotowuje to specjalną implementację IUnknown, która jest wymagana dla obiektów agregowanych.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget:: ExternalQueryInterface — opis funkcji

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parametry

*lpIID*<br/>
Daleko wskaźnik do IID (pierwszy argument polecenia QueryInterface)

*ppvObj*<br/>
Wskaźnik do elementu IUnknown * (drugi argument do polecenia QueryInterface)

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w implementacji elementu IUnknown dla każdego interfejsu, który implementuje Klasa. Ta funkcja zapewnia standardową implementację metody QueryInterface opartą na danych w oparciu o mapę interfejsu obiektu. Konieczne jest Rzutowanie wartości zwracanej na wartość HRESULT. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływała "kontrolowanie IUnknown" zamiast używać mapy interfejsu lokalnego.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget:: ExternalAddRef — opis funkcji

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w implementacji elementu IUnknown:: AddRef dla każdego interfejsu, który implementuje Klasa. Wartość zwracana jest nową liczbą odwołań dla obiektu CCmdTarget. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływała "kontrolowanie IUnknown" zamiast manipulowania lokalnymi liczbą odwołań.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget:: ExternalRelease — opis funkcji

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję w implementacji elementu IUnknown:: Release dla każdego interfejsu, który implementuje Klasa. Wartość zwracana wskazuje na nową liczbę odwołań dla obiektu. Jeśli obiekt jest zagregowany, funkcja ta będzie wywoływała "kontrolowanie IUnknown" zamiast manipulowania lokalnymi liczbą odwołań.

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP — opis makra

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Uwagi

Użyj tego makra w dowolnej klasie pochodnej `CCmdTarget` , która będzie miała mapę interfejsu. Używane w podobny sposób jak DECLARE_MESSAGE_MAP. To wywołanie makra należy umieścić w definicji klasy, zwykle w nagłówku (. H). Klasa z DECLARE_INTERFACE_MAP musi definiować mapę interfejsu w pliku implementacji (. CPP) za pomocą makr BEGIN_INTERFACE_MAP i END_INTERFACE_MAP.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART i END_INTERFACE_PART — opisy makr

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parametry

*localClass*<br/>
Nazwa klasy implementującej interfejs

*iface*<br/>
Nazwa interfejsu, który implementuje Ta klasa

#### <a name="remarks"></a>Uwagi

Dla każdego interfejsu, który implementuje klasa, należy mieć parę BEGIN_INTERFACE_PART i END_INTERFACE_PART. Te makra definiują lokalną klasę pochodzącą od interfejsu OLE, który definiujesz, oraz osadzoną zmienną członkowską tej klasy. Elementy członkowskie [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)i [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) są deklarowane automatycznie. Należy uwzględnić deklaracje dla innych funkcji Członkowskich, które są częścią implementowanego interfejsu (te deklaracje są umieszczane między makrami BEGIN_INTERFACE_PART i END_INTERFACE_PART).

Argument *iface* jest interfejsem OLE, który ma zostać wdrożony, taki jak `IAdviseSink`lub `IPersistStorage` (lub własny niestandardowy interfejs).

Argument *localClass* jest nazwą klasy lokalnej, która zostanie zdefiniowana. Symbol "X" zostanie automatycznie dołączony do nazwy. Ta konwencja nazewnictwa jest używana w celu uniknięcia kolizji z klasami globalnymi o tej samej nazwie. Ponadto nazwa osadzonego elementu członkowskiego, taka sama jak nazwa *localClass* , z wyjątkiem prefiksu _X '.

Przykład:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

Zdefiniuj klasę lokalną o nazwie XMyAdviseSink pochodnej od IAdviseSink i składową klasy, w której jest zadeklarowana o nazwie m_xMyAdviseSink. Uwaga:

> [!NOTE]
> Wiersze zaczynające `STDMETHOD`się od _ są zasadniczo kopiowane z OLE2. H i nieznacznie modyfikowane. Kopiowanie ich z OLE2. H może zmniejszyć liczbę błędów, które trudno rozwiązać.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP i END_INTERFACE_MAP — opisy makr

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, w której ma zostać zdefiniowana Mapa interfejsu

*baseClass*<br/>
Klasa, z której pochodzi *theClass* .

#### <a name="remarks"></a>Uwagi

Makra BEGIN_INTERFACE_MAP i END_INTERFACE_MAP są używane w pliku implementacji do rzeczywistego definiowania mapy interfejsu. Dla każdego interfejsu, który jest zaimplementowany, istnieje co najmniej jedno wywołanie makra INTERFACE_PART. Dla każdej wartości zagregowanej używanej przez klasę istnieje jedno wywołanie makra INTERFACE_AGGREGATE.

### <a name="interface_part--macro-description"></a>INTERFACE_PART — opis makra

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu.

*IID*<br/>
`IID` , Która ma być zmapowana na osadzoną klasę.

*localClass*<br/>
Nazwa klasy lokalnej (mniej "X").

#### <a name="remarks"></a>Uwagi

To makro jest używane między makrem BEGIN_INTERFACE_MAP a makrem END_INTERFACE_MAP dla każdego interfejsu, który będzie obsługiwany przez obiekt. Umożliwia mapowanie identyfikatora IID do elementu członkowskiego klasy wskazywanej przez *theClass* i *localClass*. Element "_X" zostanie automatycznie dodany do *localClass* . Należy zauważyć, że więcej `IID` niż jedna może być skojarzona z pojedynczym członkiem. Jest to bardzo przydatne, gdy wdrażasz tylko interfejs "najbardziej pochodne" i chcesz również udostępnić wszystkie interfejsy pośrednie. Dobrym przykładem jest `IOleInPlaceFrameWindow` interfejs. Jego hierarchia wygląda następująco:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

`IOleInPlaceFrameWindow`W przypadku zaimplementowania obiektu klient może `QueryInterface` na dowolnym z następujących interfejsów: `IOleUIWindow`, `IOleWindow`, lub [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), oprócz interfejsu `IOleInPlaceFrameWindow` "najbardziej pochodnego" (ten, który jest faktycznie implementowany). Aby obsłużyć tę procedurę, można użyć więcej niż jednego makra INTERFACE_PART, aby zmapować każdy interfejs podstawowy `IOleInPlaceFrameWindow` do interfejsu:

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

Struktura zajmuje IUnknown, ponieważ jest zawsze wymagana.

### <a name="interface_part--macro-description"></a>INTERFACE_PART — opis makra

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu,

*theAggr*<br/>
Nazwa zmiennej członkowskiej, która ma zostać zagregowana.

#### <a name="remarks"></a>Uwagi

To makro służy do informowania struktury, że Klasa używa obiektu agregacji. Musi występować między makrami BEGIN_INTERFACE_PART i END_INTERFACE_PART. Obiekt zagregowany jest oddzielnym obiektem pochodnym elementu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Za pomocą wartości zagregowanej i makra INTERFACE_AGGREGATE, można sprawić, że wszystkie interfejsy, które obsługuje agregacji, są wyświetlane, aby były bezpośrednio obsługiwane przez obiekt. Argument *theAggr* jest po prostu nazwą zmiennej składowej klasy, która pochodzi od [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (bezpośrednio lub pośrednio). Wszystkie makra INTERFACE_AGGREGATE muszą być zgodne z makrami INTERFACE_PART umieszczonymi w mapie interfejsu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
