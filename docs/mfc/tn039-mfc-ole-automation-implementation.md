---
title: 'TN039: Implementacja automatyzacji MFC / OLE | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 59eca912aab816f75ce8d585036f8f900c4f7bd3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399882"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: implementacja automatyzacji MFC/OLE

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

## <a name="overview-of-ole-idispatch-interface"></a>Omówienie interfejsu IDispatch OLE

`IDispatch` Interfejs jest oznacza, że za pomocą którego aplikacje uwidocznić metody i właściwości, takie, które mogą ułatwić innych aplikacji, takich jak Visual BASIC lub innych języków, korzystać z funkcji aplikacji. Najważniejsza część ten interfejs jest `IDispatch::Invoke` funkcji. MFC wykorzystuje "mapy wysyłania" do zaimplementowania `IDispatch::Invoke`. Mapa wysyłania udostępnia informacje o implementacji MFC na układ lub "kształt" Twoje `CCmdTarget`-pochodnych klas, w taki sposób, że możesz bezpośrednio modyfikować właściwości obiektu lub wywołać element członkowski funkcji w ramach obiektu do zaspokojenia `IDispatch::Invoke` żądania.

W większości przypadków ClassWizard i MFC współpracują w celu ukrycia najbardziej szczegółowe informacje o automatyzacji OLE z programistom. Programistę koncentruje się na rzeczywistych funkcjonalności do udostępnienia w aplikacji i nie musisz martwić się o podstawowy nadmiar.

Istnieją przypadki, jednak, gdzie jest niezbędne do zrozumienia MFC działania w tle. Ta uwaga zajmie się jak przypisuje ramach **DISPID**s, aby właściwości i elementów członkowskich. Wiedzę na temat algorytmu, MFC wykorzystuje do przypisywania **DISPID**s jest konieczne tylko wtedy, gdy trzeba znać identyfikatory, takie jak podczas tworzenia "biblioteki typów" dla obiektów w aplikacji.

## <a name="mfc-dispid-assignment"></a>Przypisanie MFC DISPID

Mimo że automatyzacji (Visual Basic użytkownika, na przykład), użytkownik końcowy widzi rzeczywistymi nazwami automatyzację włączone właściwości i metod w ich kodzie (na przykład obiektu ShowWindow) implementacja `IDispatch::Invoke` nie otrzyma rzeczywistymi nazwami. Ze względu na optymalizację odbiera **DISPID**, który jest 32-bitowy "magic plik cookie", który opisuje metodę lub właściwość, która ma być dostępny. Te **DISPID** wartości są zwracane z `IDispatch` wdrożenia za pomocą innej metody, o nazwie `IDispatch::GetIDsOfNames`. Wywoła aplikację automatyzacji klienta `GetIDsOfNames` po dla każdego elementu członkowskiego lub właściwość zamierza dostęp oraz buforowanie ich nowsze wywołania `IDispatch::Invoke`. W ten sposób wyszukiwanie ciągu kosztowne czynność jest wykonywana tylko raz na użycie obiektu zamiast raz na `IDispatch::Invoke` wywołania.

Określa MFC **DISPID**s dla każdej metody i właściwości oparte na dwie rzeczy:

- Odległość w górnej części mapy wysyłania (względem 1)

- Odległość Mapa wysyłania z najbardziej pochodnej klasy (0 względną)

**DISPID** jest podzielona na dwie części. **LOWORD** z **DISPID** zawiera pierwszy składnik odległości od górnej krawędzi Mapa wysyłania. **HIWORD** zawiera odległość od najbardziej pochodnej klasy. Na przykład:

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

Jak widać, istnieją dwie klasy, które uwidacznia interfejsów automatyzacji OLE. Jedną z tych klas jest tworzony na podstawie innych i dlatego wykorzystuje funkcje klasy bazowej, w tym częścią automatyzacji OLE ("x" i "y" właściwości w tym przypadku).

Biblioteki MFC spowoduje wygenerowanie **DISPID**s dla klasy CDispPoint w następujący sposób:

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Ponieważ właściwości nie są w klasie bazowej **HIWORD** z **DISPID** zawsze wynosi zero (odległość od najbardziej pochodnej klasy dla CDispPoint jest równy zero).

Biblioteki MFC spowoduje wygenerowanie **DISPID**s dla klasy CDisp3DPoint w następujący sposób:

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Biorąc pod uwagę właściwości Z **DISPID** cyfrą zero: **HIWORD** , ponieważ jest on zdefiniowany w klasie, która jest ujawniany przez właściwości CDisp3DPoint. Ponieważ właściwości X i Y są zdefiniowane w klasie bazowej **HIWORD** z **DISPID** wynosi 1, ponieważ w odległości co pochodnym klasy najbardziej pochodnej klasy, w którym zdefiniowano tych właściwości.

> [!NOTE]
> **LOWORD** zawsze zależy od położenia na mapie, nawet jeśli istnieje wpisy mapy za pomocą jawnego **DISPID** (zobacz następną sekcję, aby uzyskać informacje na **_identyfikator** wersje `DISP_PROPERTY` i `DISP_FUNCTION` makr).

## <a name="advanced-mfc-dispatch-map-features"></a>Zaawansowane funkcje mapy wysyłania MFC

