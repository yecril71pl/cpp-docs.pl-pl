---
title: Klasa CDateTimeCtrl
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: 36ef44534803e35d3544b53dbeeca75a7fb3f475
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178528"
---
# <a name="cdatetimectrl-class"></a>Klasa CDateTimeCtrl

Hermetyzuje funkcjonalność formantu wyboru daty i godziny.

## <a name="syntax"></a>Składnia

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Konstruuje `CDateTimeCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Zamyka bieżący formant selektora daty i godziny.|
|[CDateTimeCtrl::Create](#create)|Tworzy formant selektora daty i godziny i dołącza je do `CDateTimeCtrl` obiektu.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Pobiera informacje o bieżącym kontrolka selektora daty i godziny.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Zwraca rozmiar idealny formantu selektora daty i godziny, który jest wymagany, aby wyświetlić bieżącą datę lub godzinę.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Pobiera kolor dla danej części kalendarza miesięcznego w kontrolce selektora daty i godziny.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Pobiera `CMonthCalCtrl` obiekt skojarzony z kontrolka selektora daty i godziny.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Pobiera czcionki obecnie używane przez datę i formant kalendarza miesięcznego podrzędnych formant selektora czasu.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Pobiera styl bieżący formant selektora daty i godziny.|
|[CDateTimeCtrl::GetRange](#getrange)|Pobiera bieżący minimalne i maksymalne dozwolone czasy systemowe kontrolki selektora daty i godziny.|
|[CDateTimeCtrl::GetTime](#gettime)|Pobiera zaznaczony czas w kontrolce selektora daty i godziny i umieszcza go w określonej `SYSTEMTIME` struktury.|
|[CDateTimeCtrl::SetFormat](#setformat)|Ustawia wyświetlaną kontrolki selektora daty i godziny zgodnie z ciągu danego formatu.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Ustawia kolor dla danej części kalendarza miesięcznego w kontrolce selektora daty i godziny.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Ustawia czcionkę, używanego przez formant kalendarza miesięcznego podrzędnych Data i godzina selektor formantu.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Ustawia styl bieżący formant selektora daty i godziny.|
|[CDateTimeCtrl::SetRange](#setrange)|Ustawia czas minimalne i maksymalne wersje systemu dozwolonych dla kontrolki selektora daty i godziny.|
|[CDateTimeCtrl::SetTime](#settime)|Ustawia czas w kontrolce selektora daty i godziny.|

## <a name="remarks"></a>Uwagi

Kontrolka selektora daty i godziny (kontrolce DTP) udostępnia prosty interfejs do wymiany informacji daty i godziny z użytkownikiem. Ten interfejs zawiera pola, z których każdy zawiera część daty i godziny informacje przechowywane w formancie. Użytkownik może zmienić informacje przechowywane w formancie, zmieniając zawartość ciągu w danym polu. Użytkownik może przenieść do innego pola przy użyciu myszy lub klawiatury.

Kontrolka selektora daty i godziny można dostosować przez zastosowanie różnych stylów do obiektu podczas jego tworzenia. Zobacz [style daty i godziny selektor formantu](/windows/desktop/Controls/date-and-time-picker-control-styles) w zestawie Windows SDK, aby uzyskać więcej informacji o stylach specyficzne dla kontrolki selektora daty i godziny. Można ustawić format wyświetlania kontrolki DTP, przy użyciu stylów formatowania. Te style formatu są opisane w obszarze "Format style" w temacie Windows SDK [style daty i godziny selektor formantu](/windows/desktop/Controls/date-and-time-picker-control-styles).

Kontrolka selektora daty i czasu używa także powiadomienia i wywołania zwrotne, które są opisane w [korzystanie z CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

Konstruuje `CDateTimeCtrl` obiektu.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

Zamyka bieżący formant selektora daty i godziny.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_dateTimeCtrl*, która jest używana do uzyskania programowego dostępu kontrolka selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zamyka kalendarz rozwijany dla bieżącego kontrolka selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

Tworzy formant selektora daty i godziny i dołącza je do `CDateTimeCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa kombinację style kontrolki czasu daty. Zobacz [style daty i godziny selektor formantu](/windows/desktop/Controls/date-and-time-picker-control-styles) w zestawie Windows SDK, aby uzyskać więcej informacji o stylach selektora daty i godziny.

*Rect*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar kontrolki selektora daty i godziny.

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki selektora daty i godziny. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator daty i godziny selektor formantu kontroli.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##### <a name="to-create-a-date-and-time-picker-control"></a>Aby utworzyć kontrolkę selektora daty i godziny

