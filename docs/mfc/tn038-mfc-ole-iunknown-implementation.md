---
title: 'TN038: Implementacja interfejsu IUnknown MFC OLE | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.ole
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a17ce210dffd13e0ffdac142c6121954eec1045d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: implementacja interfejsu MFC/OLE IUnknown
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Istotą OLE 2 jest "OLE Component Object Model" lub modelu COM. Standard definiuje COM dla obiektów, jak współpracujących komunikować się ze sobą. Obejmuje to szczegóły jakie "obiektu" wygląda, w tym jak metody są wysyłane do obiektu. COM również definiuje klasę podstawową, od których pochodzą wszystkie zgodne klasy COM. Ta klasa podstawowa jest [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Mimo że [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfejsu jest określana jako klasę C++, COM nie jest specyficzne dla żadnego języka jeden — można ją wdrożyć w C, PASCAL lub dowolnego innego języka może obsługiwać binarne układ obiektu COM.  
  
 OLE odwołuje się do wszystkich klas pochodnych [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jako "Interfejsy". Jest to ważna różnica od "interfejsu" takie jak [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) niesie ze sobą żadnej implementacji. Definiuje on po prostu protokołu za pomocą którego komunikację obiektów, nie szczegółowe informacje na temat tych wdrożeń czy. Jest to uzasadnione dla systemu, który pozwala na maksymalne elastyczność. To zadanie MFC do zaimplementowania domyślne zachowanie dla programów MFC/C++.  
  
 Aby zrozumieć implementacji MFC [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) należy najpierw zrozumieć ten interfejs jest. Uproszczone [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jest zdefiniowana poniżej:  
  
```  
class IUnknown  
{  
public:  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;  
    virtual ULONG AddRef() = 0;  
    virtual ULONG Release() = 0;  
};  
```  
  
> [!NOTE]
>  Niektórych niezbędne Konwencja wywoływania szczegółowe informacje, takie jak `__stdcall` pozostało na tej ilustracji.  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) funkcje Członkowskie kontroli zarządzania pamięcią obiektu. COM wykorzystuje schemat zliczania odwołania do śledzenia obiektów. Nigdy nie odwołuje się do obiektu bezpośrednio, tak jak w języku C++. Zamiast tego obiekty COM zawsze odwołuje się za pomocą wskaźnika. Do zwolnienia obiektu po zakończeniu właściciela przy użyciu jego, obiekt [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) nosi nazwę elementu członkowskiego (a nie za pomocą operatora delete, jak będą wykonywane dla obiekt tradycyjnego języka C++). Zliczanie mechanizm umożliwia wiele odwołań do pojedynczego obiektu mają być zarządzane. Implementacja interfejsu [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) przechowuje licznika odwołań w obiekcie — obiekt nie zostanie usunięty, dopóki nie osiągnie jego liczebności referencyjnej zero.  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) są bardzo prosta z punktu widzenia implementacji. W tym miejscu jest prosta implementacja:  
  
```  
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
  
 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkcja członkowska jest nieco bardziej interesującego. Nie jest to bardzo interesujące obiekt których tylko funkcje Członkowskie są [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) — powinna być uwzględniona Poinformuj obiekt, aby wykonać więcej czynności niż [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) udostępnia. Jest to, gdy [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) jest użyteczne. Umożliwia uzyskanie innego "interfejsu" na tym samym obiekcie. Te interfejsy są zazwyczaj uzyskiwane z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) i dodać dodatkowe funkcje, dodając nowe funkcje elementów członkowskich. Interfejsy modelu COM nigdy nie ma zmiennych Członkowskich zadeklarowany w interfejsie, a wszystkie funkcje elementów członkowskich są deklarowane jako czysty wirtualnego. Na przykład  
  
```  
class IPrintInterface : public IUnknown  
{  
public:  
    virtual void PrintObject() = 0;  
};  
```  
  
 Aby uzyskać IPrintInterface, jeśli masz tylko [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), wywołaj [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) przy użyciu `IID` z **IPrintInterface**. `IID` Jest liczbą 128-bitowego, który unikatowo identyfikuje interfejsu. Brak `IID` dla danego interfejsu można lub OLE zdefiniować. Jeśli `pUnk` jest wskaźnikiem do [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) obiekt, może być kod, aby pobrać IPrintInterface:  
  
```  
IPrintInterface* pPrint = NULL;  
if (pUnk->QueryInterface(IID_IPrintInterface,   
 (void**)&pPrint) == NOERROR)  
{  
    pPrint->PrintObject();
pPrint->Release();
*// release pointer obtained via QueryInterface  
}  
```  
  
 Wydaje się dość proste, ale jak będzie można zaimplementować obiekt, który obsługuje zarówno IPrintInterface i [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfejsu w tym przypadku jest proste, ponieważ IPrintInterface pochodzi bezpośrednio z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) — wdrażając IPrintInterface, [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jest obsługiwana automatycznie. Na przykład:  
  
```  
class CPrintObj : public CPrintInterface  
{  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();
virtual void PrintObject();

};  
```  
  
 Implementacje [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) czy być dokładnie takie same jak te zaimplementowanym powyżej. **CPrintObj::QueryInterface** będzie wyglądać mniej więcej tak:  
  
```  
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
  
 Jak widać, jeśli rozpoznano identyfikatora interfejsu (IID), wskaźnika jest zwracany do obiektu; w przeciwnym razie wystąpi błąd. Należy również zauważyć, że pomyślnie [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) powoduje domniemanym [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379). Oczywiście można również musi implementować CEditObj::Print. Jest proste, ponieważ IPrintInterface bezpośrednio został utworzony na podstawie [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfejsu. Jednak jeśli chcesz obsługiwać dwa interfejsy różnych zarówno pochodną [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), Uwzględnij następujące kwestie:  
  
```  
class IEditInterface : public IUnkown  
{  
public:  
    virtual void EditObject() = 0;  
};  
```  
  
 Mimo że istnieje wiele różnych sposobów, aby zaimplementować klasę obsługi zarówno IEditInterface i IPrintInterface, w tym języku C++ dziedziczenie wielokrotne ta uwaga będzie skoncentrować się na korzystanie z klasy zagnieżdżone, aby zaimplementować tę funkcję.  
  
```  
class CEditPrintObj  
{  
public:  
    CEditPrintObj();

 
    HRESULT QueryInterface(REFIID iid,
    void**);

    ULONG AddRef();
ULONG Release();
DWORD m_dwRef;  
 
    class CPrintObj : public IPrintInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual HRESULT QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_printObj;  
 
    class CEditObj : public IEditInterface  
 {  
    public: 
    CEditPrintObj* m_pParent;  
    virtual ULONG QueryInterface(REFIID iid,
    void** ppvObj);

    virtual ULONG AddRef();
virtual ULONG Release();

 } m_editObj;  
};  
```  
  
 Poniżej znajduje się całego wdrożenia:  
  
```  
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
 
HRESULT CEditPrintObj::QueryInterface(REFIID iid,
    void** ppvObj)  
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
 
HRESULT CEditPrintObj::CEditObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
 
ULONG CEditPrintObj::CPrintObj::AddRef()   
{   
    return m_pParent->AddRef();

}  
 
ULONG CEditPrintObj::CPrintObj::Release()   
{   
    return m_pParent->Release();

}  
 
HRESULT CEditPrintObj::CPrintObj::QueryInterface(
    REFIID iid,
    void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid,
    ppvObj);

}  
```  
  
 Zwróć uwagę, że większość [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementacji jest umieszczany w klasie CEditPrintObj zamiast duplikowania kod w CEditPrintObj::CEditObj i CEditPrintObj::CPrintObj. Zmniejsza ilość kodu i pozwala uniknąć błędów. W tym miejscu klucza punktu w interfejsie IUnknown jest możliwe do wywołania [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) pobrać wszystkie interfejsu może obsługiwać obiektu i z każdego z tych interfejsów jest możliwe, wykonaj te same. Oznacza to, że wszystkie [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkcji, które są dostępne z każdego interfejsu musi działać dokładnie tak samo. Aby dla tych obiektów do wywołania implementacji w "zewnętrzne do obiektu" wskaźnik wstecz jest używana (m_pParent). Wskaźnik m_pParent został zainicjowany podczas CEditPrintObj konstruktora. Następnie może implementować CEditPrintObj::CPrintObj::PrintObject, a także CEditPrintObj::CEditObj::EditObject. Dość fragmentem kodu został dodany do dodania jedną funkcję — możliwość edytowania obiektu. Na szczęście jest bardzo nietypowe dla interfejsów mieć tylko jeden element członkowski funkcji (chociaż się zdarzyć) i w takim przypadku EditObject i PrintObject będzie zazwyczaj można łączyć w jednym interfejsie.  
  
 Jest wiele wyjaśnienie i wiele kod Prosty scenariusz. Klasy MFC/OLE zapewniają prostszą alternatywę. MFC — implementacja używa technika podobny do sposobu komunikaty systemu Windows są opakowywane z mapy komunikatów. Tej funkcji jest nazywany *mapy interfejsu* jest omówiona w następnej sekcji.  
  
## <a name="mfc-interface-maps"></a>Mapy interfejsu MFC  
 MFC/OLE zawiera implementację "Map interfejsu" podobny "Mapy komunikatów" i "Mapy wysyłania" MFC w koncepcji i wykonywanie. Podstawowe funkcje MFC interfejsu map są następujące:  
  
-   Standardowa implementacja elementu [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), wbudowanych w `CCmdTarget` klasy.  
  
-   Konserwacja liczbę odwołań, zmodyfikowany przez [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [zlecenia](http://msdn.microsoft.com/library/windows/desktop/ms682317)  
  
-   Opartego na implementację danych [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)  
  
 Ponadto map interfejsów obsługują następujące funkcje:  
  
-   Obsługa tworzenia agregowaniu obiekty COM  
  
-   Obsługa użycia zagregowane obiekty w implementacji obiektu modelu COM  
  
-   Implementacja jest hookable i rozszerzalny  
  
 Aby uzyskać więcej informacji dotyczących agregacji, zobacz [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) tematu.  
  
 Obsługa mapy interfejsu MFC jest ścieżką do katalogu głównego w `CCmdTarget` klasy. `CCmdTarget`"*ma a*" odwołania liczby, a także wszystkie funkcje Członkowskie skojarzone z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) implementacji (liczba odwołań na przykład jest `CCmdTarget`). Aby utworzyć klasę, która obsługuje OLE COM, wyprowadzenia klasy z `CCmdTarget` i korzystanie z różnych makr oraz funkcje Członkowskie `CCmdTarget` do wykonania żądanej interfejsów. Implementacji MFC używa klasy zagnieżdżone w celu zdefiniowania każdej implementacji interfejsu, podobnie jak w powyższym przykładzie. To jest ułatwiono dzięki standardowej implementacji interfejsu IUnknown, a także liczbę makra, które części kodu powtarzających się wyeliminować.  
  
## <a name="interface-map-basics"></a>Podstawy mapy interfejsu  
  
#### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Aby zaimplementować klasę przy użyciu interfejsu MFC mapy  
  
1.  Dziedziczyć po klasie bezpośrednio lub pośrednio `CCmdTarget`.  
  
2.  Użyj `DECLARE_INTERFACE_MAP` funkcji w definicji klasy pochodnej.  
  
3.  Dla każdego interfejsu chcesz wspierać, użyj `BEGIN_INTERFACE_PART` i `END_INTERFACE_PART` makra w definicji klasy.  
  
4.  W pliku implementacji, należy użyć `BEGIN_INTERFACE_MAP` i `END_INTERFACE_MAP` makra, aby zdefiniować mapy interfejsu klasy.  
  
5.  Dla każdego identyfikatora IID obsługiwane, należy użyć `INTERFACE_PART` makro między `BEGIN_INTERFACE_MAP` i `END_INTERFACE_MAP` makra, aby zamapować ten identyfikator IID do konkretnego "części" klasy.  
  
6.  Implementuje zagnieżdżonych klas reprezentujących interfejsów, która jest obsługiwana.  
  
7.  Użyj `METHOD_PROLOGUE` makro dostępu do nadrzędnej `CCmdTarget`-pochodzi z obiektu.  
  
8. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) można delegować do `CCmdTarget` stosowania tych funkcji (`ExternalAddRef`, `ExternalRelease`, i `ExternalQueryInterface` ).  
  
 W powyższym przykładzie CPrintEditObj może zostać wdrożone w następujący sposób:  
  
```  
class CPrintEditObj : public CCmdTarget  
{  
public: *// member data and member functions for CPrintEditObj go here  
 
// Interface Maps  
protected:  
    DECLARE_INTERFACE_MAP() 
 
    BEGIN_INTERFACE_PART(EditObj,
    IEditInterface)  
    STDMETHOD_(void,
    EditObject)();
END_INTERFACE_PART(EditObj) 
 
    BEGIN_INTERFACE_PART(PrintObj,
    IPrintInterface)  
    STDMETHOD_(void,
    PrintObject)();
END_INTERFACE_PART(PrintObj) 
};  
```  
  
 Powyżej deklaracji tworzy klasę pochodzącą od `CCmdTarget`. `DECLARE_INTERFACE_MAP` Makro informuje platformę, że ta klasa mapy niestandardowy interfejs. Ponadto `BEGIN_INTERFACE_PART` i `END_INTERFACE_PART` makra definiować zagnieżdżonych klas, w tym przypadku z nazwami CEditObj i CPrintObj (X jest używany tylko w celu zróżnicowania zagnieżdżonych klas z globalnej klasy, które zaczynają się rozpoczynać się od "I"C"i interfejsu klasy "). Tworzone są dwa elementy zagnieżdżone tych klas: m_CEditObj i m_CPrintObj, odpowiednio. Makra automatycznie zadeklarować [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkcje; w związku z tym można zadeklarować tylko funkcje specyficzne dla tego interfejsu: EditObject i PrintObject (makro OLE `STDMETHOD` jest używany, aby `_stdcall` i wirtualnych słowa kluczowe są udostępniane jako odpowiednie dla platformy docelowej).  
  
 Aby zaimplementować interfejs mapy dla tej klasy:  
  
```  
BEGIN_INTERFACE_MAP(CPrintEditObj,
    CCmdTarget)  
    INTERFACE_PART(CPrintEditObj,
    IID_IPrintInterface,
    PrintObj)  
    INTERFACE_PART(CPrintEditObj,
    IID_IEditInterface,
    EditObj)  
END_INTERFACE_MAP()  
```  
  
 Utworzone połączenie IID_IPrintInterface IID m_CPrintObj i IID_IEditInterface z m_CEditObj odpowiednio. `CCmdTarget` Implementacja [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) (`CCmdTarget::ExternalQueryInterface`) za pomocą tej mapy wskaźniki m_CPrintObj i m_CEditObj na żądanie. Nie jest konieczne uwzględnienie wpis dotyczący `IID_IUnknown`; ramach użyje pierwszego interfejsu mapy (w tym przypadku m_CPrintObj) po `IID_IUnknown` jest wymagane.  
  
 Mimo że `BEGIN_INTERFACE_PART` makro automatycznie zadeklarowany [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkcje dla Ciebie, nadal należy wdrożyć je:  
  
```  
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalAddRef();

}  
 
ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return pThis->ExternalRelease();

}  
 
HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj)  
    return (HRESULT)pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
 
void FAR EXPORT CEditPrintObj::XEditObj::EditObject()  
{  
    METHOD_PROLOGUE(CEditPrintObj,
    EditObj) *// code to "Edit" the object,
    whatever that means...  
}  
```  
  
 Implementację CEditPrintObj::CPrintObj, mogą być podobne do powyżej definicje CEditPrintObj::CEditObj. Mimo że będzie można utworzyć makra, który może służyć do automatycznego generowania tych funkcji (ale we wcześniejszej części programowanie MFC/OLE miało to miejsce), staje się trudny można ustawić punktów przerwania, generując makra więcej niż jeden wiersz kodu. Z tego powodu ten kod jest rozwinięta ręcznie.  
  
 Za pomocą implementacji framework mapy komunikatów, istnieje kilka rzeczy, które nie zostały należy zrobić:  
  
-   Implementuje metody QueryInterface  
  
-   AddRef wdrożenie i wersji  
  
-   Deklarowanie żadnej z tych metod wbudowanych w obu interfejsów sieci  
  
 Ponadto platformę używa mapy komunikatów wewnętrznie. Dzięki temu można dziedziczyć po klasie framework powiedz `COleServerDoc`, który już obsługuje niektórych interfejsów i zawiera elementy zastępcze lub ma zostać dodany do interfejsami przez platformę. Można to zrobić, ponieważ w ramach w pełni obsługuje dziedziczenia mapy interfejsu z klasy podstawowej. Dlaczego jest przyczyną `BEGIN_INTERFACE_MAP` przyjmuje jako drugi parametr nazwę klasy podstawowej.  
  
> [!NOTE]
>  Zazwyczaj nie jest możliwe ponowne użycie implementacji wbudowanych implementacje interfejsów OLE MFC przez dziedziczenie osadzonych specjalizacja interfejsu z wersji biblioteki MFC. Nie jest to możliwe ponieważ korzystanie z `METHOD_PROLOGUE` makra w celu uzyskania dostępu do zawierający `CCmdTarget`-oznacza obiekt pochodne *stałego przesunięcia* osadzonego obiektu z `CCmdTarget`-pochodzi z obiektu. Oznacza to, na przykład XMyAdviseSink osadzone nie może pochodzić od implementacji MFC w `COleClientItem::XAdviseSink`, ponieważ XAdviseSink korzysta z tego od określonego przesunięcia od góry `COleClientItem` obiektu.  
  
> [!NOTE]
>  Można jednak delegować do implementacji MFC dla wszystkich funkcji, które mają MFC domyślne zachowanie. Jest to wykonywane w implementacji MFC `IOleInPlaceFrame` (XOleInPlaceFrame) w `COleFrameHook` klasy (następuje delegacja do m_xOleInPlaceUIWindow dla funkcji). W tym projekcie została wybrana, aby zmniejszyć rozmiar środowiska uruchomieniowego obiektów implementujących interfejsy wielu; eliminuje potrzebę wskaźnik Wstecz (takie jak m_pParent sposób został użyty w poprzedniej sekcji).  
  
### <a name="aggregation-and-interface-maps"></a>Agregacja i map — interfejs  
 Oprócz obsługi autonomicznej obiektów COM, MFC obsługuje agregacji. Agregacja sam jest zbyt złożony temat omówimy Zapoznaj się [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx) tematu, aby uzyskać więcej informacji na temat agregacji. Ta uwaga po prostu opisano obsługę agregacji wbudowane mapy framework i interfejsu.  
  
 Istnieją dwa sposoby używania agregacji: (1) przy użyciu obiektu COM, który obsługuje agregację i (2) implementacja może być agregowany przez inny obiekt. Te możliwości mogą określane jako "za pomocą obiektu agregacji" i "wprowadzenie, obiekt będzie się agregowaniu". MFC obsługuje zarówno.  
  
### <a name="using-an-aggregate-object"></a>Przy użyciu obiektu agregacji  
 Aby użyć obiektu agregacji, musi być określony sposób powiązać agregacji do mechanizmu QueryInterface. Innymi słowy obiektu agregacji musi zachowują się tak, jakby jest natywny część obiektu. W jaki sposób powoduje wiązania w interfejsie MFC mapowania mechanizmu oprócz `INTERFACE_PART` makra, w przypadku, gdy obiekt zagnieżdżony jest mapowany na IID, można również zadeklarować obiektu agregacji w ramach Twojej `CCmdTarget` klasy. Aby to zrobić, `INTERFACE_AGGREGATE` makro jest używane. Dzięki temu można określić zmienną członkowską (który musi być wskaźnikiem do [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) lub klasy), której ma zostać włączone do mechanizmu mapy interfejsu. Jeśli wskaźnik nie ma wartości NULL podczas `CCmdTarget::ExternalQueryInterface` jest wywoływana, platforma automatycznie wywoła obiektu agregacji [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) funkcji członkowskiej, jeśli `IID` żądanie nie jest jednym z natywnego `IID`s obsługiwane przez `CCmdTarget` samego obiektu.  
  
##### <a name="to-use-the-interfaceaggregate-macro"></a>Aby użyć makra INTERFACE_AGGREGATE  
  
1.  Deklaruje zmienną członkowską ( `IUnknown*`) zawierający wskaźnik do obiektu agregacji.  
  
2.  Obejmują `INTERFACE_AGGREGATE` makra w mapie interfejsu odwołuje się do zmiennej członkowskiej według nazwy.  
  
3.  W pewnym momencie (zazwyczaj podczas `CCmdTarget::OnCreateAggregates`), zainicjować zmiennej członkowskiej inną niż NULL.  
  
 Na przykład:  
  
```  
class CAggrExample : public CCmdTarget  
{  
public:  
    CAggrExample();

 
protected:  
    LPUNKNOWN m_lpAggrInner;  
    virtual BOOL OnCreateAggregates();

 
    DECLARE_INTERFACE_MAP() *// "native" interface part macros may be used here  
};  
 
CAggrExample::CAggrExample()  
{  
    m_lpAggrInner = NULL;  
}  
 
BOOL CAggrExample::OnCreateAggregates()  
{ *// wire up aggregate with correct controlling unknown  
    m_lpAggrInner = CoCreateInstance(CLSID_Example,  
    GetControllingUnknown(),
    CLSCTX_INPROC_SERVER,  
    IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)  
    return FALSE; *// optionally,
    create other aggregate objects here  
    return TRUE;  
}  
 
BEGIN_INTERFACE_MAP(CAggrExample,
    CCmdTarget) *// native "INTERFACE_PART" entries go here  
    INTERFACE_AGGREGATE(CAggrExample,
    m_lpAggrInner)  
END_INTERFACE_MAP()  
```  
  
 Zmienna m_lpAggrInner jest ustawiana w Konstruktorze wartości null. Platformę ignoruje zmienną członkowską NULL w implementacji domyślnej [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). `OnCreateAggregates`jest dobrym miejscem do faktycznie utworzyć obiekty agregacji. Musisz wywołać ją jawnie w przypadku tworzenia obiektu poza implementacji MFC `COleObjectFactory`. Przyczyna tworzenie wartości zagregowanych w `CCmdTarget::OnCreateAggregates` oraz użycie `CCmdTarget::GetControllingUnknown` staną się widoczne podczas tworzenia obiektów agregowaniu omówione.  
  
 Ta technika zapewni obiektu wszystkich interfejsów, które obsługuje obiektu agregacji oraz jego natywnych interfejsów. Jeśli chcesz tylko podzestaw interfejsów, które obsługuje agregacji, można zastąpić `CCmdTarget::GetInterfaceHook`. Dzięki temu można bardzo niskiego poziomu hookability, podobnie jak [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521). Zwykle ma wszystkich interfejsów, które obsługuje agregacji.  
  
### <a name="making-an-object-implementation-aggregatable"></a>Co się agregowaniu implementacji obiektu  
 Dla obiekt się agregowaniu, implementacja [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) należy przekazać "kontrolowanie nieznany". Innymi słowy, go jako część obiektu go należy delegować [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) na inny obiekt również pochodzi od [ IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). To "Nieznany kontrolowanie" jest dostarczane do obiektu podczas jego tworzenia, oznacza to, że są dostarczane do implementacji `COleObjectFactory`. To wdrożenie zawiera niewielkiej liczby dodatkowych czynności, a w niektórych przypadkach nie jest pożądane, więc MFC sprawia, że jest to opcjonalne. Aby włączyć obiekt się agregowaniu, należy wywołać `CCmdTarget::EnableAggregation` z konstruktora obiektu.  
  
 Jeśli obiekt korzysta również agregacje, również należy koniecznie Podaj prawidłowego "Nieznany kontrolowanie" obiekty agregacji. Zwykle to [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) wskaźnika jest przekazywany do obiektu po utworzeniu agregacji. Na przykład parametr parametr pUnkOuter ma "kontrolowanie nieznany" dla obiektów utworzonych za pomocą `CoCreateInstance`. Poprawne wskaźnik "kontrolowanie nieznany" mogą być pobierane przez wywołanie `CCmdTarget::GetControllingUnknown`. Wartość zwracana z tej funkcji, jednak nie jest prawidłowy w konstruktorze. Z tego powodu zaleca się tworzenie z wartości zagregowanych tylko w zastępująca `CCmdTarget::OnCreateAggregates`, gdzie wartość zwrotu z `GetControllingUnknown` jest niezawodne, nawet jeśli utworzone na podstawie `COleObjectFactory` implementacji.  
  
 Ważne jest również czy obiekt manipulowania liczba niepoprawne odwołanie podczas dodawania lub zwalniania liczby sztuczne odwołań. Aby upewnić się, jest to możliwe, zawsze wywołać `ExternalAddRef` i `ExternalRelease` zamiast `InternalRelease` i `InternalAddRef`. Rzadko wywołać `InternalRelease` lub `InternalAddRef` dla klasy, która obsługuje agregacji.  
  
### <a name="reference-material"></a>Materiały informacyjne  
 Zaawansowanego wykorzystania OLE, takie jak Definiowanie własnych interfejsów lub przesłonięcie framework implementacji interfejsów OLE wymaga użycia podstawowy mechanizm mapy interfejsu.  
  
 W tej sekcji omówiono każdego makra i interfejsy API, które jest używane do implementowania te zaawansowane funkcje.  
  
### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation — Opis elementu funkcja  
  
```  
 
void EnableAggregation();

 
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w konstruktorze klasy pochodnej, jeśli chcesz obsługuje OLE agregacji w przypadku obiektów tego typu. Przygotowuje to specjalne implementacji interfejsu IUnknown, który jest wymagane dla obiektów agregowaniu.  
  
### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface — Opis elementu funkcja  
  
```  
 
    DWORD ExternalQueryInterface(constvoidFAR* lpIID, LPVOIDFAR* ppvObj);
```  
  
## <a name="remarks"></a>Uwagi  
  
#### <a name="parameters"></a>Parametry  
 `lpIID`  
 Wskaźnik daleko IID (pierwszy argument funkcji QueryInterface)  
  
 `ppvObj`  
 Wskaźnik IUnknown * (drugi argument funkcji QueryInterface)  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w implementacji interfejsu IUnknown dla każdego interfejsu klasy implementuje. Ta funkcja udostępnia standardowej implementacji opartej na danych QueryInterface oparte na mapie interfejsu użytkownika obiektu. Jest zwracana wartość HRESULT rzutowania. Obiekt jest agregowana, ta funkcja wywoła "Kontrolowanie IUnknown" zamiast mapę interfejsu lokalnego.  
  
### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef — Opis elementu funkcja  
  
```  
 
DWORD ExternalAddRef();

 
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w implementacji IUnknown::AddRef dla każdego interfejsu klasy implementuje. Wartość zwracana jest liczba nowych odwołania do obiektu klasy. Obiekt jest agregowana, ta funkcja wywoła "Kontrolowanie IUnknown" zamiast manipulowanie liczba lokalnego odwołania.  
  
### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease — Opis elementu funkcja  
  
```  
 
DWORD ExternalRelease();

 
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w implementacji IUnknown::Release dla każdego interfejsu klasy implementuje. Wartości zwracanej wskazuje liczba nowych odwołanie do obiektu. Obiekt jest agregowana, ta funkcja wywoła "Kontrolowanie IUnknown" zamiast manipulowanie liczba lokalnego odwołania.  
  
### <a name="declareinterfacemap--macro-description"></a>Declare_interface_map — — Opis elementu makro  
  
```  
 
DECLARE_INTERFACE_MAP  
 
```  
  
## <a name="remarks"></a>Uwagi  
 Używanie tego makra w dowolnej klasy pochodzące z `CCmdTarget` będą mieć mapy interfejsu. Używane w znacznie taki sam sposób jak `DECLARE_MESSAGE_MAP`. To wywołanie makra powinna zostać umieszczona w definicji klasy, zazwyczaj w nagłówku (. H) pliku. Klasa o `DECLARE_INTERFACE_MAP` musi definiować mapy interfejsu w pliku implementacji (. CPP) z `BEGIN_INTERFACE_MAP` i `END_INTERFACE_MAP` makra.  
  
### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>Begin_interface_part — i end_interface_part — — makro opisów  
  
```  
 
    BEGIN_INTERFACE_PART(
 localClass,   
    iface);

END_INTERFACE_PART(
 localClass)  
```  
  
## <a name="remarks"></a>Uwagi  
  
#### <a name="parameters"></a>Parametry  
 `localClass`  
 Nazwa klasy, która implementuje interfejs  
  
 `iface`  
 Nazwa interfejsu, który implementuje ta klasa  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego interfejsu, który będzie implementowany klasy, musisz mieć `BEGIN_INTERFACE_PART` i `END_INTERFACE_PART` pary. Te makra zdefiniuj lokalnej klasy pochodzącej od definiujących oraz zmiennej członkowskiej osadzonych w tej klasy interfejsu OLE. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), i [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) elementy członkowskie są deklarowane jako automatycznie. Musi zawierać deklaracje do innych funkcji elementu członkowskiego, które są częścią interfejsu implementowana (deklaracje te są umieszczane między `BEGIN_INTERFACE_PART` i `END_INTERFACE_PART` makr).  
  
 `iface` Argument jest interfejsem OLE, który chcesz wdrożyć, takich jak `IAdviseSink`, lub `IPersistStorage` (lub własny niestandardowy interfejs).  
  
 `localClass` Argument jest nazwą klasy lokalnej, która zostanie zdefiniowana. "X" zostanie automatycznie dołączony do nazwy. Konwencja nazewnictwa jest używany w celu uniknięcia konfliktów z klasami globalne o takiej samej nazwie. Ponadto Nazwa osadzonego elementu członkowskiego, taka sama jak `localClass` nazwy z wyjątkiem jest poprzedzony "m_x".  
  
 Na przykład:  
  
```  
BEGIN_INTERFACE_PART(MyAdviseSink,
    IAdviseSink)  
    STDMETHOD_(void,
    OnDataChange)(LPFORMATETC,
    LPSTGMEDIUM);

    STDMETHOD_(void,
    OnViewChange)(DWORD,
    LONG);

    STDMETHOD_(void,
    OnRename)(LPMONIKER);

 STDMETHOD_(void,
    OnSave)();
STDMETHOD_(void,
    OnClose)();

END_INTERFACE_PART(MyAdviseSink) 
```  
  
 zdefiniowane lokalnej klasy o nazwie XMyAdviseSink pochodną IAdviseSink i elementem członkowskim klasy, w którym jest zadeklarowany jako o nazwie m_xMyAdviseSink.Note:  
  
> [!NOTE]
>  Wiersze rozpoczynające się od `STDMETHOD`_ zasadniczo są kopiowane z OLE2. H i nieco zmodyfikowany. Kopiowanie ich z OLE2. H można zmniejszyć liczbę błędów, które są trudne do rozwiązania.  
  
### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>Begin_interface_map — i end_interface_map — — makro opisów  
  
```  
 
    BEGIN_INTERFACE_MAP(
 theClass,   
    baseClass)END_INTERFACE_MAP 
```  
  
## <a name="remarks"></a>Uwagi  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, w którym ma być zdefiniowana mapy interfejsu  
  
 `baseClass`  
 Klasy, z którego `theClass` pochodną.  
  
## <a name="remarks"></a>Uwagi  
 `BEGIN_INTERFACE_MAP` i `END_INTERFACE_MAP` makra są używane w pliku implementacji w celu faktycznego zdefiniowania mapy interfejsu. Dla każdego interfejsu, która jest zaimplementowana istnieje co najmniej jeden `INTERFACE_PART` makro wywołań. Dla każdego wartość zagregowaną, która korzysta z klasy, istnieje `INTERFACE_AGGREGATE` wywołanie makra.  
  
### <a name="interfacepart--macro-description"></a>Interface_part — — Opis elementu makro  
  
```  
 
    INTERFACE_PART(
 theClass,   
    iid, 
    localClass) 
```  
  
## <a name="remarks"></a>Uwagi  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy zawierającej mapy interfejsu.  
  
 `iid`  
 `IID` Który ma być zmapowana do osadzonego klasy.  
  
 `localClass`  
 Nazwa klasy lokalnej (mniej "X").  
  
## <a name="remarks"></a>Uwagi  
 To makro jest używane między `BEGIN_INTERFACE_MAP` makro i `END_INTERFACE_MAP` makro dla każdego interfejsu obiektu będzie obsługiwać. Umożliwia mapowanie identyfikatora IID do elementu członkowskiego klasy oznaczona `theClass` i `localClass`. "m_x" zostanie dodany do `localClass` automatycznie. Należy pamiętać, że więcej niż jeden `IID` może być skojarzony z jednym elementem członkowskim. Jest to przydatne, gdy wdrażania tylko "najbardziej pochodnej" interfejs i udostępniać również wszystkie interfejsy pośrednich. Dobrym przykładem jest `IOleInPlaceFrameWindow` interfejsu. Swojej hierarchii wygląda następująco:  
  
```  
IUnknown  
    IOleWindow 
    IOleUIWindow 
    IOleInPlaceFrameWindow 
```  
  
 Jeśli obiekt implementuje `IOleInPlaceFrameWindow`, klient może `QueryInterface` na żadnym z tych interfejsów: `IOleUIWindow`, `IOleWindow`, lub [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), poza interfejs "najbardziej pochodnej" `IOleInPlaceFrameWindow` (znajdujący się w rzeczywistości Implementowanie). Do obsługi tego można użyć więcej niż jednej `INTERFACE_PART` makro mapować każdy interfejs podstawowy do `IOleInPlaceFrameWindow` interfejsu:  
  
 w pliku definicji klasy:  
  
```  
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)  
```  
  
 Plik implementacji klasy:  
  
```  
BEGIN_INTERFACE_MAP(CMyWnd,
    CFrameWnd)  
    INTERFACE_PART(CMyWnd,
    IID_IOleWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleUIWindow,
    MyFrameWindow)  
    INTERFACE_PART(CMyWnd,
    IID_IOleInPlaceFrameWindow,
    MyFrameWindow)  
END_INTERFACE_MAP  
```  
  
 Platformę zapewnia obsługę interfejsu IUnknown, ponieważ jest zawsze wymagane.  
  
### <a name="interfacepart--macro-description"></a>Interface_part — — Opis elementu makro  
  
```  
 
    INTERFACE_AGGREGATE(
 theClass,   
    theAggr) 
```  
  
## <a name="remarks"></a>Uwagi  
  
#### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy zawierającej mapy interfejsu  
  
 `theAggr`  
 Nazwa zmiennej członkowskiej, która ma być agregowany.  
  
## <a name="remarks"></a>Uwagi  
 To makro jest używane mówić platformę wykorzystanie klasy obiektu agregacji. Musi znajdować się między `BEGIN_INTERFACE_PART` i `END_INTERFACE_PART` makra. Obiekt agregacji jest oddzielny obiekt pochodzi od [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509). Za pomocą agregacji i `INTERFACE_AGGREGATE` makra, możesz wprowadzić wszystkich interfejsów, które obsługuje agregacji są bezpośrednio obsługiwane przez obiekt. `theAggr` Argument jest po prostu nazwę zmiennej członkowskiej, która jest pochodną klasy [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) (bezpośrednio lub pośrednio). Wszystkie `INTERFACE_AGGREGATE` wykonaj makra `INTERFACE_PART` makra w mapie interfejsów.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