Istnieje szereg dodatkowych funkcji, które nie obsługuje ClassWizard w tej wersji programu Visual C++. Obsługuje ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, i `DISP_PROPERTY_EX` który zdefiniować metodę, właściwość zmiennej elementu członkowskiego i pobierania/ustawiania właściwości funkcji składowej, odpowiednio. Te możliwości są zazwyczaj wszystko, co jest potrzebne do utworzenia większość serwerów automatyzacji.

Następujące dodatkowe makra można użyć, gdy makra ClassWizard obsługiwane nie są odpowiednie: `DISP_PROPERTY_NOTIFY`, i `DISP_PROPERTY_PARAM`.

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY — Opis makra

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości.

*memberName*<br/>
Nazwa zmiennej składowej, w którym przechowywany jest właściwość.

*pfnAfterSet*<br/>
Nazwa elementu członkowskiego funkcja do wywołania po zmianie właściwości.

*vtPropType*<br/>
Wartość, określając typ właściwości.

### <a name="remarks"></a>Uwagi

To makro jest znacznie jak DISP_PROPERTY, z tą różnicą, że akceptuje dodatkowy argument. Dodatkowy argument *pfnAfterSet,* powinna być funkcją składową, która nie zwraca żadnego i nie przyjmuje żadnych parametrów "void OnPropertyNotify()". Będzie ona wywoływana **po** zmiennej składowej został zmodyfikowany.

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM — Opis makra

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

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości.

*memberGet*<br/>
Nazwa funkcji składowej, używany do pobrania właściwości.

*zestaw elementów członkowskich*<br/>
Nazwa używana do ustawiania właściwości funkcji elementu członkowskiego.

*vtPropType*<br/>
Wartość, określając typ właściwości.

*vtsParams*<br/>
Ciąg miejsca rozdzielone VTS_ dla każdego parametru.

### <a name="remarks"></a>Uwagi

Podobnie jak DISP_PROPERTY_EX — makro, to makro definiuje właściwość uzyskuje się z oddzielnych funkcji elementów członkowskich Get i Set. To makro, jednak pozwala określić listę parametrów dla właściwości. Jest to przydatne w przypadku implementowania właściwości, które są indeksowane lub sparametryzowane w inny sposób. Parametry będą zawsze umieszczać najpierw następuje nową wartość dla właściwości. Na przykład:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

odpowiada pobieranie i ustawianie elementów członkowskich:

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID — Opisy makra

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

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości.

*identyfikator DISPID*<br/>
Naprawiono DISPID dla właściwości lub metody.

*pfnGet*<br/>
Nazwa funkcji składowej, używany do pobrania właściwości.

*pfnSet*<br/>
Nazwa używana do ustawiania właściwości funkcji elementu członkowskiego.

*memberName*<br/>
Nazwa zmiennej składowej do mapowania właściwości

*vtPropType*<br/>
Wartość, określając typ właściwości.

*vtsParams*<br/>
Ciąg miejsca rozdzielone VTS_ dla każdego parametru.

### <a name="remarks"></a>Uwagi

Te makra pozwala użytkownikowi na określenie **DISPID** samodzielny MFC automatycznie przypisać jedną. Te zaawansowane makra o tych samych nazwach z wyjątkiem ten identyfikator jest dołączany do nazwy makra (np. **DISP_PROPERTY_ID**) i identyfikator jest określany przez podany parametr tuż za *pszName* parametru. Zobacz AFXDISP. Godz. Aby uzyskać więcej informacji na temat tych makr. **_Identyfikator** wpisy muszą być umieszczone na końcu Mapa wysyłania. Wpływają one na automatyczne **DISPID** Generowanie w taki sam sposób jak innej niż **_identyfikator** będzie wersja makra ( **DISPID**s są określane według pozycji). Na przykład:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC generuje DISPID dla klasy CDisp3DPoint w następujący sposób:

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

Określanie stałym **DISPID** przydaje się do zachowania zgodności z poprzednimi wersjami istniejących interfejs ekspedycji, aby zaimplementować niektórych właściwości lub metody zdefiniowane przez system (zazwyczaj wskazywany przez ujemnych  **Identyfikator DISPID**, takich jak **DISPID_NEWENUM** kolekcji).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Pobieranie interfejsu IDispatch dla COleClientItem

Wiele serwerów będzie obsługiwać usługi automation w ramach ich obiektów dokumentu, oraz funkcje serwera OLE. Aby uzyskać dostęp do tego interfejsu automatyzacji, należy go bezpośredni dostęp `COleClientItem::m_lpObject` zmiennej składowej. Poniższy kod powoduje pobranie `IDispatch` interfejsu pochodną obiektu `COleClientItem`. Może zawierać poniższy kod w aplikacji, jeśli okaże się tej funkcji konieczne:

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

Interfejs ekspedycji zwracane z tej funkcji można następnie używane bezpośrednio lub dołączone do `COleDispatchDriver` uzyskać bezpieczny dostęp. Jeśli używasz go bezpośrednio, upewnij się, należy wywołać jej `Release` elementu członkowskiego kiedy za pomocą wskaźnika na tłumaczeniu ( `COleDispatchDriver` destruktor nie).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
