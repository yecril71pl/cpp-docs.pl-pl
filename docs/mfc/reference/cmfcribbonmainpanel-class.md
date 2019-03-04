---
title: Klasa CMFCRibbonMainPanel
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: e4bd1ab8cffc87d5079518cf9a1d6e430ca40fd9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294459"
---
# <a name="cmfcribbonmainpanel-class"></a>Klasa CMFCRibbonMainPanel

Implementuje panel wstążki, który jest wyświetlany po kliknięciu [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Składnia

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Domyślny konstruktor.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|Dodaje element wstążki do okienka po lewej stronie panelu przycisku aplikacji. (Przesłania [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Dodaje ciąg tekstowy do ostatnich menu listy plików.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Dodaje element wstążki w dolnym okienku Panelu wstążki w aplikacji.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Dodaje element wstążki do prawego okienka panelu przycisku aplikacji.|
|`CMFCRibbonMainPanel::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Zwraca prostokąt, który reprezentuje obszar główny panel wstążki.|
|`CMFCRibbonMainPanel::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|

## <a name="remarks"></a>Uwagi

Wyświetla w ramach `CMFCRibbonMainPanel` po otwarciu panelu aplikacji. Zawiera on trzy sekcje:

- W okienku po lewej stronie zawiera polecenia związane z plikami, takie jak **Otwórz**, **Zapisz**, **drukowania**, i **Zamknij**. Aby dodać polecenie do to okienko, należy wywołać [CMFCRibbonMainPanel::Add](#add).

- W okienku po prawej stronie zawiera opcje, które modyfikują polecenie, które kliknij w okienku po lewej stronie. Na przykład jeśli klikniesz **Zapisz jako** z okienka po lewej stronie w okienku po prawej stronie można wyświetlić listę typów plików. Aby dodać element do to okienko, należy wywołać [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Dolne okienko zawiera przyciski, dzięki czemu można zmienić ustawienia aplikacji i zakończyć program. Aby dodać element do to okienko, należy wywołać [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

Dodaje element wstążki do okienka po lewej stronie panelu przycisku aplikacji.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[out w] Wskaźnik do elementu wstążki do dodania do panelu głównego.

### <a name="remarks"></a>Uwagi

Dodaje element wstążki do panelu. Elementy dodane przy użyciu tej metody będą znajdować się w lewej kolumnie główny panel.

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

Dodaje ciąg tekstowy do ostatnich menu listy plików.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
Określa ciąg do dodania do listy ostatnio używanych plików.

*nWidth*<br/>
Określa szerokość w pikselach, ostatnie panel listy plików.

### <a name="remarks"></a>Uwagi

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

Dodaje element wstążki w dolnym okienku Panelu wstążki w aplikacji.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[out w] Wskaźnik do elementu wstążki do dodania do dolnej części panelu głównego.

### <a name="remarks"></a>Uwagi

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

Dodaje element wstążki do prawego okienka panelu przycisku aplikacji.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
Wskaźnik do elementu wstążki do dodania do prawej strony głównej zespołu.

*nWidth*<br/>
Określa szerokość w pikselach, prawy panel.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia dodawanie elementu wstążki do prawym panelu. Prawy panel zwykle wyświetla listę ostatnio używanych plików, ale możesz dodać innego wstążki elementu w tym miejscu.

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

Zwraca prostokąt, który reprezentuje obszar główny panel wstążki.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

Prostokąt, który reprezentuje obszar główny panel wstążki.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
