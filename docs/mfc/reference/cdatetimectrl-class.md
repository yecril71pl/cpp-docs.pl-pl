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
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321912"
---
# <a name="cdatetimectrl-class"></a>Klasa CDateTimeCtrl

Hermetyzuje funkcjonalność kontrolki selektora daty i godziny.

## <a name="syntax"></a>Składnia

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Konstruuje `CDateTimeCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDateTimeCtrl::ZamknijMonthCal](#closemonthcal)|Zamyka bieżącą kontrolkę selektora daty i godziny.|
|[CDateTimeCtrl::Utwórz](#create)|Tworzy kontrolkę selektora daty i `CDateTimeCtrl` godziny i dołącza ją do obiektu.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Pobiera informacje o bieżącej kontroli selektora daty i godziny.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Zwraca idealny rozmiar kontrolki selektora daty i godziny, który jest wymagany do wyświetlenia bieżącej daty lub godziny.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Pobiera kolor dla danej części kalendarza miesiąca w obszarze kontroli selektora daty i godziny.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Pobiera `CMonthCalCtrl` obiekt skojarzony z formantem selektora daty i godziny.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Pobiera czcionkę aktualnie używaną przez kontrolkę kalendarza podrzędnego miesiąca podrzędnego formantu selektora daty i godziny.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Pobiera styl bieżącej kontrolki selektora daty i godziny.|
|[CDateTimeCtrl::GetRange](#getrange)|Pobiera bieżące minimalne i maksymalne dozwolone czasy systemowe dla kontrolki selektora daty i godziny.|
|[CDateTimeCtrl::GetTime](#gettime)|Pobiera aktualnie wybrany czas z kontrolki selektora daty `SYSTEMTIME` i godziny i umieszcza go w określonej strukturze.|
|[CDateTimeCtrl::SetFormat](#setformat)|Ustawia wyświetlanie kontrolki selektora daty i godziny zgodnie z danym ciągiem formatu.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Ustawia kolor dla danej części kalendarza miesiąca w obszarze kontroli selektora daty i godziny.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Ustawia czcionkę, która będzie używana jako formant kalendarza miesiąca podrzędnego daty i godziny.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Ustawia styl bieżącej kontrolki selektora daty i godziny.|
|[CDateTimeCtrl::SetRange](#setrange)|Ustawia minimalną i maksymalną dozwoloną liczbę czasów systemowych dla kontroli selektora daty i godziny.|
|[CDateTimeCtrl::SetTime](#settime)|Ustawia godzinę w formancie selektora daty i godziny.|

## <a name="remarks"></a>Uwagi

Kontrolka selektora daty i godziny (kontrolka DTP) zapewnia prosty interfejs do wymiany informacji o dacie i godzinie z użytkownikiem. Ten interfejs zawiera pola, z których każdy wyświetla część informacji o dacie i godzinie przechowywanych w formancie. Użytkownik może zmienić informacje przechowywane w formancie, zmieniając zawartość ciągu w danym polu. Użytkownik może przechodzić z pola do pola za pomocą myszy lub klawiatury.

Formant selektora daty i godziny można dostosować, stosując różne style do obiektu podczas jego tworzenia. Zobacz [Style sterowania selektorem daty i godziny](/windows/win32/Controls/date-and-time-picker-control-styles) w usłudze Windows SDK, aby uzyskać więcej informacji na temat stylów specyficznych dla kontrolki selektora daty i godziny. Format wyświetlania formantu DTP można ustawić za pomocą stylów formatowania. Te style formatu są opisane w obszarze "Style formatu" w temacie [Data i czas selektora](/windows/win32/Controls/date-and-time-picker-control-styles)czasu w temacie Windows SDK .

Formant selektora daty i godziny używa również powiadomień i wywołań zwrotnych, które są opisane w [za pomocą funkcji CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl

Konstruuje `CDateTimeCtrl` obiekt.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::ZamknijMonthCal

Zamyka bieżącą kontrolkę selektora daty i godziny.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_CLOSEMONTHCAL,](/windows/win32/Controls/dtm-closemonthcal) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_dateTimeCtrl*, która jest używana do programowego dostępu do kontroli selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zamyka kalendarz rozwijany dla bieżącej kontrolki selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Utwórz

Tworzy kontrolkę selektora daty i `CDateTimeCtrl` godziny i dołącza ją do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa kombinację stylów kontroli daty. Aby uzyskać więcej informacji na temat stylów selektora daty i godziny, zobacz [Style sterowania selektorem daty i godziny](/windows/win32/Controls/date-and-time-picker-control-styles) w programie Windows SDK.

*Rect*<br/>
Odwołanie do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która jest położenie i rozmiar kontrolki selektora daty i godziny.

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest nadrzędnym oknie kontrolki selektora daty i godziny. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu daty i godziny.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli tworzenie zakończyło się sukcesem; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##### <a name="to-create-a-date-and-time-picker-control"></a>Aby utworzyć kontrolkę selektora daty i godziny

1. Wywołanie [CDateTimeCtrl](#cdatetimectrl) `CDateTimeCtrl` do konstruowania obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, która tworzy kontrolkę selektora daty i godziny systemu Windows i dołącza ją do `CDateTimeCtrl` obiektu.

Podczas wywoływania `Create`typowe formanty są inicjowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo

Pobiera informacje o bieżącej kontroli selektora daty i godziny.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pDateTimePickerInfo*|[na zewnątrz] Wskaźnik do [struktury DATETIMEPICKERINFO,](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) który otrzymuje opis bieżącej kontrolki selektora daty i godziny.<br /><br /> Wywołujący jest odpowiedzialny za przydzielanie tej struktury. Jednak ta metoda inicjuje *element członkowski cbSize* struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETDATETIMEPICKERINFO,](/windows/win32/Controls/dtm-getdatetimepickerinfo) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_dateTimeCtrl*, która jest używana do programowego dostępu do kontroli selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wskazuje, czy pomyślnie pobiera informacje o bieżącej kontroli selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor

Pobiera kolor dla danej części kalendarza miesiąca w obszarze kontroli selektora daty i godziny.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Parametry

*Kolor iColor*<br/>
Wartość **int** określająca obszar koloru kalendarza miesiąca do pobrania. Aby uzyskać listę wartości, zobacz parametr *iColor* dla [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF, która reprezentuje ustawienie kolorów dla określonej części kontrolki kalendarza miesiąca, jeśli zakończy się pomyślnie. Funkcja zwraca wartość -1, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl

Pobiera `CMonthCalCtrl` obiekt skojarzony z formantem selektora daty i godziny.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) lub NULL, jeśli nie powiedzie się lub jeśli okno nie jest widoczne.

### <a name="remarks"></a>Uwagi

Formanty selektora daty i godziny tworzą formant kalendarza miesiąca podrzędnego, gdy użytkownik kliknie strzałkę listy rozwijanej. Gdy `CMonthCalCtrl` obiekt nie jest już potrzebny, jest niszczony, więc aplikacja nie może polegać na przechowywaniu obiektu reprezentującego kalendarz miesiąca podrzędnego formantu daty selektora czasu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont

Pobiera czcionkę aktualnie używaną przez kontrolkę kalendarza miesiąca selektora daty i godziny.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CFont](../../mfc/reference/cfont-class.md) lub NULL, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Obiekt `CFont` wskazywalny przez zwracaną wartość jest obiektem tymczasowym i jest niszczony podczas następnego czasu przetwarzania bezczynnego.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle

Pobiera styl formantu kalendarza rozwijanego miesiąca, który jest skojarzony z bieżącą kontrolką selektora daty i godziny.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Styl formantu kalendarza rozwijanego miesiąca, który jest kombinacją bitową (OR) stylów kontroli selektora daty i godziny. Aby uzyskać więcej informacji, zobacz [Style sterowania kalendarzem miesiąca](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETMCSTYLE,](/windows/win32/Controls/dtm-getmcstyle) który jest opisany w windows SDK.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange

Pobiera bieżące minimalne i maksymalne dozwolone czasy systemowe dla kontrolki selektora daty i godziny.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*pMinRange (pMinRange)*<br/>
Wskaźnik do [obiektu COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) zawierający najwcześniejszy czas `CDateTimeCtrl` dozwolony w obiekcie.

*pMaxRange (Polski)*<br/>
Wskaźnik do `COleDateTime` obiektu lub `CTime` obiektu zawierającego ostatni dozwolony `CDateTimeCtrl` czas w obiekcie.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawierająca flagi wskazujące, które zakresy są ustawione. Jeśli użytkownik

`return value & GDTR_MAX`== 0

wtedy drugi parametr jest prawidłowy. Podobnie, jeśli

`return value & GDTR_MIN`== 0

wtedy pierwszy parametr jest prawidłowy.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC można określić `COleDateTime` `CTime` albo użycia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime

Pobiera aktualnie wybrany czas z kontrolki selektora daty `SYSTEMTIME` i godziny i umieszcza go w określonej strukturze.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parametry

*timeDest (czas)*<br/>
W pierwszej wersji odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który otrzyma informacje o czasie systemowym. W drugiej wersji odwołanie do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który otrzyma informacje o czasie systemowym.

*pTimeDest (Identyfikator czasu)*<br/>
Wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) aby otrzymać informacje o czasie systemowym. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

W pierwszej wersji, nonzero, jeśli czas jest `COleDateTime` pomyślnie zapisany do obiektu; w przeciwnym razie 0. W drugiej i trzeciej wersji wartość DWORD równa element *członkowskiemu dwFlag* w strukturze [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Zobacz **uwagi** poniżej, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji `GetTime`MFC , `COleDateTime` można `CTime` użyć lub klas `SYSTEMTIME` lub można użyć struktury, do przechowywania informacji o czasie.

Zwracana wartość DWORD w drugiej i trzeciej wersji, powyżej, wskazuje, czy formant selektora daty i godziny jest ustawiony na stan "no date", jak wskazano w *dwFlags*członka struktury [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) . Jeśli zwrócona wartość jest równa GDT_NONE, formant jest ustawiony na stan "no date" i używa stylu DTS_SHOWNONE. Jeśli zwrócona wartość jest równa GDT_VALID, czas systemowy jest pomyślnie przechowywany w lokalizacji docelowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize

Zwraca idealny rozmiar kontrolki selektora daty i godziny, który jest wymagany do wyświetlenia bieżącej daty lub godziny.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*psize (psize)*|[na zewnątrz] Wskaźnik do [size](/windows/win32/api/windef/ns-windef-size) struktury, która zawiera idealny rozmiar dla formantu.|

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość jest zawsze PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_GETIDEALSIZE,](/windows/win32/Controls/dtm-getidealsize) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_dateTimeCtrl*, która jest używana do programowego dostępu do kontroli selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu pobiera rozmiar idealny do wyświetlania kontrolki selektora daty i godziny.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::SetFormat

Ustawia wyświetlanie kontrolki selektora daty i godziny zgodnie z danym ciągiem formatu.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Parametry

*pstrFormat*<br/>
Wskaźnik do ciągu formatu zakończonego z zerowym zakończeniem, który definiuje żądany ekran. Ustawienie tego parametru na WARTOŚĆ NULL spowoduje zresetowanie formantu do domyślnego ciągu formatu dla bieżącego stylu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

> [!NOTE]
> Dane wejściowe użytkownika nie określa sukcesu lub niepowodzenia dla tego wywołania.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor

Ustawia kolor dla danej części kalendarza miesiąca w obszarze kontroli selektora daty i godziny.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*Kolor iColor*<br/>
**wartość int** określająca obszar formantu kalendarza miesiąca do ustawienia. Ta wartość może być jedną z następujących czynności.

|Wartość|Znaczenie|
|-----------|-------------|
|MCSC_BACKGROUND|Ustaw kolor tła wyświetlany między miesiącami.|
|MCSC_MONTHBK|Ustaw kolor tła wyświetlany w ciągu miesiąca.|
|MCSC_TEXT|Ustaw kolor używany do wyświetlania tekstu w ciągu miesiąca.|
|MCSC_TITLEBK|Ustaw kolor tła wyświetlany w tytule kalendarza.|
|MCSC_TITLETEXT|Ustaw kolor używany do wyświetlania tekstu w tytule kalendarza.|
|MCSC_TRAILINGTEXT|Ustaw kolor używany do wyświetlania nagłówka i tekstu końcowego dnia. Nagłówki i dni końcowe to dni z poprzednich i kolejnych miesięcy, które pojawiają się w bieżącym kalendarzu.|

*ref*<br/>
Wartość COLORREF reprezentująca kolor, który zostanie ustawiony dla określonego obszaru kalendarza miesiąca.

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF, która reprezentuje poprzednie ustawienie koloru dla określonej części formantu kalendarza miesiąca, jeśli zakończy się pomyślnie. W przeciwnym razie wiadomość zwraca -1.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont

Ustawia czcionkę, która będzie używana jako formant kalendarza miesiąca podrzędnego daty i godziny.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*hFont ( hFont )*<br/>
Uchwyt do czcionki, która zostanie ustawiona.

*bRedraw*<br/>
Określa, czy formant powinien zostać ponownie narysowany natychmiast po ustawieniu czcionki. Ustawienie tego parametru na WARTOŚĆ TRUE powoduje, że formant ponownie rysuje się.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Jeśli używasz tego kodu, należy wprowadzić element `CDialog`członkowski klasy pochodnej o nazwie `CFont` *m_MonthFont* typu .

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle

Ustawia styl formantu kalendarza rozwijanego miesiąca skojarzonego z bieżącą kontrolą selektora daty i godziny.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Dwstyle*|[w] Nowy styl sterowania kalendarza miesiąca, który jest kombinacją bitową (OR) stylów sterowania kalendarzem miesiąca. Aby uzyskać więcej informacji, zobacz [Style sterowania kalendarzem miesiąca](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Wartość zwracana

Poprzedni styl formantu kalendarza rozwijanego miesiąca.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [DTM_SETMCSTYLE,](/windows/win32/Controls/dtm-setmcstyle) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_dateTimeCtrl*, która jest używana do programowego dostępu do kontroli selektora daty i godziny. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia kontrolkę selektora daty i godziny, aby wyświetlać numery tygodni, skrócone nazwy dni tygodnia i brak wskaźnika dzisiaj.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange

Ustawia minimalną i maksymalną dozwoloną liczbę czasów systemowych dla kontroli selektora daty i godziny.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange (pMinRange)*<br/>
Wskaźnik do [obiektu COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) zawierający najwcześniejszy czas `CDateTimeCtrl` dozwolony w obiekcie.

*pMaxRange (Polski)*<br/>
Wskaźnik do `COleDateTime` obiektu lub `CTime` obiektu zawierającego ostatni dozwolony `CDateTimeCtrl` czas w obiekcie.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC można określić `COleDateTime` `CTime` albo użycia. Jeśli `COleDateTime` obiekt ma stan NULL, zakres zostanie usunięty. Jeśli `CTime` wskaźnik lub `COleDateTime` wskaźnik ma wartość NULL, zakres zostanie usunięty.

### <a name="example"></a>Przykład

  Zobacz przykład [CDateTimeCtrl::GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime

Ustawia godzinę w formancie selektora daty i godziny.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Parametry

*czasNowy*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu zawierającego, do którego zostanie ustawiony formant.

*pCzasNowy*<br/>
W drugiej wersji powyżej wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu zawierającego czas, do którego formant zostanie ustawiony. W trzeciej wersji powyżej wskaźnik do [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury zawierającej czas, do którego formant zostanie ustawiony.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji `SetTime`MFC , można `COleDateTime` `CTime` użyć lub klas lub `SYSTEMTIME` można użyć struktury, aby ustawić informacje o czasie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)
