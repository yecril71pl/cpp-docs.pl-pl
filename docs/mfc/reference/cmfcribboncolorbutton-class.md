---
title: Klasa CMFCRibbonColorButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8da5a7a05f1765fea840c579c91ddd9b3ef672b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncolorbutton-class"></a>Klasa CMFCRibbonColorButton
`CMFCRibbonColorButton` Klasa implementuje przycisk koloru, które można dodać do pasek wstążki. Przycisk koloru wstążki Wyświetla menu rozwijanego, który zawiera co najmniej jeden palety kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Dodaje grupę kolorów do obszaru regularne kolorów.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Określa, czy **automatyczne** przycisk jest aktywny.|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Umożliwia **innych** przycisku.|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|Zwraca aktualnie wybranego koloru.|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Zwraca rozmiar elementów kolorów, które są wyświetlane na pasku kolorów.|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Zwraca kolor aktualnie zaznaczonego elementu w menu podręczne paletę kolorów.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Usuwa wszystkie grupy kolorów z obszaru regularne kolorów.|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|Zaznaczy kolor w obszarze regularne kolorów.|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Ustawia rozmiar wszystkich elementów kolorów, które są wyświetlane na pasku kolorów.|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu.|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>Uwagi  
 Przycisk koloru wstążki Wyświetla pasek koloru po naciśnięciu klawisza go. Domyślnie ten pasek koloru zawiera paletę kolorów o nazwie obszar regularne koloru. Opcjonalnie można wyświetlić pasek koloru **automatyczne** przycisku, który pozwala użytkownikowi na wybranie domyślnego koloru, i **innych** przycisku, który wyświetla zawierający dodatkowe kolorów palety kolorów menu podręczne.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCRibbonColorButton` klasy. W przykładzie przedstawiono sposób tworzenia `CMFCRibbonColorButton` obiekt, ustaw duży obraz, Włącz **automatyczne** przycisku, Włącz **innych** przycisku, ustaw liczbę kolumn, ustaw rozmiar wszystkich elementów kolorów które są wyświetlane na pasku kolorów, Dodaj grupę kolorów do obszaru regularne kolorów i określ listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu. Następujący fragment kodu jest częścią [rysowania klienta — przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup  
 Dodaje grupę kolorów do obszaru regularne kolorów.  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszName`  
 Nazwa grupy.  
  
 [in]`lstColors`  
 Lista kolorów.  
  
 [in]`bContiguousColumns`  
 Określa, jak elementy kolorów są wyświetlane w grupie. Jeśli `TRUE`, kolor elementów są rysowane bez odstępy w pionie. Jeśli `FALSE`, kolor elementów są rysowane z odstępów w pionie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby kolor wyskakującego wyświetlić kilka grup kolorów. Można kontrolować sposób wyświetlania kolorów w grupie.  
  
##  <a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton  
 Konstruuje `CMFCRibbonColorButton` obiektu.  
  
```  
CMFCRibbonColorButton();

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    COLORREF color = RGB(0, 0, 0));

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    BOOL bSimpleButtonLook,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    COLORREF color = RGB(0, 0, 0));
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Określa identyfikator polecenia do wykonania, gdy użytkownik kliknie przycisk polecenia.  
  
 [in]`lpszText`  
 Określa tekst wyświetlany na przycisku.  
  
 [in]`nSmallImageIndex`  
 Liczony od zera indeks mały obraz wyświetlany na przycisku.  
  
 [in]`color`  
 Kolor przycisku (wartość domyślna to czarny).  
  
 [in]`bSimpleButtonLook`  
 Jeśli `TRUE`, przycisk jest rysowane jako prosty prostokąt.  
  
 [in]`nLargeImageIndex`  
 Liczony od zera indeks duży obraz wyświetlany na przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton  
 Określa, czy **automatyczne** przycisk jest aktywny.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE,  
    LPCTSTR lpszToolTip=NULL,  
    BOOL bOnTop=TRUE,  
    BOOL bDrawBorder=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Etykieta dla **automatyczne** przycisku.  
  
 [in]`colorAutomatic`  
 Wartości RGB, który określa **automatyczne** przycisku domyślny kolor.  
  
 [in]`bEnable`  
 `TRUE`Jeśli **automatyczne** przycisk jest włączony; `FALSE` Jeśli została ona wyłączona.  
  
 [in]`lpszToolTip`  
 Etykietka narzędzia **automatyczne** przycisku.  
  
 [in]`bOnTop`  
 Określa, czy **automatyczne** znajduje się przycisk u góry, przed paletę kolorów.  
  
 [in]`bDrawBorder`  
 `TRUE`Jeśli aplikacja rysuje obramowanie pasek koloru na Wstążce przycisk koloru. Pasek koloru Wyświetla wybrany kolor. `FALSE`Jeśli aplikacja nie narysować obramowanie  
  
##  <a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton  
 Umożliwia **innych** przycisku.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszLabel`  
 Etykieta przycisku.  
  
 `lpszToolTip`  
 Tekst etykietki narzędzia dla **innych** przycisku.  
  
