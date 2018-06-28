---
title: Klasa CMFCColorPickerCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3d4c8af6373f2b526c07ee570f4be878bd073d4
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042046"
---
# <a name="cmfccolorpickerctrl-class"></a>Klasa CMFCColorPickerCtrl
`CMFCColorPickerCtrl` Klasa udostępnia funkcje dla formantu, który jest używany do wybierania kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Konstruuje `CMFCColorPickerCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Pobiera kolor wybranego przez użytkownika.|  
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Pobiera wartości odcień, jasność i nasycenie koloru przez użytkownika.|  
|[CMFCColorPickerCtrl::GetHue](#gethue)|Pobiera składnik hue kolor wybranego przez użytkownika.|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Pobiera składnik jasności koloru przez użytkownika.|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Pobiera składnik nasycenie koloru przez użytkownika.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki kolorów RGB lub sześciokąt określona komórka.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Ustawia bieżący kolor do określonej wartości kolorów RGB.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Ustawia bieżący kolor na określoną wartość koloru HLS.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Zmienia składnika odcienia, który aktualnie wybranego koloru.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Zmienia składnika jasności aktualnie wybranego koloru.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Ustawia szerokość paska jasności w formancie selektora kolorów.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Ustawia kolor wybranego początkowej.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Ustawia bieżący paletę kolorów.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Zmienia składnika nasycenie aktualnie wybranego koloru.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Ustawia typ formantu selektora kolorów do wyświetlenia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Wywoływane przez platformę przed wyświetleniem kursora, który wskazuje wybranego koloru.|  
  
## <a name="remarks"></a>Uwagi  
 Wybrano standardowe kolory z palety kolorów (sześciokąt) i kolory niestandardowe są wybierane w pasku jasności kolorów są określone za pomocą notacji czerwony/zielony/niebieski lub hue/satuaration/jasności notacji.  
  
 Na poniższej ilustracji przedstawiono kilka `CMFCColorPickerCtrl` obiektów.  
  
 ![Okno dialogowe CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 `CMFCColorPickerCtrl` Obsługuje dwie pary style. Style HEX i HEX_GREYSCALE są odpowiednie dla standardowych kolor zaznaczenia. SELEKTOR i JASNOŚCI style są odpowiednie dla wybór koloru niestandardowego.  
  
 Wykonaj poniższe kroki, aby dołączyć do nich `CMFCColorPickerCtrl` kontroli do dialogowym:  
  
1.  Jeśli używasz **ClassWizard**, Wstaw nową kontrolkę przycisku do szablonu — okno dialogowe (ponieważ `CMFCColorPickerCtrl` klasy jest odziedziczone `CButton` klasy).  
  
2.  Wstaw zmiennej członkowskiej skojarzony z nowego formantu przycisku do pola klasy okien dialogowych. Następnie należy zmienić typ zmiennej z `CButton` do `CMFCColorPickerCtrl`.  
  
3.  Wstaw `WM_INITDIALOG` program obsługi komunikatów dla klasy okno dialogowe. W obsłudze, Ustaw typ, palety i początkowej wybrany kolor `CMFCColorPickerCtrl` formantu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania `CMFCColorPickerCtrl` obiektu przy użyciu różnych metod w `CMFCColorPickerCtrl` klasy. W przykładzie pokazano, jak ustawić typ formantu selektora i jak ustawić kolor, odcień, jasność i nasycenie. Przykładem jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcolorpickerctrl.h  
  
##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl  
 Konstruuje `CMFCColorPickerCtrl` obiektu.  
  
```  
CMFCColorPickerCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor  
 Wywoływane przez platformę przed wyświetleniem kursora, który wskazuje wybranego koloru.  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] *rect*  
 Określa prostokątny obszar wokół wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę, gdy trzeba zmienić kształt kursora, który wskazuje wybranego koloru.  
  
