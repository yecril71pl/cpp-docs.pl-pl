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
ms.openlocfilehash: 55ef22eec84b4d7e5e4ea27abe611cf2d18f2a1b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465345"
---
# <a name="cmfcribbonstatusbarpane-class"></a>Klasa CMFCRibbonStatusBarPane
`CMFCRibbonStatusBarPane` Klasa implementuje element wstążki, który można dodać do paska stanu wstążki.  
  
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
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Zwraca ciąg, który definiuje najdłuższy ciąg tekstowy, który można wyświetlić w okienku bez obcinania.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Zwraca bieżące ustawienie wyrównania tekstu.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Określa, czy animacja jest w toku.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Określa, czy okienka znajduje się w obszarze rozszerzonego paska stanu wstążki.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Przesłania [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Przesłania [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definiuje najdłuższy ciąg tekstowy, który można wyświetlić w okienku bez obcinania.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Przypisuje do okienka listy obrazów, który może służyć do animacji.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Określa wyrównanie tekstu.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Powoduje uruchomienie animacji, która jest przypisana do okienka.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Zatrzymuje animacji, która jest przypisana do okienka. .|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Wywoływane przez platformę, gdy przestanie animacji, która jest przypisana do okienka.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonStatusBarPane` klasy. W przykładzie pokazano sposób tworzenia `CMFCRibbonStatusBarPane` obiektu, ustawianie wyrównania tekstu etykiety okienka paska stanu, definiowanie najdłuższy tekstu, które mogą być wyświetlane w okienku paska stanu bez obcinania, Dołącz do okienka paska stanu listy obrazów, który może służyć do każ i rozpoczęcia animacji.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Skonstruuj obiekt w okienku paska stanu.  
  
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
 [in] *nCmdID*  
 Określa identyfikator polecenia okienka.  
  
 [in] *lpszText*  
 Określa ciąg tekstowy, który będzie wyświetlany w okienku.  
  
 [in] *bIsStatic*  
 W przypadku opcji TRUE w okienku stanu nie wyróżnione lub wybrane, klikając go.  
  
 [in] *hIcon*  
 Określa dojścia do ikony, który będzie wyświetlany w okienku.  
  
 [in] *lpszAlmostLargeText*  
 Określa najdłuższy ciąg tekstowy, który można wyświetlić w okienku.  
  
 [in] *hBmpAnimationList*  
 Określa dojścia do listy obrazów, który jest używany podczas tworzenia animacji.  
  
 [in] *cxAnimation*  
 Określa szerokość w pikselach, ikony na liście obrazu, który jest używany podczas tworzenia animacji.  
  
 [in] *clrTrnsp*  
 Określa przezroczysty kolor obrazów z listy obrazów, które są używane podczas tworzenia animacji.  
  
 [in] *uiAnimationListResID*  
 Określa identyfikator zasobu, listy obrazów, który jest używany podczas tworzenia animacji.  
  
##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Pobiera najdłuższy ciąg tekstowy, który można wyświetlić w okienku paska stanu.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Najdłuższy ciąg tekstowy, który można wyświetlić w okienku paska stanu.  
  
##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign  
 Pobiera bieżące ustawienie wyrównania tekstu etykiety okienka paska stanu.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący wyrównanie tekstu, który może być jednym z następujących czynności:  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation  
 Określa, czy animacja jest w toku.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli animacji jest w toku; Wartość FALSE w przeciwnym razie.  
  
##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended  
 Ustal, czy okienka znajduje się w obszarze rozszerzonego paska stanu wstążki.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli okienko znajduje się w stanie rozszerzonej powierzchni paska. Wartość FALSE w przeciwnym razie.  
  
##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder  
 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Przechwytywania zmian danych**  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground  
 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation  
 Platforma wywołuje tę metodę, po zakończeniu animacji, która jest przypisana do okienka.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Uwagi  
 `StopAnimation` metoda wywołuje metodę `OnFinishAnimation` metody, która służy do czyszczenia danych, po zakończeniu animacji.  
  
##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Definiowanie najdłuższy tekstu, które mogą być wyświetlane w okienku paska stanu bez obcinania.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszAlmostLargeText*  
 Określa najdłuższy parametry, z których mogą być wyświetlane w okienku paska stanu bez obcinania.  
  
### <a name="remarks"></a>Uwagi  
 Biblioteka oblicza rozmiar tekstu, *lpszAlmostLargeText* określa i w związku z tym zmienia rozmiar okienka. Jeśli nadal nie mieszczą się w okienku, tekst zostanie obcięta.  
  
##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList  
 Dołącza do okienka paska stanu listy obrazów, który może służyć do animacji.  
  
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
 [in] *hBmpAnimationList*  
 Określa dojścia do listy obrazów.  
  
 [in] *cxAnimation*  
 Określa szerokość w pikselach, ramkę z listy obrazów.  
  
 [in] *clrTransp*  
 Określa przezroczysty kolor listy obrazów.  
  
 [in] *uiAnimationListResID*  
 Określa identyfikator zasobu listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli dołączone do okienka paska stanu; listy obrazów Wartość FALSE w przeciwnym razie.  
  
##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign  
 Określa wyrównanie tekstu w etykiecie w okienku paska stanu.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nAlign*  
 Określa wyrównanie tekstu.  
  
### <a name="remarks"></a>Uwagi  
 *nAlign* może mieć jedną z następujących wartości:  
  
- TA_LEFT: wyrównanie do lewej  
  
- TA_CENTER: wyrównanie do środka  
  
- TA_RIGHT: wyrównanie do prawej  
  
##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation  
 Uruchamia animacji, które można przypisać do okienka.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFrameDelay*  
 Określa szybkość odtwarzania animacji, w milisekundach.  
  
 [in] *nDuration*  
 Określa, jak długo można odtwarzać animację, w milisekundach. Użyj wartości -1 dla wejścia w nieskończoną pętlę.  
  
### <a name="remarks"></a>Uwagi  
 Należy określić dojście do listy obrazów przed wywołaniem `StartAnimation` przy użyciu `SetAnimationList`.  
  
##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation  
 Zatrzymuje animacji, która została przypisana do okienka paska stanu.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Klasa CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)
