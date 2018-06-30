---
title: 'TN039: Implementacja automatyzacji MFC OLE | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9dcc179b1481c4f1f6b6a0773bba792eefffae25
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122124"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: implementacja automatyzacji MFC/OLE

> [!NOTE]
> Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.

## <a name="overview-of-ole-idispatch-interface"></a>Przegląd interfejsu IDispatch OLE

`IDispatch` Interfejs jest sposób za pomocą którego aplikacje uwidacznia metody i właściwości, tak aby wprowadzić inne aplikacje, takie jak Visual BASIC lub innych języków, użyj funkcji aplikacji. To najważniejszy element ten interfejs `IDispatch::Invoke` funkcji. MFC używa "mapy wysyłania" do zaimplementowania `IDispatch::Invoke`. Mapy wysyłania zawiera informacje implementacji MFC na układ lub "kształtu" Twoje `CCmdTarget`-pochodnej klasy, w taki sposób, że można bezpośrednio manipulowania właściwościami obiektu lub wywołać elementu członkowskiego funkcji w ramach obiektu do zaspokojenia `IDispatch::Invoke` żądania.

W większości przypadków ClassWizard i MFC współpracują w celu Ukryj większość szczegóły automatyzacji OLE z programisty aplikacji. Programistę koncentruje się na rzeczywiste funkcji do udostępnienia w aplikacji i nie trzeba się martwić o podstawowej żmudne procesy.

Brak przypadków, gdy konieczne jest zrozumienie MFC zadań w tle. Ta uwaga będzie dotyczyć jak przypisuje platformę **DISPID**s do funkcji Członkowskich i właściwości. Wiedza algorytmu MFC używa do przypisywania **DISPID**s jest konieczne tylko wtedy, gdy trzeba wiedzieć, identyfikatory, takie jak podczas tworzenia biblioteki"typu" obiektów w aplikacji.

## <a name="mfc-dispid-assignment"></a>Przypisanie MFC DISPID

Chociaż Automatyzacja (Visual Basic użytkownika, na przykład), użytkownik końcowy widzi rzeczywiste nazwy automatyzację włączone właściwości i metody w kodzie ich (na przykład obiektu ShowWindow) wdrożenia `IDispatch::Invoke` nie otrzyma rzeczywiste nazwy. Ze względu na optymalizację odbiera **DISPID**, która jest 32-bitowe "magicznych plik cookie" opisujący metody lub właściwości, która ma być dostępny. Te **DISPID** wartości są zwracane z `IDispatch` wdrożenia za pomocą innej metody o nazwie `IDispatch::GetIDsOfNames`. Automatyzacja aplikacji klient nawiąże połączenie `GetIDsOfNames` po dla każdego elementu członkowskiego lub właściwości zamierza uzyskują dostęp do pamięci podręcznej ich nowsze wywołania `IDispatch::Invoke`. W ten sposób wyszukiwania kosztowne ciągu jest wykonywane tylko raz na użycie obiektu zamiast raz na `IDispatch::Invoke` wywołania.

Określa MFC **DISPID**s dla każdej metody i właściwości oparte na dwie czynności:

- Odległość od początku mapy wysyłania (względem 1)

- Odległość mapy wysyłania z najbardziej pochodnej klasy (względną 0)

**DISPID** jest podzielony na dwie części. **LOWORD** z **DISPID** zawiera pierwszy składnik odległość od początku mapy wysyłania. **HIWORD** zawiera odległość od najbardziej pochodnej klasy. Na przykład:

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

Jak widać, istnieją dwie klasy, które uwidacznia interfejsów automatyzacji OLE. Jeden z tych klas pochodzi od innych i w związku z tym wykorzystuje funkcje klasy podstawowej, w tym części automatyzacji OLE ("x" i "y" właściwości w tym przypadku).

Wygeneruje MFC **DISPID**s dla klasy CDispPoint w następujący sposób:

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Ponieważ właściwości nie są w klasie podstawowej, **HIWORD** z **DISPID** zawsze wynosi zero (odległość od najbardziej pochodnej klasy dla CDispPoint wynosi zero).

Wygeneruje MFC **DISPID**s dla klasy CDisp3DPoint w następujący sposób:

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Podano właściwości Z **DISPID** z zerem **HIWORD** , ponieważ jest on zdefiniowany w klasie jest ujawniany przez właściwości CDisp3DPoint. Ponieważ właściwości X i Y są definiowane w klasie podstawowej, **HIWORD** z **DISPID** ma wartość 1, ponieważ jest klasa, w którym te właściwości są definiowane w odległości pochodnym jedną z najbardziej pochodnej klasy.

> [!NOTE]
> **LOWORD** zawsze jest określany przez pozycja w planie, nawet jeśli istnieją wpisy w mapie z jawnym **DISPID** (zobacz następną sekcję, aby uzyskać informacje na **_ID** wersje `DISP_PROPERTY` i `DISP_FUNCTION` makr).

## <a name="advanced-mfc-dispatch-map-features"></a>Zaawansowane funkcje mapy wysyłania MFC

