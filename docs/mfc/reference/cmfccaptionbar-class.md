---
title: Klasa CMFCCaptionBar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs: C++
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4449ebd1563fe02705913fd4f19e51d195b3d732
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfccaptionbar-class"></a>Klasa CMFCCaptionBar
A `CMFCCaptionBar` obiekt jest pasek sterowania, który może wyświetlać trzy elementy: przycisk etykietę tekstową i mapy bitowej. Umożliwia wyświetlanie tylko jeden element każdego typu naraz. Można wyrównać każdy element, do lewej lub prawej krawędzi formant lub do Centrum. Styl flat lub 3D można również dotyczą górne i dolne obramowania paska podpisu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|Tworzy kontrolkę paska podpisu i dołącza go do `CMFCCaptionBar` obiektu.|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Wskazuje, czy innego okienka można dynamicznie wstawiony między pasek tytułu i jego ramka nadrzędny. (Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|Włącza lub wyłącza przycisk na pasku podpisu.|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|Zwraca wyrównanie określonego elementu.|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania paska podpisu.|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Pobiera prostokąt ograniczający przycisku na pasku podpisu.|  
|[CMFCCaptionBar::GetMargin](#getmargin)|Zwraca odległość między krawędzią elementów paska podpisu i krawędzią formantu paska podpisu.|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Określa, czy pasek podpisu jest w trybie pasek komunikatów.|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Usuwa obraz mapy bitowej na pasku podpisu.|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|Usuwa przycisk na pasku podpisu.|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Usuwa ikonę na pasku podpisu.|  
|[CMFCCaptionBar::RemoveText](#removetext)|Usuwa tekst etykiety na pasku podpisu.|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej dla paska podpisu.|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Określa rozmiar obramowania paska podpisu.|  
|[CMFCCaptionBar::SetButton](#setbutton)|Ustawia przycisk paska podpisu.|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Określa, czy przycisk jest naciśnięty.|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Ustawia etykietkę narzędzia dla przycisku.|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Ustawia styl obramowania paska podpisu.|  
|[CMFCCaptionBar::SetIcon](#seticon)|Ustawia ikonę na pasku podpisu.|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Ustawia etykietkę narzędzia obrazu na pasku podpisu.|  
|[CMFCCaptionBar::SetMargin](#setmargin)|Ustawia odległość między krawędzią elementu pasek podpisu i krawędzią formantu paska podpisu.|  
|[CMFCCaptionBar::SetText](#settext)|Określa tekst etykiety na pasku podpisu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Wywoływane przez platformę, by wypełnienia tła paska podpisu.|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Wywoływane przez platformę, by narysować obramowanie pasek tytułu.|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Wywoływane przez platformę, by narysować przycisk paska podpisu.|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Wywoływane przez platformę, by narysować obraz paska podpisu.|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Wywoływane przez platformę, by narysować tekst paska podpisu.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Kolor tła paska podpisu.|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Kolor obramowania paska podpisu.|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Kolor tekstu pasek podpisu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć pasek podpisu, wykonaj następujące kroki:  
  
1.  Utworzyć `CMFCCaptionBar` obiektu. Zazwyczaj należy dodać pasek tytułu klasie ramki okna.  
  
2.  Wywołanie [CMFCCaptionBar::Create](#create) metody Tworzenie formantu paska podpisu i dołączenie go do `CMFCCaptionBar` obiektu.  
  
3.  Wywołanie [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), i [CMFCCaptionBar::SetBitmap](#setbitmap)można ustawić elementów paska podpisu.  
  
 Po ustawieniu button element należy przypisać do przycisku identyfikator polecenia. Kiedy użytkownik kliknie przycisk trasy pasek podpisu `WM_COMMAND` wiadomości, które mają ten identyfikator do nadrzędnego okna ramki.  
  
 Pasek tytułu może również działać w trybie pasek wiadomości, która emuluje pasek komunikatów, która jest wyświetlana w aplikacjach pakietu Office 2007. W trybie pasek komunikatów pasek tytułu Wyświetla mapę bitową, wiadomość i przycisk umożliwiający (zwykle powoduje otwarcie okna dialogowego.) Etykietka narzędzia można przypisać do mapy bitowej.  
  
 Aby włączyć tryb pasek komunikatów, należy wywołać [CMFCCaptionBar::Create](#create) i ustaw dla parametru czwarty (bIsMessageBarMode) `TRUE`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCCaptionBar` klasy. W przykładzie pokazano, jak tworzenie formantu paska podpisu, należy ustawić obramowanie 3D pasek tytułu, Ustaw odległość w pikselach między krawędzią podpis paska elementów i krawędzią formantu paska podpisu należy ustawić przycisk paska podpisu , ustawione etykietki narzędzia dla przycisku, etykieta tekstowa paska podpisu, Ustaw obraz mapy bitowej na pasku podpisu i ustawione etykietki narzędzia obrazu w pasek tytułu. Następujący fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcaptionbar.h  
  
##  <a name="create"></a>CMFCCaptionBar::Create  
 Tworzy kontrolkę paska podpisu i dołącza go do `CMFCCaptionBar` obiektu.  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Logiczna lub kombinacja Style paska podpisu.  
  
 `pParentWnd`  
 Okno nadrzędne kontrolki paska podpisu.  
  
 `uID`  
 Identyfikator formantu paska podpisu.  
  
 `nHeight`  
 Wysokość w pikselach formantu paska podpisu. Jeśli wartość -1, wysokość jest obliczane na podstawie wysokość ikony, tekst i przycisku, który wyświetla formantu paska podpisu.  
  
 `bIsMessageBarMode`  
 `TRUE`Jeśli pasek tytułu jest w trybie pasek komunikatów; `FALSE` inaczej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli podpis formantu paska został utworzony pomyślnie; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CMFCCaptionBar` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać `Create` metodę, która tworzy kontrolkę systemu Windows i dołącza go do `CMFCCaptionBar` obiektu.  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore  
 Wskazuje, czy innego okienka można dynamicznie wstawiony między pasek tytułu i jego ramka nadrzędny.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `FALSE` Jeśli zastąpiona.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enablebutton"></a>CMFCCaptionBar::EnableButton  
 Włącza lub wyłącza przycisk na pasku podpisu.  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć przycisk `FALSE` wyłączenie przycisku.  
  
##  <a name="getalignment"></a>CMFCCaptionBar::GetAlignment  
 Zwraca wyrównanie określonego elementu.  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`elem`  
 Element paska podpisu dla których mają zostać pobrane wyrównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyrównanie elementu, takiego jak przycisk, mapy bitowej, tekstu lub ikony.  
  
### <a name="remarks"></a>Uwagi  
 Wyrównanie elementu może być jedną z następujących wartości:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize  
 Zwraca rozmiar obramowania paska podpisu.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar w pikselach obramowania.  
  
##  <a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect  
 Pobiera prostokąt ograniczający przycisku na pasku podpisu.  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` obiekt, który zawiera współrzędne prostokątem przycisku na pasku podpisu.  
  
##  <a name="getmargin"></a>CMFCCaptionBar::GetMargin  
 Zwraca odległość między krawędzią elementów paska podpisu i krawędzią formantu paska podpisu.  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odległość w pikselach między krawędzią elementów paska podpisu i krawędzią formantu paska podpisu.  
  
##  <a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode  
 Określa, czy pasek podpisu jest w trybie pasek komunikatów.  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pasek tytułu jest w trybie pasek komunikatów; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 W trybie pasek komunikatów pasek tytułu Wyświetla obraz z etykietka narzędzia, tekst komunikatu i przycisk.  
  
##  <a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground  
 Kolor tła paska podpisu.  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder  
 Kolor obramowania paska podpisu.  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText  
 Kolor tekstu pasek podpisu.  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground  
 Wywoływane przez platformę, by wypełnienia tła paska podpisu.  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia paska podpisu.  
  
 [in]`rect`  
 Prostokąt ograniczający do wypełnienia.  
  
### <a name="remarks"></a>Uwagi  
 `OnDrawBackground` Metoda jest wywoływana, gdy tło paska podpis ma być wypełnione. Domyślna implementacja wypełnienia tła przy użyciu [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) kolorów.  
  
 Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd paska podpisu.  
  
##  <a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder  
 Wywoływane przez platformę, by narysować obramowanie pasek tytułu.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia, która jest używana do wyświetlania obramowania.  
  
 [in]`rect`  
 Prostokąt ograniczający.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie obramowania mają płaski.  
  
 Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd obramowania paska podpisu.  
  
##  <a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton  
 Wywoływane przez platformę, by narysować przycisk paska podpisu.  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia, która jest używana do wyświetlania przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku.  
  
 [in]`strButton`  
 Etykieta tekstowa przycisku.  
  
 [in]`bEnabled`  
 `TRUE`Jeśli ten przycisk jest włączony; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd przycisku paska podpisu.  
  
##  <a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage  
 Wywoływane przez platformę, by narysować obraz paska podpisu.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia, która jest używana do wyświetlania obrazu.  
  
 [in]`rect`  
 Określa prostokątem obrazu.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd obrazu.  
  
##  <a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText  
 Wywoływane przez platformę, by narysować tekst paska podpisu.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia, która jest używana do wyświetlania przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający tekstu.  
  
 [in]`strText`  
 Ciąg tekstowy do wyświetlenia.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja Wyświetla tekst przy użyciu `CDC::DrawText` i [CMFCCaptionBar::m_clrBarText](#m_clrbartext) kolorów.  
  
 Należy przesłonić tę metodę w `CMFCCaptionBar` klasy do dostosowywania wyglądu tekstu na pasku podpisu.  
  
##  <a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap  
 Usuwa obraz mapy bitowej na pasku podpisu.  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>CMFCCaptionBar::RemoveButton  
 Usuwa przycisk na pasku podpisu.  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>Uwagi  
 Układ elementów paska podpisu są automatycznie korygowane.  
  
##  <a name="removeicon"></a>CMFCCaptionBar::RemoveIcon  
 Usuwa ikonę na pasku podpisu.  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>CMFCCaptionBar::RemoveText  
 Usuwa tekst etykiety na pasku podpisu.  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>CMFCCaptionBar::SetBitmap  
 Ustawia obraz mapy bitowej dla paska podpisu.  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hBitmap`  
 Dojście do mapy bitowej do ustawienia.  
  
 [in]`clrTransparent`  
 Wartości RGB, który określa przezroczysty kolor mapy bitowej.  
  
 [in]`bStretch`  
 Jeśli `TRUE`, mapy bitowej jest rozciągany tak, jeśli nie pasuje do ograniczenia prostokąt obrazu. W przeciwnym razie nie jest rozciągana mapy bitowej.  
  
 [in]`bmpAlignment`  
 Wyrównanie mapy bitowej.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby ustawić mapy bitowej na pasku podpisu.  
  
 Poprzednie mapy bitowej jest niszczony automatycznie. Jeśli pasek tytułu Wyświetla ikonę, ponieważ wywołana [CMFCCaptionBar::SetIcon](#seticon) metody mapy bitowej nie będą wyświetlane, chyba że usunąć ikonę wywołując [CMFCCaptionBar::RemoveIcon](#removeicon).  
  
 Mapy bitowej jest wyrównany określone przez `bmpAlignment` parametru.  Ten parametr może mieć jedną z następujących `BarElementAlignment` wartości:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize  
 Określa rozmiar obramowania paska podpisu.  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nSize`  
 Nowy rozmiar w pikselach obramowania paska podpisu.  
  
##  <a name="setbutton"></a>CMFCCaptionBar::SetButton  
 Ustawia przycisk paska podpisu.  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszLabel`  
 Przycisk polecenia etykiety.  
  
 `uiCmdUI`  
 Identyfikator przycisku polecenia.  
  
 `btnAlignmnet`  
 Wyrównanie przycisku.  
  
 `bHasDropDownArrow`  
 `TRUE`Jeśli przycisk wyświetla strzałkę listy rozwijanej, `FALSE` inaczej.  
  
##  <a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed  
 Określa, czy przycisk jest naciśnięty.  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bPresed`  
 `TRUE`Jeśli przycisk śledzi jego stan naciśnięcia `FALSE` inaczej.  
  
##  <a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip  
 Ustawia etykietkę narzędzia dla przycisku.  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszToolTip`  
 W etykiecie.  
  
 [in]`lpszDescription`  
 Opis elementu tooltip.  
  
##  <a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder  
 Ustawia styl obramowania paska podpisu.  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bFlat`  
 `TRUE`w przypadku płaskiej obramowania paska podpisu. `FALSE`Jeśli obramowanie 3D.  
  
##  <a name="seticon"></a>CMFCCaptionBar::SetIcon  
 Ustawia ikonę na pasku podpisu.  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hIcon`  
 Dojście do ikonę, aby ustawić.  
  
 [in]`iconAlignment`  
 Wyrównanie ikony.  
  
### <a name="remarks"></a>Uwagi  
 Paski podpis można wyświetlać ikony lub mapy bitowe. Zobacz [CMFCCaptionBar::SetBitmap](#setbitmap) Aby dowiedzieć się, jak wyświetlić mapy bitowej. Jeśli ustawisz zarówno ikony, jak i mapy bitowej jest zawsze wyświetlany ikony. Wywołanie [CMFCCaptionBar::RemoveIcon](#removeicon) Aby usunąć ikonę na pasku podpisu.  
  
 Ikona jest wyrównany zgodnie z `iconAlignment` parametru. Może być jedną z następujących `BarElementAlignment` wartości:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip  
 Ustawia etykietkę narzędzia dla obrazu na pasku podpisu.  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszToolTip`  
 Tekst etykietki narzędzia.  
  
 [in]`lpszDescription`  
 Opis elementu tooltip.  
  
##  <a name="setmargin"></a>CMFCCaptionBar::SetMargin  
 Ustawia odległość między krawędzią elementu pasek podpisu i krawędzią formantu paska podpisu.  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nMargin`  
 Odległość w pikselach między krawędzią elementów paska podpisu i krawędzią formantu paska podpisu.  
  
##  <a name="settext"></a>CMFCCaptionBar::SetText  
 Określa tekst etykiety na pasku podpisu.  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strText`  
 Ciąg tekstowy, aby ustawić.  
  
 [in]`textAlignment`  
 Wyrównanie tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Etykieta tekstowa jest wyrównany określone przez `textAlignment` parametru. Może być jedną z następujących `BarElementAlignment` wartości:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
