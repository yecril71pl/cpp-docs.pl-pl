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
ms.openlocfilehash: 6a1d5c2d7bb2da2ba293ac29a59948f80c1bed59
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680613"
---
# <a name="cmfccolordialog-class"></a>Klasa CMFCColorDialog
`CMFCColorDialog` Klasa przedstawia okno dialogowe wyboru kolorów.  
  
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
|[CMFCColorDialog::GetPalette](#getpalette)|Zwraca wartość palety kolorów.|  
|`CMFCColorDialog::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. Informacje o składni i więcej informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Palety jest pochodną paleta systemu.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Ustawia bieżący kolor wybrany.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Ustawia kolor najbardziej odpowiednikiem określonej wartości RGB.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Wybiera wartość RGB dla pierwszej strony właściwości.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Wybiera wartość RGB na drugiej stronie właściwości.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`m_bIsMyPalette`|Wartość TRUE, jeśli okno dialogowe wyboru kolorów używa własnego paletę kolorów, lub FAŁSZ, jeśli okno dialogowe korzysta z palety, który jest określony w `CMFCColorDialog` konstruktora.|  
|`m_bPickerMode`|Wartość TRUE, gdy użytkownik jest wybór koloru z okna dialogowego wyboru; w przeciwnym razie wartość FALSE.|  
|`m_btnColorSelect`|Przycisk koloru, który został wybrany przez użytkownika.|  
|`m_CurrentColor`|Obecnie wybrany kolor.|  
|`m_hcurPicker`|Można wybrać kolor kursora.|  
|`m_NewColor`|Potencjalny wybranego koloru, który może być trwale wybrane lub cofnąć do oryginalnego koloru.|  
|`m_pColourSheetOne`|Wskaźnik do pierwszej strony właściwości arkusza właściwości wyboru kolorów.|  
|`m_pColourSheetTwo`|Wskaźnik do drugiej strony właściwości arkusza właściwości wyboru kolorów.|  
|`m_pPalette`|Bieżący palety logiczne.|  
|`m_pPropSheet`|Wskaźnik do arkusza właściwości dla okna dialogowego wyboru kolorów.|  
|`m_wndColors`|Obiekt formantu selektora kolorów.|  
|`m_wndStaticPlaceHolder`|Formant statyczny jest symbolem zastępczym dla arkusza właściwości próbnika kolorów.|  
  
## <a name="remarks"></a>Uwagi  
 Okno dialogowe wyboru kolorów jest wyświetlana jako arkusz właściwości, za pomocą dwóch stron. Na pierwszej stronie wybierz kolor standardowy z palety systemu; na drugiej stronie wybierz kolor niestandardowy.  
  
 Można skonstruować `CMFCColorDialog` obiektów na stosie, a następnie wywołać `DoModal`, przekazując kolor początkowy jako parametr do `CMFCColorDialog` konstruktora. Okno dialogowe wyboru kolorów następnie tworzy kilka [klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) obiekty do obsługi każdego palety kolorów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować okna dialogowego kolorów przy użyciu różnych metod w `CMFCColorDialog` klasy. W przykładzie pokazano, jak ustawić bieżącą i nowe kolory okna dialogowego i sposobu ustawiania składników czerwonego, zielonego i niebieskiego wybrany kolor na stronach właściwości dwa okna dialogowego kolorów. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
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
 Domyślny wybór kolorów. Jeśli nie określono wartości, wartość domyślna to RGB(0,0,0) (czarny).  
  
 [in] *Flagidw*  
 (Zastrzeżone).  
  
 [in] *pParentWnd*  
 Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe.  
  
 [in] *hPal*  
 Dojście do palety kolorów.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolor"></a>  CMFCColorDialog::GetColor  
 Pobiera kolor, który użytkownik wybiera z okna dialogowego kolorów.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](/windows/desktop/gdi/colorref) wartość, która zawiera informacje o RGB na kolor wybrany w oknie dialogowym koloru.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, po wywołaniu metody `DoModal` metody.  
  
##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette  
 Pobiera paletę kolorów, które są dostępne w bieżącym oknie dialogowym koloru.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPalette` obiektu, który został określony w `CMFCColorDialog` konstruktora.  
  
### <a name="remarks"></a>Uwagi  
 Paletę kolorów, która określa kolory, które użytkownik może wybrać.  
  
##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette  
 Palety jest pochodną paleta systemu.  
  
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
 Ustawia bieżący kolor na kolor w bieżącej palecie, który jest najbardziej podobny.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *rgb*  
 A [COLORREF](/windows/desktop/gdi/colorref) , który określa kolor RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne  
 Jawnie określa składników czerwonego, zielonego i niebieskiego wybrany kolor na pierwszej stronie właściwości okna dialogowego kolorów.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *R*  
 Określa składnik czerwony wartości RGB.  
  
 [in] *G*  
 Określa składnik zielony wartości RGB.  
  
 [in] *B*  
 Określa składnik niebieski wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo  
 Jawnie określa składników czerwonego, zielonego i niebieskiego wybrany kolor na drugiej stronie właściwości okna dialogowego kolorów.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *R*  
 Określa składnik czerwony wartości RGB  
  
 [in] *G*  
 Określa składnik zielony wartości RGB  
  
 [in] *B*  
 Określa składnik niebieski wartości RGB  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
