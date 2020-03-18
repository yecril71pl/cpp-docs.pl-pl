---
title: Klasa korzystanie CDateTimeCtrl
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
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418686"
---
# <a name="cdatetimectrl-class"></a>Klasa korzystanie CDateTimeCtrl

Hermetyzuje funkcjonalność formantu selektora daty i godziny.

## <a name="syntax"></a>Składnia

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CDateTimeCtrl:: Korzystanie CDateTimeCtrl](#cdatetimectrl)|Konstruuje obiekt `CDateTimeCtrl`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CDateTimeCtrl:: CloseMonthCal](#closemonthcal)|Zamyka bieżącą kontrolkę selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: Create](#create)|Tworzy kontrolkę selektora daty i godziny i dołącza ją do obiektu `CDateTimeCtrl`.|
|[Korzystanie CDateTimeCtrl:: GetDateTimePickerInfo](#getdatetimepickerinfo)|Pobiera informacje o bieżącej kontrolce selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: GetIdealSize](#getidealsize)|Zwraca idealny rozmiar kontrolki selektora daty i godziny, która jest wymagana do wyświetlenia bieżącej daty lub godziny.|
|[Korzystanie CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor)|Pobiera kolor danej części kalendarza miesięcznego w kontrolce selektora dat i godzin.|
|[Korzystanie CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Pobiera obiekt `CMonthCalCtrl` skojarzony z kontrolką selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: GetMonthCalFont](#getmonthcalfont)|Pobiera czcionkę aktualnie używaną przez formant selektora daty i godziny w kalendarzu podrzędnym.|
|[Korzystanie CDateTimeCtrl:: GetMonthCalStyle](#getmonthcalstyle)|Pobiera styl bieżącej kontrolki selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: GetRange](#getrange)|Pobiera bieżący minimalny i maksymalny dozwolony czas systemowy dla kontrolki selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: GetTime](#gettime)|Pobiera aktualnie wybrany czas z kontrolki selektora daty i godziny i umieszcza ją w określonej strukturze `SYSTEMTIME`.|
|[Korzystanie CDateTimeCtrl:: SetFormat](#setformat)|Ustawia sposób wyświetlania kontrolki selektora daty i godziny zgodnie z danym ciągiem formatu.|
|[Korzystanie CDateTimeCtrl:: SetMonthCalColor](#setmonthcalcolor)|Ustawia kolor danej części kalendarza miesięcznego w kontrolce selektora dat i godzin.|
|[Korzystanie CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Ustawia czcionkę, która będzie używana przez kontrolkę kalendarzowa elementu podrzędnego formantu daty i godziny.|
|[Korzystanie CDateTimeCtrl:: SetMonthCalStyle](#setmonthcalstyle)|Ustawia styl bieżącej kontrolki selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: SetRange](#setrange)|Ustawia minimalną i maksymalną dozwoloną godzinę systemową dla kontrolki selektora daty i godziny.|
|[Korzystanie CDateTimeCtrl:: SetTime](#settime)|Ustawia godzinę w kontrolce selektora daty i godziny.|

## <a name="remarks"></a>Uwagi

Kontrolka selektora daty i godziny (formant DTP) udostępnia prosty interfejs do wymiany informacji o dacie i godzinie użytkownika. Ten interfejs zawiera pola, z których każdy wyświetla część informacji o dacie i godzinie przechowywanych w formancie. Użytkownik może zmienić informacje przechowywane w kontrolce, zmieniając zawartość ciągu w danym polu. Użytkownik może przechodzić z pola do pola za pomocą myszy lub klawiatury.

Możesz dostosować kontrolkę selektora daty i godziny, stosując wiele stylów do obiektu podczas jego tworzenia. Aby uzyskać więcej informacji na temat stylów specyficznych dla kontrolki selektora daty i godziny, zobacz [Style kontrolki selektora daty i godziny](/windows/win32/Controls/date-and-time-picker-control-styles) w Windows SDK. Możesz ustawić format wyświetlania formantu DTP, używając stylów formatu. Te style formatu są opisane w sekcji "Style formatowania" w [stylu formantu selektora daty i godziny](/windows/win32/Controls/date-and-time-picker-control-styles)tematu Windows SDK.

Kontrolka selektora daty i godziny używa również powiadomień i wywołań zwrotnych, które są opisane w temacie [using korzystanie CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDTCTL. h

##  <a name="cdatetimectrl"></a>Korzystanie CDateTimeCtrl:: Korzystanie CDateTimeCtrl

Konstruuje obiekt `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>Korzystanie CDateTimeCtrl:: CloseMonthCal

Zamyka bieżącą kontrolkę selektora daty i godziny.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_dateTimeCtrl*, która jest używana do programistycznego dostępu do formantu selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zamyka kalendarz rozwijany dla bieżącej kontrolki selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>Korzystanie CDateTimeCtrl:: Create

Tworzy kontrolkę selektora daty i godziny i dołącza ją do obiektu `CDateTimeCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa kombinację stylów formantu daty i godziny. Aby uzyskać więcej informacji na temat stylów selektora daty i godziny, zobacz [Style kontrolki selektora daty i godziny](/windows/win32/Controls/date-and-time-picker-control-styles) w Windows SDK.

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , która jest pozycją i rozmiarem kontrolki selektora daty i godziny.

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu selektora daty i godziny. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki selektora daty i godziny.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli Tworzenie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##### <a name="to-create-a-date-and-time-picker-control"></a>Aby utworzyć kontrolkę selektora daty i godziny

1. Wywołaj [Korzystanie CDateTimeCtrl](#cdatetimectrl) w celu skonstruowania obiektu `CDateTimeCtrl`.

1. Wywołaj tę funkcję elementu członkowskiego, co spowoduje utworzenie kontrolki selektora daty i godziny systemu Windows i dołączenie jej do obiektu `CDateTimeCtrl`.

Podczas wywoływania `Create`są inicjowane typowe formanty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>Korzystanie CDateTimeCtrl:: GetDateTimePickerInfo

Pobiera informacje o bieżącej kontrolce selektora daty i godziny.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pDateTimePickerInfo*|określoną Wskaźnik do struktury [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) , która otrzymuje opis kontrolki selektora bieżącej daty i godziny.<br /><br /> Obiekt wywołujący jest odpowiedzialny za przydzielanie tej struktury. Jednak ta metoda Inicjuje element członkowski *cbSize* struktury.|

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_dateTimeCtrl*, która jest używana do programistycznego dostępu do formantu selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wskazuje, czy pomyślnie pobiera informacje o bieżącej kontrolce selektora dat i godzin.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>Korzystanie CDateTimeCtrl:: GetMonthCalColor

Pobiera kolor danej części kalendarza miesięcznego w kontrolce selektora dat i godzin.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
Wartość **int** określająca, który obszar kolorów kalendarza miesiąca ma zostać pobrany. Aby zapoznać się z listą wartości, zobacz *iColor* parametr [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Wartość zwrócona

Wartość COLORREF, która reprezentuje ustawienie koloru dla określonej części kontrolki kalendarza miesięcznego. Funkcja zwraca wartość-1, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>Korzystanie CDateTimeCtrl:: GetMonthCalCtrl

Pobiera obiekt `CMonthCalCtrl` skojarzony z kontrolką selektora daty i godziny.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) lub wartość null, jeśli okno nie jest widoczne.

### <a name="remarks"></a>Uwagi

Kontrolki selektora daty i godziny tworzą formant kalendarza podrzędnego miesiąc, gdy użytkownik kliknie strzałkę listy rozwijanej. Gdy obiekt `CMonthCalCtrl` nie jest już wymagany, zostanie zniszczony, więc aplikacja nie może polegać na przechowywaniu obiektu reprezentującego kalendarz podrzędny dla kontrolki selektora daty i godziny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>Korzystanie CDateTimeCtrl:: GetMonthCalFont

Pobiera czcionkę używaną obecnie przez kontrolkę kalendarza miesięcznego kontrolki selektora daty i godziny.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [CFont](../../mfc/reference/cfont-class.md) lub wartość null, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Obiekt `CFont` wskazywany przez wartość zwracaną jest obiektem tymczasowym i jest niszczony podczas następnego czasu bezczynności przetwarzania.

##  <a name="getmonthcalstyle"></a>Korzystanie CDateTimeCtrl:: GetMonthCalStyle

Pobiera styl kontrolki kalendarza miesiąca rozwijanego, która jest skojarzona z bieżącą kontrolką selektora dat i godzin.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Wartość zwrócona

Styl kontrolki kalendarza miesiąca rozwijanego, który jest kombinacją bitową (lub) stylów formantu selektora daty i godziny. Aby uzyskać więcej informacji, zobacz [Style kontrolki kalendarza miesięcznego](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) , który jest opisany w Windows SDK.

##  <a name="getrange"></a>Korzystanie CDateTimeCtrl:: GetRange

Pobiera bieżący minimalny i maksymalny dozwolony czas systemowy dla kontrolki selektora daty i godziny.

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
Wskaźnik do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) zawierającego Najwcześniejszy czas dozwolony w obiekcie `CDateTimeCtrl`.

*pMaxRange*<br/>
Wskaźnik do obiektu `COleDateTime` lub obiektu `CTime` zawierającego ostatni czas dozwolony w obiekcie `CDateTimeCtrl`.

### <a name="return-value"></a>Wartość zwrócona

Wartość DWORD zawierająca flagi wskazujące, które zakresy są ustawione. Jeśli użytkownik

`return value & GDTR_MAX` = = 0

następnie drugi parametr jest prawidłowy. Podobnie, jeśli

`return value & GDTR_MIN` = = 0

następnie pierwszy parametr jest prawidłowy.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)komunikatu Win32, zgodnie z opisem w Windows SDK. W implementacji MFC można określić użycie `COleDateTime` lub `CTime`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>Korzystanie CDateTimeCtrl:: GetTime

Pobiera aktualnie wybrany czas z kontrolki selektora daty i godziny i umieszcza ją w określonej strukturze `SYSTEMTIME`.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
W pierwszej wersji odwołanie do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który otrzyma informacje o czasie systemowym. W drugiej wersji odwołanie do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) , który otrzyma informacje o czasie systemowym.

*pTimeDest*<br/>
Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , aby uzyskać informacje o czasie systemowym. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwrócona

W pierwszej wersji, niezerowej, jeśli czas został pomyślnie zapisany w obiekcie `COleDateTime`; w przeciwnym razie 0. W drugiej i trzeciej wersji wartość DWORD równa *dwFlagemu* zestawowi członkowskiemu w strukturze [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) . Aby uzyskać więcej informacji, zobacz sekcję **uwagi** poniżej.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)komunikatu Win32, zgodnie z opisem w Windows SDK. W implementacji MFC `GetTime`można użyć klas `COleDateTime` lub `CTime` lub użyć struktury `SYSTEMTIME` do przechowywania informacji o czasie.

Wartość zwracana DWORD w drugiej i trzeciej wersji, powyżej, wskazuje, czy kontrolka selektora daty i godziny ma ustawioną wartość "brak daty", jak wskazano w elemencie członkowskim struktury [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *flagiDW*. Jeśli zwracana wartość jest równa GDT_NONE, formant jest ustawiony na wartość "No Date" i używa stylu DTS_SHOWNONE. Jeśli wartość zwracana jest równa GDT_VALID, czas systemowy zostanie pomyślnie zapisany w lokalizacji docelowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>Korzystanie CDateTimeCtrl:: GetIdealSize

Zwraca idealny rozmiar kontrolki selektora daty i godziny, która jest wymagana do wyświetlenia bieżącej daty lub godziny.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*psize*|określoną Wskaźnik do struktury [rozmiaru](/windows/win32/api/windef/ns-windef-size) , który zawiera idealny rozmiar kontrolki.|

### <a name="return-value"></a>Wartość zwrócona

Wartość zwracana jest zawsze prawdziwa.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_dateTimeCtrl*, która jest używana do programistycznego dostępu do formantu selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera idealny rozmiar do wyświetlania kontrolki selektora dat i godzin.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>Korzystanie CDateTimeCtrl:: SetFormat

Ustawia sposób wyświetlania kontrolki selektora daty i godziny zgodnie z danym ciągiem formatu.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parametry

*pstrFormat*<br/>
Wskaźnik do ciągu formatu zakończony zerem, który definiuje żądany ekran. Ustawienie tego parametru na wartość NULL spowoduje zresetowanie formantu do domyślnego ciągu formatu dla bieżącego stylu.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

> [!NOTE]
>  Dane wejściowe użytkownika nie określają sukcesu lub niepowodzenia dla tego wywołania.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>Korzystanie CDateTimeCtrl:: SetMonthCalColor

Ustawia kolor danej części kalendarza miesięcznego w kontrolce selektora dat i godzin.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*iColor*<br/>
wartość **int** określająca, który obszar kontrolki kalendarza miesięcznego ma zostać ustawiony. Może to być jedna z następujących wartości.

|Wartość|Znaczenie|
|-----------|-------------|
|MCSC_BACKGROUND|Ustaw kolor tła wyświetlany między miesiącami.|
|MCSC_MONTHBK|Ustaw kolor tła wyświetlany w ciągu miesiąca.|
|MCSC_TEXT|Ustaw kolor używany do wyświetlania tekstu w ciągu miesiąca.|
|MCSC_TITLEBK|Ustaw kolor tła wyświetlany w tytule kalendarza.|
|MCSC_TITLETEXT|Ustaw kolor używany do wyświetlania tekstu w tytule kalendarza.|
|MCSC_TRAILINGTEXT|Ustaw kolor używany do wyświetlania nagłówka i tekstu końcowego. Dni nagłówka i końcowe są dni od poprzedniego i następnego miesiąca, które są wyświetlane w bieżącym kalendarzu.|

*ref*<br/>
Wartość COLORREF reprezentująca kolor, który zostanie ustawiony dla określonego obszaru kalendarza miesiąca.

### <a name="return-value"></a>Wartość zwrócona

Wartość COLORREF, która reprezentuje poprzednie ustawienie koloru dla określonej części kontrolki kalendarza miesięcznego. W przeciwnym razie komunikat zwróci wartość-1.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CDateTimeCtrl:: GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>Korzystanie CDateTimeCtrl:: SetMonthCalFont

Ustawia czcionkę, która będzie używana przez kontrolkę kalendarzowa elementu podrzędnego formantu daty i godziny.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
Dojście do czcionki, która zostanie ustawiona.

*bRedraw*<br/>
Określa, czy kontrolka ma być odświeżana bezpośrednio po ustawieniu czcionki. Ustawienie dla tego parametru wartości TRUE powoduje, że formant będzie ponownie rysowany.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)komunikatu Win32, zgodnie z opisem w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  W przypadku użycia tego kodu należy utworzyć element członkowski klasy pochodnej `CDialog`o nazwie *m_MonthFont* `CFont`.

##  <a name="setmonthcalstyle"></a>Korzystanie CDateTimeCtrl:: SetMonthCalStyle

Ustawia styl kontrolki kalendarza miesięcznej wartości skojarzonej z bieżącą kontrolką selektora dat i godzin.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwStyle*|podczas Styl formantu kalendarza nowego miesiąca, który jest kombinacją bitową (lub) stylów formantu kalendarza miesięcznego. Aby uzyskać więcej informacji, zobacz [Style kontrolki kalendarza miesięcznego](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Wartość zwrócona

Poprzedni styl kontrolki kalendarza miesiąca listy rozwijanej.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_dateTimeCtrl*, która jest używana do programistycznego dostępu do formantu selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia kontrolkę selektora daty i godziny, aby wyświetlić numery tygodni, skrócone nazwy dni tygodnia i brak wskaźnika dzisiaj.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>Korzystanie CDateTimeCtrl:: SetRange

Ustawia minimalną i maksymalną dozwoloną godzinę systemową dla kontrolki selektora daty i godziny.

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
Wskaźnik do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) zawierającego Najwcześniejszy czas dozwolony w obiekcie `CDateTimeCtrl`.

*pMaxRange*<br/>
Wskaźnik do obiektu `COleDateTime` lub obiektu `CTime` zawierającego ostatni czas dozwolony w obiekcie `CDateTimeCtrl`.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)komunikatu Win32, zgodnie z opisem w Windows SDK. W implementacji MFC można określić użycie `COleDateTime` lub `CTime`. Jeśli obiekt `COleDateTime` ma stan NULL, zakres zostanie usunięty. Jeśli wskaźnik `CTime` lub wskaźnik `COleDateTime` ma wartość NULL, zakres zostanie usunięty.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CDateTimeCtrl:: GetRange](#getrange).

##  <a name="settime"></a>Korzystanie CDateTimeCtrl:: SetTime

Ustawia godzinę w kontrolce selektora daty i godziny.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parametry

*timeNew*<br/>
Odwołanie do obiektu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zawierającego element, do którego zostanie ustawiony formant.

*pTimeNew*<br/>
W drugiej wersji, wskaźnik do obiektu [CTime](../../atl-mfc-shared/reference/ctime-class.md) zawierającego godzinę, do której zostanie ustawiony formant. W trzeciej wersji, wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej godzinę, do której zostanie ustawiony formant.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)komunikatu Win32, zgodnie z opisem w Windows SDK. W implementacji MFC `SetTime`można użyć klas `COleDateTime` lub `CTime` lub użyć struktury `SYSTEMTIME`, aby ustawić informacje o czasie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CMNCTRL1 MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)
