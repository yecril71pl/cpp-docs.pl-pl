---
title: Klasa CMFCColorDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b2b3c2ff247014a692a78084f42c208b4497023
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040236"
---
# <a name="cmfccolordialog-class"></a>Klasa CMFCColorDialog
`CMFCColorDialog` Klasa reprezentuje okno dialogowe wybór kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Konstruuje `CMFCColorDialog` obiektu.|  
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|Zwraca bieżący kolor wybrany.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Zwraca paletę kolorów.|  
|`CMFCColorDialog::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. Składnia i uzyskać więcej informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Palety jest pochodną palety systemu.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Ustawia bieżący kolor wybrany.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Ustawia kolor najbardziej odpowiednikiem określonej wartości RGB.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Wybiera wartości RGB dla pierwszej strony właściwości.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Wybiera wartości RGB dla drugiej strony właściwości.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE` Jeśli okno dialogowe Wybieranie koloru używa własnego paletę kolorów lub `FALSE` czy okno dialogowe używa palety, który jest określony w `CMFCColorDialog` konstruktora.|  
|`m_bPickerMode`|`TRUE` gdy użytkownik wybiera kolor z okna dialogowego wyboru; w przeciwnym razie `FALSE`.|  
|`m_btnColorSelect`|Przycisk koloru, który został wybrany przez użytkownika.|  
|`m_CurrentColor`|Obecnie wybranego koloru.|  
|`m_hcurPicker`|Służy do pobierania kolor kursora.|  
|`m_NewColor`|Potencjalny wybranego koloru, które mogą zostać trwale wybrane lub przywrócona do oryginalnego koloru.|  
|`m_pColourSheetOne`|Wskaźnik do pierwszej strony właściwości arkusza właściwości Kolor zaznaczenia.|  
|`m_pColourSheetTwo`|Wskaźnik do drugiej strony właściwości arkusza właściwości Kolor zaznaczenia.|  
|`m_pPalette`|Bieżący logiczną paletę.|  
|`m_pPropSheet`|Wskaźnik do arkusza właściwości dla okna dialogowego wyboru koloru.|  
|`m_wndColors`|Obiekt formantu selektora kolorów.|  
|`m_wndStaticPlaceHolder`|Statyczne formant, który zostanie wypełniony arkusz właściwości próbnika kolorów.|  
  
## <a name="remarks"></a>Uwagi  
 Okno dialogowe wybór kolorów jest wyświetlana jako arkusz właściwości z dwoma stronami. Na pierwszej stronie wybierz kolor standardowy z palety systemu; na drugiej stronie wybierz niestandardowego koloru.  
  
 Można utworzyć `CMFCColorDialog` obiektów na stosie, a następnie wywołać `DoModal`, przekazując kolor początkowy jako parametr `CMFCColorDialog` konstruktora. Okno dialogowe Wybieranie koloru utworzy kilka [klasy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) obiekty do obsługi każdego paletę kolorów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skonfigurować przy użyciu różnych metod w oknie dialogowym koloru `CMFCColorDialog` klasy. W przykładzie pokazano, jak ustawić bieżący i kolory nowego okna dialogowego i sposobu ustawiania czerwony, zielonemu i niebieskiemu składników wybranego koloru na stronach właściwości dwa okna dialogowego kolorów. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog  
 Konstruuje `CMFCColorDialog` obiektu.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrInit*  
 Domyślny wybór kolorów. Jeśli wartość nie zostanie określona, wartością domyślną jest RGB(0,0,0) (czarny).  
  
 [in] *wartość elementu dwFlags*  
 (Zastrzeżone).  
  
 [in] *pParentWnd*  
 Wskaźnik do okna nadrzędnego lub właściciela okna dialogowego.  
  
 [in] *hPal*  
 Dojście do paletę kolorów.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolor"></a>  CMFCColorDialog::GetColor  
 Pobiera kolor, który użytkownik wybiera z okna dialogowego kolorów.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, która zawiera dane RGB kolor wybrany w oknie dialogowym koloru.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po wywołaniu metody `DoModal` metody.  
  
##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette  
 Pobiera paletę kolorów, które są dostępne w bieżącym oknie dialogowym koloru.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPalette` obiekt, który został określony w `CMFCColorDialog` konstruktora.  
  
### <a name="remarks"></a>Uwagi  
 Określa paletę kolorów, kolorów, które użytkownik może wybrać.  
  
##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette  
 Palety jest pochodną palety systemu.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor  
 Ustawia bieżący kolor okna dialogowego.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *rgb*  
 Wartości kolorów RGB  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor  
 Ustawia bieżący kolor na kolor w palecie bieżącego najbardziej podobne.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *rgb*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) , który określa kolor RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne  
 Jawnie określa składniki czerwony, zielonemu i niebieskiemu wybranego koloru na pierwszej stronie właściwości okna dialogowego kolorów.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *R*  
 Określa składnika czerwony wartości RGB.  
  
 [in] *G*  
 Określa składnika zielony wartości RGB.  
  
 [in] *B*  
 Określa składnika niebieski wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo  
 Jawnie określa składniki czerwony, zielonemu i niebieskiemu wybranego koloru na drugiej stronie właściwości okna dialogowego kolorów.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *R*  
 Określa składnik red wartości RGB  
  
 [in] *G*  
 Określa składnika zielony wartości RGB  
  
 [in] *B*  
 Określa składnika niebieski wartości RGB  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
