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
ms.openlocfilehash: 709992c42cf7fd489fbe8fe8d4ebf40bf92a989e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849968"
---
# <a name="cmfccolorpickerctrl-class"></a>Klasa CMFCColorPickerCtrl
`CMFCColorPickerCtrl` Klasa oferuje funkcję dla formantu, który jest używany do wybierania kolorów.  
  
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
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Pobiera wartości hue, jasność i nasycenie koloru, wybierany przez użytkownika.|  
|[CMFCColorPickerCtrl::GetHue](#gethue)|Pobiera składnika odcienia koloru, wybierany przez użytkownika.|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Pobiera składnik jasność koloru, wybierany przez użytkownika.|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Pobiera składnik nasycenie koloru, wybierany przez użytkownika.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki kolor RGB lub sześciokąt określona komórka.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Ustawia bieżący kolor do określonej wartości kolorów RGB.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Ustawia bieżący kolor na określoną wartość koloru HLS.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Zmiany składnika odcienia, który aktualnie wybranego koloru.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Zmiany składnika jasności aktualnie wybranego koloru.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Ustawia szerokość paska jasności w kontroli próbnika kolorów.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Ustawia kolor wybrany początkowy.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Ustawia bieżącej palecie kolorów.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Zmiany składnika nasycenie koloru zaznaczony.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Ustawia typ kontroli próbnika kolorów do wyświetlenia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Wywoływane przez platformę, przed wyświetleniem kursor, który wskazuje na wybranym kolorze.|  
  
## <a name="remarks"></a>Uwagi  
 Wybrano standardowe kolory z palety kolorów (sześciokąt), a kolorów niestandardowych są zaznaczone na pasku jasności w przypadku, gdy kolory są określone przy użyciu notacji czerwony/zielony/niebieski lub hue/satuaration/jasności notacji.  
  
 Poniższa ilustracja przedstawia kilka `CMFCColorPickerCtrl` obiektów.  
  
 ![Okno dialogowe CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 `CMFCColorPickerCtrl` Obsługuje dwie pary stylów. Style HEX i HEX_GREYSCALE są odpowiednie dla zaznaczenia kolor standardowy. Wybór i JASNOŚCI style są odpowiednie do wyboru koloru niestandardowego.  
  
 Wykonaj poniższe kroki, aby dołączyć `CMFCColorPickerCtrl` kontroli do dialogowym:  
  
1.  Jeśli używasz **ClassWizard**, Wstaw nową kontrolkę przycisku do usługi szablonu okna dialogowego (ponieważ `CMFCColorPickerCtrl` klasy jest dziedziczony z `CButton` klasy).  
  
2.  Wstaw zmiennej członkowskiej, która jest skojarzona z nową kontrolkę przycisku do swojej klasy okno dialogowe. Następnie zmień typ zmiennej z `CButton` do `CMFCColorPickerCtrl`.  
  
3.  Wstaw `WM_INITDIALOG` procedury obsługi komunikatów dla klasy okno dialogowe. W obsłudze, Ustaw typ, palety i początkowe wybrany kolor `CMFCColorPickerCtrl` kontroli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować `CMFCColorPickerCtrl` obiektu przy użyciu różnych metod w `CMFCColorPickerCtrl` klasy. W przykładzie pokazano, jak ustawić typ formantu selektora i jak ustawić kolor, hue, jasność i nasycenie. Przykład jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
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
 Wywoływane przez platformę, przed wyświetleniem kursor, który wskazuje na wybranym kolorze.  
  
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
 Należy przesłonić tę metodę, gdy trzeba zmienić kształt kursora, który wskazuje na wybranym kolorze.  
  
##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor  
 Pobiera kolor wybranego przez użytkownika.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość RGB wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS  
 Pobiera wartości hue, jasność i nasycenie koloru, wybierany przez użytkownika.  
  
```  
void GetHLS(
    double* hue,  
    double* luminance,  
    double* saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *hue*  
 Wskaźnik do zmiennej typu double odbierająca hue informacji.  
  
 [out] *jasności*  
 Wskaźnik do zmiennej typu double odbierająca jasności informacji.  
  
 [out] *nasycenia*  
 Wskaźnik do zmiennej typu double odbierająca nasycenie informacji.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Pobiera składnika odcienia koloru, wybierany przez użytkownika.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik aplikacji hue wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 Pobiera składnik jasność koloru, wybierany przez użytkownika.  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik jasności wybranego koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 Pobiera wartość nasycenie koloru, wybierany przez użytkownika.  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Składnik nasycenie kolorów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 Ustawia bieżący kolor na kolor zdefiniowany przez określone składniki kolor RGB lub sześciokąt określona komórka.  
  
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
 Kolor czerwony składnik.  
  
 [in] *G*  
 Kolor zielony składnik.  
  
 [in] *B*  
 Składnik niebieski.  
  
 [in] *x*  
 Współrzędna x kursora, które wskazuje sześciokąt komórki.  
  
 [in] *y*  
 Współrzędna y kursora, które wskazuje sześciokąt komórki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Drugie przeciążenie to metoda zawsze zwraca wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze przeciążenie tej metody ustawia bieżący kolor na kolor, który odpowiada kontrolkę wyboru koloru na określone składniki koloru czerwonego, zielonego i niebieskiego.  
  
 Drugie przeciążenie tej metody ustawia bieżący kolor kolor sześciokąt komórkę, która jest wskazywana przez lokalizacji kursora określony.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Ustawia bieżący kolor do określonej wartości kolorów RGB.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Kolorów*  
 Wartość koloru RGB.  
  
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
  
 [in] *nasycenia*  
 Wartość nasycenia koloru.  
  
 [in] *bInvalidate*  
 Wartość TRUE, aby wymusić okna, aby natychmiast zaktualizować na nowy kolor; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
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
 Ustawia szerokość paska jasności w kontroli próbnika kolorów.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *w*  
 Szerokość paska jasności (w pikselach).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do zmiany rozmiaru Pasek jasności, który znajduje się w **niestandardowe** kartę kontroli próbnika kolorów. *w* parametr określa nową szerokość paska jasności. Wartość szerokości jest ignorowany w przypadku przekroczenia trzy czwarte szerokość obszaru klienta.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Ustawia kolor wybrany początkowy.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *ref*  
 Wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę należy wywołać po zainicjowaniu kontroli próbnika kolorów.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Ustawia bieżącej palecie kolorów.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pPalette*  
 Wskaźnik do palety kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Paletę kolorów, która definiuje tablicy kolorów, które są prezentowane w kontroli próbnika kolorów.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Zmienia nasycenie koloru aktualnie wybrany.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Nasycenia*  
 Wartość nasycenia koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Ustawia typ kontroli próbnika kolorów do wyświetlenia.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *colorType*  
 Typ formantu selektora kolorów.  
  
 Typy są definiowane przez `CMFCColorPickerCtrl::COLORTYPE` wyliczenia. Możliwe typy są JASNOŚCI, wybór, HEX i HEX_GREYSCALE. Domyślnym typem jest wybór.  
  
### <a name="remarks"></a>Uwagi  
 Aby określić typ formantu selektora kolorów, tę metodę należy wywołać przed utworzeniem kontrolki Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)
