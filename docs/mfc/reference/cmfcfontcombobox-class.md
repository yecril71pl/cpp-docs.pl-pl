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
ms.openlocfilehash: 9141dec6fdcb966dcdb664bb8dc090b50a10a614
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040002"
---
# <a name="cmfcfontcombobox-class"></a>Klasa CMFCFontComboBox
`CMFCFontComboBox` Klasy tworzy kontrolki pola kombi, który zawiera listę czcionek.  
  
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
|`CMFCFontComboBox::CompareItem`|Wywoływane przez platformę, by określić względne położenie nowego elementu w polu posortowaną listę bieżącego formantu pole kombi czcionki. (Przesłania [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|  
|`CMFCFontComboBox::DrawItem`|Wywoływane przez platformę, by narysować określonego elementu w bieżącym kontrolki pola kombi czcionki. (Przesłania [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|Pobiera informacje o aktualnie wybranej czcionki.|  
|`CMFCFontComboBox::MeasureItem`|Wywoływane przez platformę, aby poinformować system Windows wymiarów pola listy w bieżącym kontrolki pola kombi czcionki. (Przesłania [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|  
|`CMFCFontComboBox::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|Wybiera czcionkę, która jest zgodny z określonymi kryteriami z pola kombi czcionki.|  
|[CMFCFontComboBox::Setup](#setup)|Inicjuje listę elementów w polu kombi czcionki.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Wskazuje platformę czcionki do rysowania etykiety elementów w polu kombi bieżącej czcionki.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CMFCFontComboBox` obiektów w oknie dialogowym, Dodaj `CMFCFontComboBox` zmienną do klasy okno dialogowe. Następnie w `OnInitDialog` metody klasy okno dialogowe, wywołanie [CMFCFontComboBox::Setup](#setup) metodę, aby zainicjować listę elementów w formancie pola kombi.  
  
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
 Wskaźnik do [klasy CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) obiektu, który opisuje czcionki. Można ją `NULL` Jeśli czcionki nie jest zaznaczona w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont  
 Wskazuje platformę czcionki do rysowania etykiety elementów w polu kombi bieżącej czcionki.  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ustaw ten element członkowski `TRUE` przekierować platformę, by używać tej samej czcionki do rysowania etykiety każdego elementu. Ustaw ten element członkowski `FALSE` przekierować platformę, by narysować każda etykieta elementu czcionki, którego nazwa jest taka sama jak etykiety. Wartość domyślna tego elementu członkowskiego to `FALSE`.  
  
##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont  
 Wybiera czcionkę, która jest zgodny z określonymi kryteriami z pola kombi czcionki.  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pDesc*  
 Wskazuje obiekt opis czcionki.  
  
 [in] *lpszName*  
 Określa nazwę czcionki.  
  
 [in] *nCharSet*  
 Określa zestaw znaków. Wartość domyślna to DEFAULT_CHARSET. Aby uzyskać więcej informacji, zobacz `lfCharSet` członkiem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli element w polu kombi czcionki jest zgodny z określonej czcionki opis obiektu lub nazwa czcionki i charset; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zaznaczyć, a następnie przewiń do pozycji pole kombi czcionki, który odpowiada określonej czcionki.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `SelectFont` metoda `CMFCFontComboBox` klasy. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>  CMFCFontComboBox::Setup  
 Inicjuje listę elementów w polu kombi czcionki.  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFontType*  
 Określa typ czcionki. Wartość domyślna to bitowe połączenie (lub) DEVICE_FONTTYPE, RASTER_FONTTYPE i TRUETYPE_FONTTYPE.  
  
 [in] *nCharSet*  
 Określa zestaw znaków czcionki. Wartość domyślna to DEFAULT_CHARSET.  
  
 [in] *nPitchAndFamily*  
 Określa czcionkę gęstość i rodzinę. Wartość domyślna to DEFAULT_PITCH.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli pole kombi czcionki został zainicjowany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje pola kombi czcionki Wyliczanie zainstalowanych czcionek, które zgodne z określonymi parametrami, a następnie wstawianie tych nazw czcionek w pole kombi czcionki.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `Setup` metoda `CMFCFontComboBox` klasy. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)
