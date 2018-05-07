---
title: Klasa CMFCRibbonStatusBarPane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df9109ef4613a2fb905fc5bef525f3553155417b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonstatusbarpane-class"></a>Klasa CMFCRibbonStatusBarPane
`CMFCRibbonStatusBarPane` Klasa implementuje element wstążki, które można dodać do wstążki paska stanu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Tworzy i inicjuje `CMFCRibbonStatusBarPane` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Zwraca ciąg, który definiuje najdłuższy ciąg tekstowy, które mogą być wyświetlane w okienku bez obcięcie.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Zwraca bieżące ustawienie wyrównania tekstu.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Określa, czy animacja jest w toku.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Określa, czy okienku znajduje się w obszarze rozszerzonej paska stanu wstążki.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Przesłania [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Przesłania [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definiuje najdłuższy ciąg tekstowy, które mogą być wyświetlane w okienku bez obcięcie.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Przypisuje do okienka listy obrazów, który może służyć do animacji.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Określa wyrównanie tekstu.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Powoduje uruchomienie animacji, który jest przypisany do okienka.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Zatrzymuje animacji, który jest przypisany do okienka. .|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Wywoływane przez platformę, gdy przestanie animacji, który jest przypisany do okienka.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCRibbonStatusBarPane` klasy. W przykładzie przedstawiono sposób tworzenia `CMFCRibbonStatusBarPane` obiektów, wyrównania tekstu etykiety w okienku paska stanu, zdefiniuj najdłuższym tekst, który można wyświetlić w okienku paska stanu bez obcinania, Dołącz do okienku paska stanu listy obrazów, który może służyć do każ i rozpoczęcia animacji.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Skonstruować obiektu okienko na pasku stanu.  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nCmdID`  
 Określa identyfikator polecenia okienka.  
  
 [in] `lpszText`  
 Określa ciąg tekstowy, który będzie wyświetlany w okienku.  
  
 [in] `bIsStatic`  
 Jeśli `TRUE`, w okienku stanu nie może być wyróżniony ani przez kliknięcie przycisku go.  
  
 [in] `hIcon`  
 Określa dojścia do ikony mają być wyświetlane w okienku.  
  
 [in] `lpszAlmostLargeText`  
 Określa najdłuższy ciąg tekstowy, który może być wyświetlany w okienku.  
  
 [in] `hBmpAnimationList`  
 Określa dojścia do listy obrazów, który jest używany dla animacji.  
  
 [in] `cxAnimation`  
 Określa szerokość w pikselach, ikony w listy obrazów, który jest używany dla animacji.  
  
 [in] `clrTrnsp`  
 Określa kolor przezroczysty obrazów z listy obrazów, które są używane do animacji.  
  
 [in] `uiAnimationListResID`  
 Określa identyfikator zasobu, listy obrazów, który jest używany dla animacji.  
  
##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Pobiera ciąg tekstowy najdłuższym wyświetlanych w okienku paska stanu.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Najdłuższy ciąg tekstowy, wyświetlanych w okienku paska stanu.  
  
##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign  
 Pobiera bieżące ustawienie wyrównania tekstu etykiety w okienku paska stanu.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący wyrównanie tekstu, który może być jedną z następujących:  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation  
 Określa, czy animacja jest w toku.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli animacji jest w toku; `FALSE` inaczej.  
  
##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended  
 Określ, czy okienku znajduje się w obszarze rozszerzonej paska stanu wstążki.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli okienko znajduje się na pasku rozszerzonej obszaru stanu. `FALSE` w przeciwnym razie wartość.  
  
##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `CDC*`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation  
 Struktura wywołuje tę metodę po zakończeniu animacji, który jest przypisany do okienka.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Uwagi  
 `StopAnimation` wywołania metody `OnFinishAnimation` metodę, która służy do oczyszczania danych po zakończeniu animacji.  
  
##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Zdefiniuj najdłuższym tekst, który można wyświetlić w okienku paska stanu bez obcięcie.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszAlmostLargeText`  
 Określa ciąg najdłuższym mogą być wyświetlane w okienku paska stanu bez obcinania.  
  
### <a name="remarks"></a>Uwagi  
 Biblioteka oblicza rozmiar tekstu, który `lpszAlmostLargeText` określa i powoduje zmianę rozmiaru okienka. Jeśli nadal nie mieści się w okienku, tekst zostanie obcięta.  
  
##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList  
 Dołącza do okienku paska stanu listy obrazów, który może służyć do animacji.  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `hBmpAnimationList`  
 Określa dojścia do listy obrazów.  
  
 [in] `cxAnimation`  
 Określa szerokość w pikselach ramkę z listy obrazów.  
  
 [in] `clrTransp`  
 Określa kolor przezroczysty listy obrazów.  
  
 [in] `uiAnimationListResID`  
 Określa identyfikator zasobu listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli pomyślnie dołączono listy obrazów okienku paska stanu. `FALSE` inaczej.  
  
##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign  
 Określa wyrównanie tekstu etykiety w okienku paska stanu.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nAlign`  
 Określa wyrównanie tekstu.  
  
### <a name="remarks"></a>Uwagi  
 `nAlign` Może mieć jeden z następujących wartości:  
  
- `TA_LEFT`: wyrównanie do lewej  
  
- `TA_CENTER:` Wyśrodkuj  
  
- `TA_RIGHT:` Wyrównanie do prawej  
  
##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation  
 Uruchamia animacji, który można przypisać do okienka.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nFrameDelay`  
 Określa szybkość animacji, w milisekundach.  
  
 [in] `nDuration`  
 Określa, jak długo ma być odtworzony animacji, w milisekundach. Użyj wartości -1 dla pętli nieskończonej.  
  
### <a name="remarks"></a>Uwagi  
 Należy określić dojścia do listy obrazów przed wywołaniem `StartAnimation` przy użyciu `SetAnimationList`.  
  
##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation  
 Zatrzymuje animacji przypisana do okienku paska stanu.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Klasa CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)
