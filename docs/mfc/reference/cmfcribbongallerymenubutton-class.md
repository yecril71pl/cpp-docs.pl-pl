---
title: Klasa CMFCRibbonGalleryMenuButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
ms.openlocfilehash: 0ec295fa64b835064435992a398d4292ccf26f38
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866167"
---
# <a name="cmfcribbongallerymenubutton-class"></a>Klasa CMFCRibbonGalleryMenuButton

Implementuje przycisk menu wstążki, który zawiera Galerie wstążki.
Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Konstruuje i inicjuje `CMFCRibbonGalleryMenuButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Przesłania [CMFCToolBarMenuButton:: CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom).)|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Przesłania [CMFCToolBarMenuButton:: CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|
|[CMFCRibbonGalleryMenuButton:: getpaleta](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Przesłania `CMFCToolBarMenuButton::HasButton`).|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Przesłania [CMFCToolBarMenuButton:: IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|

### <a name="remarks"></a>Uwagi

Przycisk menu Galeria jest wyświetlany jako menu podręczne z strzałką. Gdy użytkownik kliknie ten przycisk, zostanie wyświetlona Galeria obrazów. Gdy tworzysz przycisk menu galerii, musisz określić listę obrazów zawierającą te obrazy.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób wyświetlania galerii punktorów w przycisku menu:

```cpp
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)
{
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)
    {
        CMFCToolBarButton* pExButton =
        pMenuBar->GetButton(nBulletIndex);
        ASSERT_VALID (pExButton);

        CMFCRibbonGalleryMenuButton paletteBullet (
        pExButton->m_nID,
        pExButton->GetImage (),
        pExButton->m_strText);

        InitBulletPalette (&paletteBullet.GetPalette ());

        pMenuBar->ReplaceButton (ID_PARA_BULLETS,
        paletteBullet);
    }
}
```

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonPaletteGallery. h

##  <a name="copyfrom"></a>CMFCRibbonGalleryMenuButton::CopyFrom

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

podczas *src*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="cmfcribbongallerymenubutton"></a>CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton

Tworzy i inicjuje obiekt [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md) .

```
CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    CMFCToolBarImages& imagesPalette);

CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    UINT uiImagesPaletteResID = 0,
    int cxPaletteImage = 0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
Identyfikator polecenia przycisku. Jest to wartość wysyłana w komunikacie WM_COMMAND po kliknięciu tego przycisku przez użytkownika.

*iImage*<br/>
Indeks obrazu do wyświetlenia przy użyciu przycisku menu galerii. Obrazy są przechowywane w parametrze *imagesPalette* .

*lpszText*<br/>
Tekst, który ma być wyświetlany na przycisku menu.

*imagesPalette*<br/>
Zawiera listę obrazów do wyświetlenia w galerii.

*uiImagesPaletteResID*<br/>
Identyfikator zasobu listy obrazów do wyświetlenia w galerii.

*cxPaletteImage*<br/>
Określa szerokość (w pikselach) obrazu, który ma być wyświetlany w galerii.

### <a name="remarks"></a>Uwagi

Przycisk menu Galeria jest wyświetlany jako menu podręczne, które ma strzałkę. Gdy użytkownik kliknie ten przycisk, zostanie wyświetlona Galeria obrazów.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia konstruktora `CMFCRibbonGalleryMenuButton` klasy. Ten fragment kodu jest częścią [przykładu demonstracyjnego pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

##  <a name="createpopupmenu"></a>CMFCRibbonGalleryMenuButton::CreatePopupMenu

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpalette"></a>CMFCRibbonGalleryMenuButton:: getpaleta

```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="hasbutton"></a>CMFCRibbonGalleryMenuButton::HasButton

```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isemptymenuallowed"></a>CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)
