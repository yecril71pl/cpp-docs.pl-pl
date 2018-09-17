---
title: Klasa CMFCFontComboBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0294a16c13941d74ccd3955f78e22e33ef8fc7a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725184"
---
# <a name="cmfcfontcombobox-class"></a>Klasa CMFCFontComboBox
`CMFCFontComboBox` Klasy tworzy formant pola kombi, która zawiera listę czcionek.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Konstruuje `CMFCFontComboBox` obiektu.|  
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|Metoda wywoływana przez platformę, aby określić względne położenie nowego elementu w polu posortowaną listę bieżącego formant pola kombi czcionki. (Przesłania [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|  
|`CMFCFontComboBox::DrawItem`|Metoda wywoływana przez platformę, by narysować określonego elementu w bieżącym formant pola kombi czcionki. (Przesłania [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|Pobiera informacje o aktualnie wybranej czcionki.|  
|`CMFCFontComboBox::MeasureItem`|Metoda wywoływana przez platformę, aby poinformować Windows wymiary pola listy w bieżącym formant pola kombi czcionki. (Przesłania [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|  
|`CMFCFontComboBox::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|Wybiera czcionkę, która odpowiada określonym kryteriom z pola kombi czcionki.|  
|[CMFCFontComboBox::Setup](#setup)|Inicjuje listy elementów w polu kombi czcionki.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Wskazuje Framework czcionki, która za pomocą rysowania etykiety elementów w bieżącym polu kombi czcionki.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CMFCFontComboBox` obiektów w oknie dialogowym, Dodaj `CMFCFontComboBox` zmienną klasy okno dialogowe. Następnie w `OnInitDialog` metody klasy okno dialogowe, wywołania [CMFCFontComboBox::Setup](#setup) metodę, aby zainicjować listy elementów w kontrolce pola kombi.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxfontcombobox.h  
  
##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox  
 Konstruuje `CMFCFontComboBox` obiektu.  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont  
 Pobiera informacje o aktualnie wybranej czcionki.  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) obiekt, który opisuje czcionki. Może być NULL, jeśli żadne czcionki jest zaznaczona w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont  
 Wskazuje Framework czcionki, która za pomocą rysowania etykiety elementów w bieżącym polu kombi czcionki.  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski należy ustawić na wartość TRUE, aby nakazać platformę, by Rysowanie każdej etykiety elementu za pomocą tej samej czcionki. Ustaw wartość FALSE, aby nakazać platformę, by narysować każdej etykiety elementu przy użyciu czcionki, którego nazwa jest taka sama jak etykiety tego elementu członkowskiego. Wartość domyślna tego elementu członkowskiego ma wartość FAŁSZ.  
  
##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont  
 Wybiera czcionkę, która odpowiada określonym kryteriom z pola kombi czcionki.  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>Parametry  
*pDesc*<br/>
[in] Wskazuje obiekt opisu czcionki.  
  
*lpszName*<br/>
[in] Określa nazwę czcionki.  
  
*nCharSet*<br/>
[in] Określa zestaw znaków. Wartość domyślna to DEFAULT_CHARSET. Aby uzyskać więcej informacji, zobacz `lfCharSet` członkiem [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli element w polu kombi czcionki pasuje do określonej czcionki opis obiektu lub nazwa czcionki i zestaw znaków; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wybieranie, a następnie przewiń listę do elementu w polu kombi czcionki, który odpowiada określonej czcionki.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia `SelectFont` method in Class metoda `CMFCFontComboBox` klasy. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>  CMFCFontComboBox::Setup  
 Inicjuje listy elementów w polu kombi czcionki.  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
*nFontType*<br/>
[in] Określa typ czcionki. Wartością domyślną jest bitową kombinacją (lub) DEVICE_FONTTYPE RASTER_FONTTYPE i TRUETYPE_FONTTYPE.  
  
*nCharSet*<br/>
[in] Określa zestaw znaków czcionek. Wartość domyślna to DEFAULT_CHARSET.  
  
*nPitchAndFamily*<br/>
[in] Określa czcionkę gęstość i rodzinę. Wartość domyślna to DEFAULT_PITCH.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pole kombi czcionki zostało zainicjowane pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje pole kombi czcionki Wyliczanie zainstalowanych czcionek, które zgodne z określonymi parametrami, a następnie wstawianie tych nazw czcionki w polu kombi czcionki.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia `Setup` method in Class metoda `CMFCFontComboBox` klasy. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)
