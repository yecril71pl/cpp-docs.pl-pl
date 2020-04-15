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
ms.openlocfilehash: 1458039c25f2379b3c3db553b2010e9391df28db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375106"
---
# <a name="cmfcribbonmainpanel-class"></a>Klasa CMFCRibbonMainPanel

Implementuje panel wstążki, który jest wyświetlany po kliknięciu [przycisku CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Składnia

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Domyślny konstruktor.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonMainPanel::Dodaj](#add)|Dodaje element wstążki do lewego okienka panelu przycisków aplikacji. (Zastępuje [CMFCRibbonPanel::Dodaj](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Dodaje ciąg tekstowy do menu listy ostatnich plików.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Dodaje element wstążki do dolnego okienka panelu aplikacji wstążki.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Dodaje element wstążki do prawego okienka panelu przycisków aplikacji.|
|`CMFCRibbonMainPanel::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Zwraca prostokąt reprezentujący obszar panelu głównego wstążki.|
|`CMFCRibbonMainPanel::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|

## <a name="remarks"></a>Uwagi

Struktura wyświetla `CMFCRibbonMainPanel` po otwarciu panelu aplikacji. Zawiera trzy okienka:

- Lewe okienko zawiera polecenia skojarzone z plikami, takie jak **Otwórz,** **Zapisz,** **Drukuj**i **Zamknij**. Aby dodać polecenie do tego okienka, zadzwoń do [CMFCRibbonMainPanel::Dodaj](#add).

- Prawe okienko zawiera opcje modyfikujące polecenie, które klikniesz w lewym okienku. Jeśli na przykład z lewego okienka zostanie kliknąć przycisk **Zapisz jako,** prawe okienko będzie wyświetlać dostępne typy plików. Aby dodać element do tego okienka, zadzwoń do [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Dolne okienko zawiera przyciski, które umożliwiają zmianę ustawień aplikacji i wyjście z programu. Aby dodać element do tego okienka, zadzwoń [do CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[PANEL CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Dodaj

Dodaje element wstążki do lewego okienka panelu przycisków aplikacji.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parametry

*pElem (właśc.*<br/>
[w, na zewnątrz] Wskaźnik do elementu wstążki, który ma być dodawany do panelu głównego.

### <a name="remarks"></a>Uwagi

Dodaje element wstążki do panelu. Elementy dodane przy użyciu tej metody będą znajdować się w lewej kolumnie panelu głównego.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList

Dodaje ciąg tekstowy do menu listy ostatnich plików.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
Określa ciąg, który ma być dodawany do listy ostatnich plików.

*nWidth (ww.*<br/>
Określa szerokość panelu listy ostatnich plików w pikselach.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom

Dodaje element wstążki do dolnego okienka panelu aplikacji wstążki.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parametry

*pElem (właśc.*<br/>
[w, na zewnątrz] Wskaźnik do elementu wstążki, aby dodać do dołu panelu głównego.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight

Dodaje element wstążki do prawego okienka panelu przycisków aplikacji.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*pElem (właśc.*<br/>
Wskaźnik do elementu wstążki, który ma zostać dodany po prawej stronie panelu głównego.

*nWidth (ww.*<br/>
Określa szerokość prawego panelu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do dodawania elementu wstążki do prawego panelu. Prawy panel zazwyczaj wyświetla listę ostatnich plików, ale w tym miejscu można dodać dowolny inny element wstążki.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame

Zwraca prostokąt reprezentujący obszar panelu głównego wstążki.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

Prostokąt reprezentujący obszar panelu głównego wstążki.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
