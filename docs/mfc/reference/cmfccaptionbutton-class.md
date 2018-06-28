---
title: Klasa CMFCCaptionButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df36f8a6af5d8ad7e2a96780e02f236e3225333d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040632"
---
# <a name="cmfccaptionbutton-class"></a>Klasa CMFCCaptionButton
`CMFCCaptionButton` Klasa implementuje przycisku, który jest wyświetlany na pasku podpisu okienko dokujące lub okno ramowe minimalnej. Zazwyczaj platformę tworzy podpis przyciski automatycznie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Tworzy obiekt CMFCCaptionButton.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|Zwraca polecenie reprezentowane przez naciśnięcie przycisku.|  
|[CMFCCaptionButton::GetIconID](#geticonid)|Zwraca identyfikator obrazu skojarzony z przyciskiem.|  
|[CMFCCaptionButton::GetRect](#getrect)|Zwraca prostokąt zajmowane przez naciśnięcie przycisku.|  
|[CMFCCaptionButton::GetSize](#getsize)|Zwraca szerokość i wysokość przycisku.|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Wskazuje, czy rozmiar mini ma ustawioną wartość wysokość paska tytułu.|  
|[CMFCCaptionButton::Move](#move)|Ustawia lokalizację rysowania przycisk i okna Pokaż stan.|  
|[CMFCCaptionButton::OnDraw](#ondraw)|Rysuje przycisk podpis.|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Określa rozmiar podręczny pasek tytułu.|  
  
## <a name="remarks"></a>Uwagi  
 Może pochodzić z klasy [klasy CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) i użyj metody chronionych `AddButton`, aby dodać przyciski podpis do okno ramowe mini.  
  
 CPaneFrameWnd.h definiuje identyfikatory poleceń dla dwóch typów podpis przyciski:  
  
- `AFX_CAPTION_BTN_PIN`, który zawiera przycisk pin podczas okienko dokujące obsługuje tryb autoukrywania.  
  
- `AFX_CAPTION_BTN_CLOSE`, które wyświetla **Zamknij** przycisku w okienku można zamknąć lub ukryte.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCCaptionButton` obiektu i ustaw rozmiar mini paska tytułu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton  
 Konstruuje `CMFCCaptionButton` obiektu.  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nHit*  
 Polecenie skojarzone z przyciskiem.  
  
 [in] *bLeftAlign*  
 Określa, czy przycisk jest wyrównany do lewej.  
  
 W poniższej tabeli przedstawiono możliwe wartości *nHit* parametru.  
  
|Wartość|Polecenie|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Przycisk Zamknij.|  
|`HTMINBUTTON`|Przycisk Minimalizuj.|  
|`HTMAXBUTTON`|Przycisk Maksymalizuj.|  
|`AFX_HTLEFTBUTTON`|Przycisk strzałki w lewo.|  
|`AFX_HTRIGHTBUTTON`|Przycisk strzałki w prawo.|  
|`AFX_HTMENU`|Klawisz strzałki menu.|  
|`HTNOWHERE`|Wartość domyślna; reprezentuje żadne polecenie.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie przyciski podpis nie są skojarzone z poleceniem.  
  
 Przyciski podpis są wyrównane albo prawej lub lewej krawędzi.  
  
##  <a name="gethit"></a>  CMFCCaptionButton::GetHit  
 Zwraca polecenie reprezentowane przez naciśnięcie przycisku.  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Polecenie reprezentowane przez naciśnięcie przycisku.  
  
 W poniższej tabeli przedstawiono możliwe wartości zwracane.  
  
|Wartość|Polecenie|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Przycisk Zamknij.|  
|`HTMINBUTTON`|Przycisk Minimalizuj.|  
|`HTMAXBUTTON`|Przycisk Maksymalizuj.|  
|`AFX_HTLEFTBUTTON`|Przycisk strzałki w lewo.|  
|`AFX_HTRIGHTBUTTON`|Przycisk strzałki w prawo.|  
|`AFX_HTMENU`|Klawisz strzałki menu.|  
|`HTNOWHERE`|Wartość domyślna; reprezentuje żadne polecenie.|  
  
##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID  
 Zwraca identyfikator obrazu skojarzony z przyciskiem.  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bHorz*  
 `TRUE` Strzałka w lewo lub w prawo obrazu identyfikatorów; `FALSE` dla obrazu identyfikatorów w górę lub Strzałka w dół.  
  
 [in] *bMaximized*  
 `TRUE` Identyfikator obrazu Maksymalizuj; `FALSE` dla Minimalizuj obrazu identyfikatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator obrazu.  
  
### <a name="remarks"></a>Uwagi  
 Parametry Określ obraz identyfikatory Minimalizuj lub zmaksymalizować przycisków podpis.  
  
##  <a name="getrect"></a>  CMFCCaptionButton::GetRect  
 Zwraca prostokąt zajmowane przez naciśnięcie przycisku.  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Prostokąt, który reprezentuje położenie przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie widzisz przycisku rozmiar zwracane jest 0.  
  
##  <a name="getsize"></a>  CMFCCaptionButton::GetSize  
 Zwraca szerokość i wysokość przycisku.  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zewnętrzne wymiary przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar zwrócił zawiera przycisk margines i obramowania.  
  
##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton  
 Wskazuje, czy rozmiar mini ma ustawioną wartość wysokość paska tytułu.  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli podpis ma ustawioną wartość rozmiaru mini; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="move"></a>  CMFCCaptionButton::Move  
 Ustawia lokalizację rysowania przycisk i okna Pokaż stan.  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *ptTo*  
 Nowa lokalizacja.  
  
 [in] *bHide*  
 Określa, czy wyświetlać przycisk.  
  
##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw  
 Rysuje przycisk podpis.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia dla przycisku.  
  
 [in] *bWykonywanie aktywnych*  
 Określa, czy do rysowania obrazu przycisku.  
  
 [in] *bHorz*  
 Zarezerwowane do użytku w klasie pochodnej.  
  
 [in] *bMaximized*  
 Określa, czy do rysowania obrazu przycisku zmaksymalizowane.  
  
 [in] *bWyłączone*  
 Określa, czy do rysowania obrazu przycisku włączone.  
  
### <a name="remarks"></a>Uwagi  
 *BMaximized* parametr jest używany, gdy przycisk jest Maksymalizuj lub przycisk Minimalizuj.  
  
##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton  
 Określa rozmiar podręczny pasek tytułu.  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bUstawienie*  
 `TRUE` Wysokość paska tytułu mini; `FALSE` dla domyślna wysokość paska tytułu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