##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor  
 Pobiera kolor wybranego przez użytkownika.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości RGB wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS  
 Pobiera wartości odcień, jasność i nasycenie koloru przez użytkownika.  
  
```  
void GetHLS(
    double* hue,  
    double* luminance,  
    double* saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *hue*  
 Wskaźnik do zmiennej typu double służącą do odbierania informacji hue.  
  
 [out] *jasności*  
 Wskaźnik do zmiennej typu double odbierająca jasności informacji.  
  
 [out] *nasycenie*  
 Wskaźnik do zmiennej typu double odbierająca nasycenie informacji.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Pobiera składnik hue kolor wybranego przez użytkownika.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik aplikacji hue wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 Pobiera składnik jasności koloru przez użytkownika.  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik jasności wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 Pobiera wartość nasycenie koloru przez użytkownika.  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik nasycenie wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki kolorów RGB lub sześciokąt określona komórka.  
  
```  
void SelectCellHexagon(
    BYTE R,  
    BYTE G,  
    BYTE B);

 
BOOL SelectCellHexagon(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *R*  
 Składnik kolor czerwony.  
  
 [in] *G*  
 Składnik kolor zielony.  
  
 [in] *B*  
 Składnik niebieski.  
  
 [in] *x*  
 Współrzędna x kursor wskazuje sześciokąt komórki.  
  
 [in] *y*  
 Współrzędna y kursor wskazuje sześciokąt komórki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Drugi przeciążenie tej metody zawsze zwraca `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przeciążenia to bieżący kolor kolor, który odpowiada kontrolkę wyboru koloru ustawia — metoda obiektu określić kolor czerwony, zielonemu i niebieskiemu składników.  
  
 Drugi przeciążenie tej metody ustawia bieżący kolor na kolor sześciokąt komórki, która jest wskazywana przez kursor określonej lokalizacji.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Ustawia bieżący kolor do określonej wartości kolorów RGB.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Kolorów*  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 Ustawia bieżący kolor na określoną wartość koloru HLS.  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hue*  
 Wartość hue.  
  
 [in] *jasności*  
 Wartość jasności.  
  
 [in] *nasycenie*  
 Nasycenie.  
  
 [in] *bInvalidate*  
 `TRUE` Aby wymusić okno, aby natychmiast zaktualizować na nowy kolor; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 Zmienia odcienia, który aktualnie wybranego koloru.  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Hue*  
 Wartość hue.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 Zmienia jasności aktualnie wybranego koloru.  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Jasności*  
 Wartość jasności.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 Ustawia szerokość paska jasności w formancie selektora kolorów.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *w*  
 Szerokość paska jasności (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do zmiany rozmiaru paska jasności, który znajduje się w **niestandardowy** kartę formantu selektora kolorów. *w* parametr określa nową szerokość paska jasności. Wartość szerokości jest ignorowana, jeśli jego rozmiar przekracza trzy czwarte szerokość obszaru klienta.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Ustawia kolor wybranego początkowej.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *ref*  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać po zainicjowaniu formantu selektora kolorów.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Ustawia bieżący paletę kolorów.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pPalette*  
 Wskaźnik do paletę kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Palety kolorów definiuje tablicy kolorów, które są prezentowane w formancie selektora kolorów.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Zmienia nasycenie aktualnie wybranego koloru.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Nasycenie*  
 Nasycenie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Ustawia typ formantu selektora kolorów do wyświetlenia.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *colorType*  
 Typ formantu selektora kolorów.  
  
 Typy są definiowane przez `CMFCColorPickerCtrl::COLORTYPE` wyliczenia. Możliwe typy `LUMINANCE`, `PICKER`, `HEX` i `HEX_GREYSCALE`. Jest to domyślny typ `PICKER`.  
  
### <a name="remarks"></a>Uwagi  
 Aby określić typ formantu selektora kolorów, tę metodę należy wywołać przed utworzeniem sterowania systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)