### <a name="remarks"></a>Uwagi  
 **Innych** przycisk jest dostępny, wyświetlonego poniżej grupy kolorów. Po kliknięciu przez użytkownika **innych** przycisku on Wyświetla okno dialogowe kolorów.  
  
##  <a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor  
 Pobiera bieżący kolor przycisku automatycznego.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości kolorów RGB reprezentujący bieżący kolor przycisku automatycznego.  
  
### <a name="remarks"></a>Uwagi  
 Kolor przycisku automatycznego jest ustawiana przez `colorAutomatic` parametr przekazany do `CMFCRibbonColorButton::EnableAutomaticButton` metody.  
  
##  <a name="getcolor"></a>CMFCRibbonColorButton::GetColor  
 Zwraca aktualnie wybranego koloru.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor wybrany przez kliknięcie przycisku.  
  
##  <a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize  
 Zwraca rozmiar elementów kolorów, które są wyświetlane na pasku kolorów.  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar przycisków kolorów palety kolorów listy rozwijanej.  
  
##  <a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns  
 Pobiera liczbę elementów w wierszu wyświetlania galerii wstążki przycisk koloru.  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę ikon w każdym wierszu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor  
 Zwraca paletę kolorów wyskakującego Kolor obecnie wybranego elementu.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor aktualnie zaznaczonego elementu w wyskakującym paletę.  
  
##  <a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups  
 Usuwa wszystkie grupy kolorów z obszaru regularne kolorów.  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>CMFCRibbonColorButton::SetColor  
 Zaznaczy kolor w obszarze regularne kolorów.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Aby ustawić kolor.  
  
##  <a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize  
 Ustawia rozmiar wszystkich elementów kolorów, które są wyświetlane na pasku kolorów.  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`sizeBox`  
 Nowy rozmiar przycisków kolorów palety kolorów.  
  
##  <a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName  
 Ustawia nazwę określonego koloru.  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Wartości RGB koloru.  
  
 [in]`strName`  
 Nowa nazwa dla określonego koloru.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ wywołuje `CMFCColorBar::SetColorName`, ta metoda zmienia nazwę określonego koloru we wszystkich `CMFCColorBar` obiektów w aplikacji.  
  
##  <a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns  
 Ustawia liczbę kolumn wyświetlanych w tabeli kolorów, która jest wyświetlana podczas procesu wyboru koloru użytkownika.  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nColumns`  
 Liczba ikon koloru do wyświetlenia w każdym wierszu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors  
 Określa listę wartości RGB, aby wyświetlić w obszarze kolor dokumentu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Tekst wyświetlany kolory dokumentu.  
  
 [in]`lstColors`  
 Odwołanie do listy wartości RGB.  
  
##  <a name="setpalette"></a>CMFCRibbonColorButton::SetPalette  
 Określa standardowe kolory do wyświetlenia w tabeli kolorów wyświetlany przycisk koloru.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pPalette`  
 Wskaźnik do paletę kolorów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor  
 Wywoływane przez platformę, gdy użytkownik zaznaczy kolor w tabeli kolorów wyświetlany, gdy użytkownik kliknie przycisk koloru.  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Kolor wybrany przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCRibbonColorButton::UpdateColor` Metody zmienia kolor aktualnie wybrany przycisk i powiadamia jego elementu nadrzędnego, wysyłając `WM_COMMAND` komunikatów z `BN_CLICKED` powiadomień w wersji standard. Użyj [CMFCRibbonColorButton::GetColor](#getcolor) metoda pobierania wybranego koloru.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)