1. Wywołaj [CDateTimeCtrl](#cdatetimectrl) do konstruowania `CDateTimeCtrl` obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, który tworzy formant selektora daty i godziny Windows i dołącza go do `CDateTimeCtrl` obiektu.

Gdy wywołujesz `Create`, typowe formanty są inicjowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

Pobiera informacje o bieżącym kontrolka selektora daty i godziny.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out] Wskaźnik do [DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo) strukturę, która odbiera opis bieżącego kontrolka selektora daty i godziny.<br /><br /> Obiekt wywołujący jest odpowiedzialny za przydzielanie tej struktury. Jednak ta metoda inicjuje *elementu cbSize* elementu członkowskiego struktury.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_dateTimeCtrl*, która jest używana do uzyskania programowego dostępu kontrolka selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wskazuje, czy pomyślnie pobiera informacje o bieżącym kontrolka selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

Pobiera kolor dla danej części kalendarza miesięcznego w kontrolce selektora daty i godziny.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
**Int** wartość określającą, jaki obszar kolor kalendarza miesięcznego do pobrania. Aby uzyskać listę wartości, zobacz *iColor* parametr [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF, która reprezentuje ustawienia koloru dla określonej części formant kalendarza miesięcznego, jeśli to się powiedzie. Funkcja zwraca wartość -1 w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl

Pobiera `CMonthCalCtrl` obiekt skojarzony z kontrolka selektora daty i godziny.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) obiekt lub wartość NULL w przypadku niepowodzenia lub jeśli okno nie jest widoczna.

### <a name="remarks"></a>Uwagi

Selektora daty i godziny utworzyć formant kalendarza miesięcznego podrzędnych, gdy użytkownik kliknie strzałkę listy rozwijanej. Gdy `CMonthCalCtrl` obiektu nie jest już potrzebny, on jest niszczony, dzięki czemu aplikacja nie należy polegać na przechowywanie obiekt reprezentujący kalendarza miesięcznego podrzędnych formant selektora czasu daty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

Pobiera czcionki obecnie używane przez datę i formant kalendarza miesięcznego formant selektora czasu.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CFont](../../mfc/reference/cfont-class.md) obiekt lub wartość NULL, jeśli nie powiedzie.

### <a name="remarks"></a>Uwagi

`CFont` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i jest niszczony, podczas następnego przetwarzania bezczynności.

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

