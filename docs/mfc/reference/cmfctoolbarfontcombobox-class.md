---
title: Klasa CMFCToolBarFontComboBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3826a1a649cf4a2c3f292b660e90384edac2575e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040093"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Klasa CMFCToolBarFontComboBox
Przycisku paska narzędzi, który zawiera kontrolki pola kombi, który umożliwia użytkownikowi wybranie czcionki z listy czcionek systemu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Konstruuje `CMFCToolBarFontComboBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Wybiera czcionkę w pole kombi czcionki, zgodnie z jedną nazwę czcionki lub prefiks i zestaw znaków czcionki.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 Wysokość znaków w polu kombi czcionki.  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać pole kombi czcionki przycisku paska narzędzi, wykonaj następujące kroki:  
  
1.  Zarezerwować Identyfikatora fikcyjnego zasobu dla przycisku w zasobie nadrzędnym paska narzędzi.  
  
2.  Utworzyć `CMFCToolBarFontComboBox` obiektu.  
  
3.  Programu obsługi wiadomości, który przetwarza komunikat AFX_WM_RESETTOOLBAR, Zastąp oryginalny przycisk Nowy przycisk pole kombi za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
4.  Synchronizuj czcionki, która jest wybrane w polu kombi czcionki w dokumencie przy użyciu [CMFCToolBarFontComboBox::SetFont](#setfont) metody.  
  
 Aby zsynchronizować czcionki dokumentu z Czcionka zaznaczona w polu kombi, użyj [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) metodę, aby pobrać atrybutów wybranej czcionki i użyj tych atrybutów, aby utworzyć [ Cfont — klasa](../../mfc/reference/cfont-class.md) obiektu.  
  
 Przycisk pole kombi czcionki wywołania funkcji Win32 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) ustalenie ekranu i drukarki czcionek dostępnych w systemie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
 Konstruuje [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) obiektu.  
  
```  
public:  
CMFCToolBarFontComboBox(
    UINT uiID,  
    int iImage,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    DWORD dwStyle = CBS_DROPDOWN,  
    int iWidth = 0,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);

 
protected:  
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,  
    int nFontType,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily);  
  
CMFCToolBarFontComboBox();
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiID*  
 Identyfikator polecenia pola kombi.  
  
 [in] *iImage*  
 Liczony od zera indeks obrazu paska narzędzi. Obraz znajduje się w [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiekt, który [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) obsługuje klasy.  
  
 [in] *nFontType*  
 Typów czcionek, które zawiera pola kombi. Ten parametr może mieć kombinację (wartość logiczna lub) z następujących wartości:  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in] *nCharSet*  
 Jeśli ustawiono DEFAULT_CHARSET, pole kombi zawiera wszystkie unikatowej nazwy czcionki w wszystkich zestawów znaków. (Jeśli istnieją dwie czcionki o takiej samej nazwie, pole kombi zawiera jeden z nich). Jeśli ustawionym na wartość zestawu prawidłowych znaków pole kombi zawiera tylko czcionki w określonego zestawu znaków. Zobacz [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) listę możliwych znak ustawia.  
  
 [in] *dwStyle*  
 Style pola kombi. (zobacz [style pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in] *iWidth*  
 Szerokość w pikselach kontrolki edycji.  
  
 [in] *nPitchAndFamily*  
 Jeśli ustawiono DEFAULT_PITCH, pole kombi zawiera czcionki, niezależnie od tego, wysokość. Jeśli ustawiono wartość FIXED_PITCH lub VARIABLE_PITCH, pole kombi zawiera tylko czcionki z danym typem wysokość. Filtrowanie oparte na rodziny czcionek nie jest obecnie obsługiwane.  
  
 [out] *pLstFontsExternal*  
 Wskaźnik do [klasy CObList](../../mfc/reference/coblist-class.md) obiekt zawierający informacje dostępne czcionki.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj `CMFCToolBarFontComboBox` obiektów przechowywania listy dostępnych czcionek w jednym udostępnionych `CObList` obiektu. Jeśli używasz drugi przeciążenia konstruktora i podaj prawidłowy wskaźnik do *pLstFontsExternal*, że `CMFCToolBarFontComboBox` obiektu zamiast spowoduje wypełnienie `CObList` który *pLstFontsExternal* Wskazuje z dostępnych czcionek.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCToolBarFontComboBox` obiektu. Następujący fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 Zwraca wskaźnik do `CMFCFontInfo` obiektu dla określonego indeksu w polu kombi.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIndex*  
 Określa liczony od zera indeks elementu pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CMFCFontInfo` obiektu. Jeśli *iIndex* nie określa indeks elementów prawidłową wartość zwracana jest `NULL`.  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 Określa wysokość w pikselach, znaków w polu kombi czcionki, jeśli pole kombi ma właściciela styl rysowania.  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `m_nFontHeight` zmienna ma wartość 0, wysokość jest obliczana automatycznie zgodnie z domyślną czcionkę pola kombi. Wysokość obejmuje zarówno wzrastająca część znaki powyżej linii bazowej i spadku znaków poniżej linii bazowej.  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 Wybiera czcionkę w pole kombi czcionki, zgodnie z nazwę czcionki i znak zestawu, które zostały określone w parametrach.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszName*  
 Określa nazwę czcionki lub prefiks.  
  
 [in] *nCharSet*  
 Określa zestaw znaków.  
  
 [in] *bExact*  
 Określa, czy *lpszName* zawiera nazwę czcionki lub prefiks czcionki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wybrano pomyślnie; Czcionka w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bExact* jest `TRUE`, ta metoda wybiera czcionkę, która dokładnie odpowiada nazwie określonej jako *lpszName*. Jeśli *bExact* jest `FALSE`, ta metoda wybiera czcionkę, która rozpoczyna się od tekstu określonego jako *lpszName* i który korzysta z zestawu znaków, który został określony jako *nCharSet*. Jeśli *nCharSet* ustawiono dla DEFAULT_CHARSET, zestaw znaków będzie ignorowana i to tylko *lpszName* zostanie użyta do wyboru czcionki.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