Istnieje szereg dodatkowych funkcji, które nie obsługują ClassWizard w tej wersji programu Visual C++. Obsługuje ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, i `DISP_PROPERTY_EX` definiującą odpowiednio metoda, właściwość zmiennej elementu członkowskiego i Pobierz/ustaw właściwość funkcja elementu członkowskiego,. Te możliwości są zazwyczaj są wystarczające do tworzenia większość serwerów automatyzacji.

Następujące dodatkowe makra można użyć w przypadku makra ClassWizard obsługiwane są nieodpowiednie: `DISP_PROPERTY_NOTIFY`, i `DISP_PROPERTY_PARAM`.

## <a name="disppropertynotify--macro-description"></a>Disp_property_notify — — Opis elementu makro

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*  
 Nazwa klasy.

*pszName*  
 Zewnętrzna nazwa właściwości.

*memberName*  
 Nazwa zmiennej członkowskiej, w którym przechowywany jest właściwość.

*pfnAfterSet*  
 Nazwa elementu członkowskiego funkcja wywoływana, gdy właściwość zostanie zmieniona.

*vtPropType*  
 Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

To makro jest disp_property —, z wyjątkiem tego, że akceptuje dodatkowy argument. Dodatkowy argument, *pfnAfterSet,* powinna być funkcji członkowskiej, która nie zwraca żadnego i nie przyjmuje żadnych parametrów "void OnPropertyNotify()". Będzie ona wywoływana **po** zmiennej członkowskiej został zmodyfikowany.

## <a name="disppropertyparam--macro-description"></a>Disp_property_param — — Opis elementu makro

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*  
 Nazwa klasy.

*pszName*  
 Zewnętrzna nazwa właściwości.

*memberGet*  
 Nazwa funkcji członkowskiej, używany do pobierania właściwości.

*zestaw elementów członkowskich*  
 Nazwa funkcji członkowskiej używany do ustawiania właściwości.

*vtPropType*  
 Wartość określająca typ właściwości.

*vtsParams*  
 Ciąg miejsca rozdzielone VTS_ dla każdego parametru.

### <a name="remarks"></a>Uwagi

Podobnie jak disp_property_ex — makro, to makro definiuje właściwość dostęp do osobnych funkcje Członkowskie Get i Set. To makro, jednak pozwala określić listę parametrów dla właściwości. Jest to przydatne w przypadku implementowania właściwości, które są indeksowane lub sparametryzowana w inny sposób. Parametry zawsze kładzie się najpierw, następuje nową wartość dla właściwości. Na przykład:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

odpowiada get i set funkcji elementów członkowskich:

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID — Makro opisów

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*  
Nazwa klasy.

*pszName*  
Zewnętrzna nazwa właściwości.

*identyfikator DISPID*  
Stały identyfikator DISPID właściwości lub metody.

*pfnGet*  
Nazwa funkcji członkowskiej, używany do pobierania właściwości.

*pfnSet*  
Nazwa funkcji członkowskiej używany do ustawiania właściwości.

*memberName*  
Nazwa zmiennej członkowskiej, aby mapować do właściwości

*vtPropType*  
Wartość określająca typ właściwości.

*vtsParams*  
Ciąg miejsca rozdzielone VTS_ dla każdego parametru.

### <a name="remarks"></a>Uwagi

Makra te umożliwiają określenie **DISPID** zamiast czekać MFC automatycznie przypisać jeden. Te zaawansowane makra mają takie same nazwy, z wyjątkiem ten identyfikator jest dołączany do nazwy makra (np. **DISP_PROPERTY_ID**) i identyfikator jest określany przez parametr określony tuż po *pszName* parametru. Zobacz AFXDISP. H, aby uzyskać więcej informacji na temat tych makr. **_ID** wpisy muszą znajdować się na końcu mapy wysyłania. Będzie miało wpływ na automatyczne **DISPID** Generowanie w taki sam sposób jak niż **_ID** czy wersji makra ( **DISPID**s są określane na podstawie pozycji). Na przykład:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

Identyfikator DISPID MFC zostanie wygenerowany dla klasy CDisp3DPoint w następujący sposób:

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

Określanie ustalonego **DISPID** przydaje się do zachowania zgodności z poprzednimi wersjami istniejących interfejs wysyłania lub zaimplementować niektórych właściwości lub metody zdefiniowane w systemie (zwykle wskazywany przez ujemny  **Identyfikator DISPID**, takich jak **DISPID_NEWENUM** kolekcji).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Trwa pobieranie interfejsu IDispatch dla COleClientItem

Wiele serwerów będzie obsługiwać automatyzacji w ich obiekty dokumentu, wraz z funkcjonalności serwera OLE. W celu uzyskania dostępu do tego interfejsu automatyzacji, należy go bezpośrednio `COleClientItem::m_lpObject` zmiennej członkowskiej. Poniższy kod pobiera `IDispatch` interfejsu dla obiekt pochodną `COleClientItem`. Poniższy kod można uwzględnić w aplikacji, jeśli okaże się tej funkcji konieczne:

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

Interfejs wysyłania zwracane z tej funkcji można następnie używane bezpośrednio lub dołączone do `COleDispatchDriver` dla bezpieczny dostęp. Jeśli używasz go bezpośrednio, upewnij się, należy wywołać jej `Release` elementu członkowskiego kiedy za pomocą wskaźnika ( `COleDispatchDriver` destruktor nie).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  