Pobiera rodzaj formant kalendarza miesięcznego listy rozwijanej, który jest skojarzony z bieżącym kontrolka selektora daty i godziny.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Styl formant kalendarza miesięcznego listy rozwijanej, która jest bitową kombinacją (lub) style kontrolki selektora daty i godziny. Aby uzyskać więcej informacji, zobacz [style kontrolki kalendarza miesięcznego](/windows/desktop/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

Pobiera bieżący minimalne i maksymalne dozwolone czasy systemowe kontrolki selektora daty i godziny.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Wskaźnik do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający Najwcześniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.

*pMaxRange*<br/>
Wskaźnik do `COleDateTime` obiektu lub `CTime` obiekt zawierający Najpóźniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawierającą flagi wskazujące, której zakresy są ustawione. IF

`return value & GDTR_MAX` == 0

drugi parametr jest prawidłowy. Podobnie jeśli

`return value & GDTR_MIN` == 0

następnie pierwszy parametr jest prawidłowy.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC można określić albo `COleDateTime` lub `CTime` użycia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

Pobiera zaznaczony czas w kontrolce selektora daty i godziny i umieszcza go w określonej `SYSTEMTIME` struktury.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
W pierwszej wersji odwołania do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego. W drugiej wersji odwołania do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego.

*pTimeDest*<br/>
Wskaźnik do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę do odbierania informacji o czasie systemu. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

W pierwszej wersji wartość różną od zera, jeśli pomyślnie zapisane czas `COleDateTime` obiektu; w przeciwnym razie 0. W wersjach drugi i trzeci równa wartości DWORD *dwFlag* zestaw elementów członkowskich [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury. Zobacz **uwagi** sekcji poniżej, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC `GetTime`, możesz użyć `COleDateTime` lub `CTime` klas, lub użyć `SYSTEMTIME` struktura do przechowywania informacji o czasie.

Zwracana wartość DWORD w wersjach drugi i trzeci powyżej, wskazuje, czy kontrolka selektora daty i godziny jest ustawiona na stan "nie daty", zgodnie z instrukcjami w [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) element członkowski struktury *Flagidw* . Jeśli wartość zwracana równa GDT_NONE, kontrolki jest ustawiona na stan "nie daty", a następnie używa stylu DTS_SHOWNONE. Jeśli wartość zwracana równa GDT_VALID, czas systemowy zostały pomyślnie zapisane w lokalizacji docelowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

Zwraca rozmiar idealny formantu selektora daty i godziny, który jest wymagany, aby wyświetlić bieżącą datę lub godzinę.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*psize*|[out] Wskaźnik do [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) strukturę, która zawiera rozmiar idealny dla formantu.|

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest zawsze wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_dateTimeCtrl*, która jest używana do uzyskania programowego dostępu kontrolka selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykładowy kod pobiera rozmiar idealny, aby wyświetlić formant selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

Ustawia wyświetlaną kontrolki selektora daty i godziny zgodnie z ciągu danego formatu.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parametry

*pstrFormat*<br/>
Wskaźnik do ciągu formatu zakończony zerem, który definiuje żądany ekran. Ustawienie tego parametru na wartość NULL spowoduje zresetowanie kontrolki do domyślny ciąg formatu dla bieżącego stylu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

> [!NOTE]
>  Dane wejściowe użytkownika nie określa powodzenie lub Niepowodzenie dla tego wywołania.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

Ustawia kolor dla danej części kalendarza miesięcznego w kontrolce selektora daty i godziny.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
**int** wartość określającą, jaki obszar formant kalendarza miesięcznego, aby ustawić. Ta wartość może być jedną z następujących czynności.

|Wartość|Znaczenie|
|-----------|-------------|
|MCSC_BACKGROUND|Ustaw kolor tła wyświetlany między miesięcy.|
|MCSC_MONTHBK|Ustaw kolor tła wyświetlany w ciągu miesiąca.|
|MCSC_TEXT|Ustaw kolor używany do wyświetlania tekstu w ciągu miesiąca.|
|MCSC_TITLEBK|Ustaw kolor tła, wyświetlany w tytule kalendarza.|
|MCSC_TITLETEXT|Ustaw kolor używany do wyświetlania tekstu w tytule kalendarza.|
|MCSC_TRAILINGTEXT|Ustaw kolor używany do wyświetlania nagłówka i końcowy dzień tekstu. Dni poprzedzające i korzysta z poprzednich i następnych miesięcy, które pojawiają się na bieżącym kalendarzu.|

*ref*<br/>
Wartość COLORREF reprezentującą color, ustawioną dla określonego obszaru kalendarza miesięcznego.

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF, która reprezentuje poprzedniego ustawienia kolorów dla określonej części formant kalendarza miesięcznego, jeśli to się powiedzie. W przeciwnym razie komunikat zwraca -1.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

Ustawia czcionkę, używanego przez formant kalendarza miesięcznego podrzędnych Data i godzina selektor formantu.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
Obsługa czcionki, zostaną ustawione.

*bRedraw*<br/>
Określa, czy formant powinien narysowania natychmiast po ustawienia czcionki. Ustawienie tego parametru na wartość TRUE powoduje, że formant do narysowania.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont), zgodnie z opisem w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Jeśli używasz tego kodu, należy wprowadzić jako członka Twojej `CDialog`-pochodne klasy o nazwie *m_MonthFont* typu `CFont`.

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

Ustawia styl formant kalendarza miesięcznego listy rozwijanej, który jest skojarzony z bieżącym kontrolka selektora daty i godziny.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwStyle*|[in] Nowego miesiąca w kalendarzu stylu formantu, który jest bitową kombinacją (lub) style kontrolki kalendarza miesięcznego. Aby uzyskać więcej informacji, zobacz [style kontrolki kalendarza miesięcznego](/windows/desktop/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Poprzednie styl formant kalendarza miesięcznego listy rozwijanej.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_dateTimeCtrl*, która jest używana do uzyskania programowego dostępu kontrolka selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia kontrolka selektora daty i godziny, aby wyświetlać numery tygodni, skrócone nazwy dni tygodnia i nie dzisiaj wskaźnika.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

Ustawia czas minimalne i maksymalne wersje systemu dozwolonych dla kontrolki selektora daty i godziny.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange*<br/>
Wskaźnik do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający Najwcześniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.

*pMaxRange*<br/>
Wskaźnik do `COleDateTime` obiektu lub `CTime` obiekt zawierający Najpóźniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC można określić albo `COleDateTime` lub `CTime` użycia. Jeśli `COleDateTime` obiekt ma stan o wartości NULL, zakresu zostaną usunięte. Jeśli `CTime` wskaźnika lub `COleDateTime` wskaźnik ma wartość NULL, zakresu zostaną usunięte.

### <a name="example"></a>Przykład

  Zobacz przykład [CDateTimeCtrl::GetRange](#getrange).

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

Ustawia czas w kontrolce selektora daty i godziny.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierającą obiekt, do której formant zostanie ustawiony.

*pTimeNew*<br/>
W drugiej wersji powyżej aby wskazywał [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający czas, do którego zostanie ustawiona formantu. W trzeciej wersji powyżej aby wskazywał [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury zawierającej czasu, do którego zostanie ustawiona formantu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC `SetTime`, możesz użyć `COleDateTime` lub `CTime` klas, lub użyć `SYSTEMTIME` struktury, aby ustawić informacje o czasie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[CMNCTRL1 próbki MFC](../../visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)
