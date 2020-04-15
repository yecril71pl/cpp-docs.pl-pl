---
title: Klasa CMonthCalCtrl
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: da9d588811361d3dfd72d44d5b9ced8460d23936
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319753"
---
# <a name="cmonthcalctrl-class"></a>Klasa CMonthCalCtrl

Hermetyzuje funkcjonalność kontrolki kalendarza miesiąca.

## <a name="syntax"></a>Składnia

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Konstruuje `CMonthCalCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMonthCalCtrl::Utwórz](#create)|Tworzy formant kalendarza miesiąca i `CMonthCalCtrl` dołącza go do obiektu.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Pobiera szerokość obramowania bieżącego kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Pobiera liczbę kalendarzy wyświetlanych w formancie kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Pobiera informacje o kontroli kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Pobiera identyfikator kalendarza dla formantu kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::GetColor](#getcolor)|Pobiera kolor określonego obszaru kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Pobiera widok, który jest obecnie wyświetlany przez formant kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Pobiera czas systemowy wskazany przez aktualnie wybraną datę.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Pobiera pierwszy dzień tygodnia, które mają być wyświetlane w lewej kolumnie kalendarza.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Pobiera bieżącą maksymalną liczbę dni, którą można wybrać w formancie kalendarza miesiąca.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Pobiera maksymalną szerokość ciągu "Dzisiaj" dla kontroli kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Pobiera minimalny rozmiar wymagany do wyświetlenia kontroli kalendarza pełnego miesiąca w miesiącu.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Pobiera współczynnik przewijania dla kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Pobiera informacje o dacie reprezentujące wysokie i niskie limity wyświetlania formantu kalendarza miesiąca.|
|[CMonthCalCtrl::GetRange](#getrange)|Pobiera bieżące daty minimalne i maksymalne ustawione w formancie kalendarza miesiąca.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Pobiera informacje o dacie reprezentujące górne i dolne granice zakresu dat aktualnie wybranego przez użytkownika.|
|[CMonthCalCtrl::GetToday](#gettoday)|Pobiera informacje o dacie dla daty określonej jako "dzisiaj" dla kontroli kalendarza miesiąca.|
|[CMonthCalCtrl::HitTest](#hittest)|Określa, która sekcja kontrolki kalendarza miesiąca znajduje się w danym punkcie na ekranie.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem wieku.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem dekady.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem miesiąca.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Wskazuje, czy bieżący widok formantu kalendarza bieżącego miesiąca jest widokiem roku.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Ustawia szerokość obramowania bieżącego kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Ustawia domyślną szerokość obramowania kontrolki kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Ustawia identyfikator kalendarza dla kontroli kalendarza bieżącego miesiąca.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić widok wieku.|
|[CMonthCalCtrl::SetColor](#setcolor)|Ustawia kolor określonego obszaru kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić określony widok.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Ustawia aktualnie wybraną datę dla formantu kalendarza miesiąca.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Ustawia wyświetlanie dla dni w miesiącu kontrolki kalendarza.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Ustawia formant kalendarza bieżącego miesiąca na widok dekady.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Ustawia dzień tygodnia, który ma być wyświetlany w lewej kolumnie kalendarza.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Ustawia maksymalną liczbę dni, które można wybrać w formancie kalendarza miesiąca.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Ustawia szybkość przewijania dla kontrolki kalendarza miesiąca.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić widok miesiąca.|
|[CMonthCalCtrl::SetRange](#setrange)|Ustawia minimalne i maksymalne dozwolone daty dla kontroli kalendarza miesiąca.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Ustawia wybór dla formantu kalendarza miesiąca na dany zakres dat.|
|[CMonthCalCtrl::SetToday](#settoday)|Ustawia kontrolka kalendarza dla bieżącego dnia.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Ustawia formant kalendarza bieżącego miesiąca na widok roku.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Odświeża formant kalendarza miesiąca do jego minimalnego rozmiaru jednego miesiąca.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Dla bieżącego kontrolki kalendarza miesiąca oblicza najmniejszy prostokąt, który może zawierać wszystkie kalendarze, które mieszczą się w określonym prostokącie.|

## <a name="remarks"></a>Uwagi

Formant kalendarza miesiąca zapewnia użytkownikowi prosty interfejs kalendarza, z którego użytkownik może wybrać datę. Użytkownik może zmienić wyświetlanie, aby:

- Przewijanie do tyłu i do przodu, z miesiąca na miesiąc.

- Kliknięcie tekstu Dzisiaj w celu wyświetlenia bieżącego dnia (jeśli styl MCS_NOTODAY nie jest używany).

- Wybieranie miesiąca lub roku z wyskakującego menu.

Formant kalendarza miesiąca można dostosować, stosując różne style do obiektu podczas jego tworzenia. Style te są opisane w [stylach sterowania kalendarzem miesiąca](/windows/win32/Controls/month-calendar-control-styles) w panelu Windows SDK.

Formant kalendarza miesiąca może wyświetlać więcej niż jeden miesiąc i może wskazywać dni specjalne (takie jak dni wolne) przez pogrubienie daty.

Aby uzyskać więcej informacji na temat korzystania z formantu kalendarza miesiąca, zobacz [Korzystanie z CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl

Konstruuje `CMonthCalCtrl` obiekt.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `Create` po skonstruowaniu obiektu.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Utwórz

Tworzy formant kalendarza miesiąca i `CMonthCalCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa kombinację stylów systemu Windows zastosowanych do formantu kalendarza miesiąca. Aby uzyskać więcej informacji na temat stylów, zobacz [Style sterowania kalendarzem miesiąca](/windows/win32/Controls/month-calendar-control-styles) w programie Windows SDK.

*Rect*<br/>
Odwołanie do struktury [RECT.](/previous-versions/dd162897\(v=vs.85\)) Zawiera położenie i rozmiar formantu kalendarza miesiąca.

*Pt*<br/>
Odwołanie do [point](/previous-versions/dd162805\(v=vs.85\)) struktury, która identyfikuje lokalizację kontrolki kalendarza miesiąca.

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, który jest nadrzędnym oknie kontrolki kalendarza miesiąca. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu kontrolki kalendarza miesiąca.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tworzenie formantu kalendarza miesiąca w dwóch krokach:

1. Wywołanie [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) `CMonthCalCtrl` do konstruowania obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, która tworzy formant kalendarza miesiąca i dołącza go do `CMonthCalCtrl` obiektu.

Podczas wywoływania `Create`typowe formanty są inicjowane. Wersja, `Create` którą dzwonisz określa, jak jest ona dopasowywania:

- Aby MFC automatycznie rozmiar formantu do jednego miesiąca, wywołać zastąpienie, który używa *pt* parametru.

- Aby samodzielnie rozmiar formantu, wywołać zastąpienie tej funkcji, która używa parametru *rect.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder

Pobiera szerokość obramowania bieżącego kontrolki kalendarza miesiąca.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość obramowania formantu w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCALENDARBORDER,](/windows/win32/Controls/mcm-getcalendarborder) który jest opisany w windows SDK.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount

Pobiera liczbę kalendarzy wyświetlanych w formancie kalendarza bieżącego miesiąca.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba kalendarzy aktualnie wyświetlanych w formancie kalendarza miesiąca. Maksymalna dozwolona liczba kalendarzy wynosi 12.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat MCM_GETCALENDARCOUNT,](/windows/win32/Controls/mcm-getcalendarcount) który jest opisany w windows SDK.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo

Pobiera informacje o kontroli kalendarza bieżącego miesiąca.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pmcGridInfo*|[na zewnątrz] Wskaźnik do struktury [MCGRIDINFO,](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) która odbiera informacje o kontroli kalendarza bieżącego miesiąca. Wywołujący jest odpowiedzialny za przydzielanie i inicjowanie tej struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat MCM_GETCALENDARGRIDINFO,](/windows/win32/Controls/mcm-getcalendargridinfo) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `GetCalendarGridInfo` używa metody do pobierania daty kalendarza, który jest wyświetlany w formancie kalendarza bieżącego miesiąca.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID

Pobiera identyfikator kalendarza dla formantu kalendarza bieżącego miesiąca.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna ze stałych [identyfikatorów kalendarza.](/windows/win32/Intl/calendar-identifiers)

### <a name="remarks"></a>Uwagi

Identyfikator kalendarza oznacza kalendarz specyficzny dla regionu, taki jak kalendarze gregoriański (zlokalizowane), japoński lub hidżryjski. Aplikacja może używać identyfikatora kalendarza, który ma różne funkcje obsługi języka.

Ta metoda wysyła [komunikat MCM_GETCALID,](/windows/win32/Controls/mcm-getcalid) który jest opisany w windows SDK.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor

Pobiera kolor obszaru obszaru kontrolki kalendarza miesiąca określonej przez *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Region kontrolki kalendarza miesiąca, z którego pobierany jest kolor. Aby uzyskać listę wartości, zobacz *parametr nRegion* [w pliku SetColor](#setcolor).

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) określająca kolor skojarzony z częścią formantu kalendarza miesiąca, jeśli zakończy się pomyślnie. W przeciwnym razie ta funkcja elementu członkowskiego zwraca wartość -1.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView

Pobiera widok, który jest obecnie wyświetlany przez formant kalendarza bieżącego miesiąca.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący widok, który jest wskazywany przez jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|MCMV_MONTH|Widok miesięczny|
|MCMV_YEAR|Widok roczny|
|MCMV_DECADE|Widok dekady|
|MCMV_CENTURY|Widok stulecia|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykładowy kod raportów, które wyświetlą formant kalendarza miesiąca aktualnie wyświetlane.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel

Pobiera czas systemowy wskazany przez aktualnie wybraną datę.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime (refDateTime)*<br/>
Odwołanie do [obiektu COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime.](../../atl-mfc-shared/reference/ctime-class.md) Odbiera bieżący czas.

*pDateTime*<br/>
Wskaźnik do struktury [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która otrzyma aktualnie wybrane informacje o dacie. Ten parametr musi być prawidłowym adresem i nie może być null.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; otherwize 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)komunikatu Win32, zgodnie z opisem w windows SDK.

> [!NOTE]
> Ta funkcja elementu członkowskiego kończy się niepowodzeniem, jeśli ustawiona jest MCS_MULTISELECT stylu.

W implementacji MFC `GetCurSel`, można `COleDateTime` określić `CTime` użycie, użycie `SYSTEMTIME` lub użycie struktury.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek

Pobiera pierwszy dzień tygodnia, które mają być wyświetlane w lewej kolumnie kalendarza.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbLocal (Polski)*<br/>
Wskaźnik do wartości BOOL. Jeśli wartość nie jest równa zero, ustawienie formantu nie jest zgodne z ustawieniem w panelu sterowania.

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita reprezentująca pierwszy dzień tygodnia. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat tego, co reprezentują te liczby całkowite.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)komunikatu Win32, zgodnie z opisem w windows SDK. Dni tygodnia są reprezentowane jako liczby całkowite w następujący sposób.

|Wartość|Dzień tygodnia|
|-----------|---------------------|
|0|Monday|
|1|Tuesday|
|2|Środa|
|3|Thursday|
|4|Piątek|
|5|Sobota|
|6|Niedziela|

### <a name="example"></a>Przykład

  Zobacz przykład [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount

Pobiera bieżącą maksymalną liczbę dni, którą można wybrać w formancie kalendarza miesiąca.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita reprezentująca całkowitą liczbę dni, które można wybrać dla formantu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)komunikatu Win32, zgodnie z opisem w windows SDK. Ta funkcja elementu członkowskiego służy do formantów z zestawem stylów MCS_MULTISELECT.

### <a name="example"></a>Przykład

  Zobacz przykład [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth

Pobiera maksymalną szerokość ciągu "Dzisiaj" dla kontroli kalendarza bieżącego miesiąca.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość ciągu "Dzisiaj" w pikselach.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu `GetMaxTodayWidth` pokazuje metodę.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Uwagi

Użytkownik może powrócić do bieżącej daty, klikając ciąg "Dzisiaj", który jest wyświetlany w dolnej części kontrolki kalendarza miesiąca. Ciąg "Dzisiaj" zawiera tekst etykiety i tekst daty.

Ta metoda wysyła komunikat [MCM_GETMAXTODAYWIDTH,](/windows/win32/Controls/mcm-getmaxtodaywidth) który jest opisany w windows SDK.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect

Pobiera minimalny rozmiar wymagany do wyświetlenia kontroli kalendarza pełnego miesiąca w miesiącu.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Parametry

*pRect*<br/>
Wskaźnik do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która otrzyma ograniczone informacje prostokąta. Ten parametr musi być prawidłowym adresem i nie może być null.

### <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia ta funkcja elementu `lpRect` członkowskiego zwraca nonzero i odbiera odpowiednie informacje ograniczające. Jeśli nie powiedzie się, funkcja elementu członkowskiego zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta

Pobiera współczynnik przewijania dla kontrolki kalendarza miesiąca.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Wartość zwracana

Szybkość przewijania dla kontrolki kalendarza miesiąca. Szybkość przewijania to liczba miesięcy, przez które formant przesuwa jego wyświetlanie, gdy użytkownik kliknie przycisk przewijania raz.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange

Pobiera informacje o dacie reprezentujące wysokie i niskie limity wyświetlania formantu kalendarza miesiąca.

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>Parametry

*refMinRange (rozmieszczenie rozmnażeń)*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu zawierającego minimalną dozwoloną datę.

*refMaxRange (rozmieszczenie) refMaxRange*<br/>
Odwołanie do `COleDateTime` obiektu `CTime` lub obiektu zawierającego maksymalną dozwoloną datę.

*pMinRange (pMinRange)*<br/>
Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najniższym końcu zakresu.

*pMaxRange (Polski)*<br/>
Wskaźnik do `SYSTEMTIME` struktury zawierającej datę na najwyższym końcu zakresu.

*Dwflags*<br/>
Wartość określająca zakres limitów zakresu do pobrania. Ta wartość musi być jedną z następujących wartości.

|Wartość|Znaczenie|
|-----------|-------------|
|GMR_DAYSTATE|Uwzględnij poprzednie i końcowe miesiące widocznego zakresu, które są wyświetlane tylko częściowo.|
|GMR_VISIBLE|Uwzględnij tylko te miesiące, które są w całości wyświetlane.|

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita reprezentująca zakres w miesiącach, łączony przez dwa limity wskazane przez *refMinRange* i *refMaxRange* w pierwszej i drugiej wersji lub *pMinRange* i *pMaxRange* w trzeciej wersji.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `GetMonthRange`, można `COleDateTime` określić `CTime` użycie, `SYSTEMTIME` użycie lub użycie struktury.

### <a name="example"></a>Przykład

  Zobacz przykład [CMonthCalCtrl::SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange

Pobiera bieżące daty minimalne i maksymalne ustawione w formancie kalendarza miesiąca.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*pMinRange (pMinRange)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najniższym końcu zakresu.

*pMaxRange (Polski)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najwyższym końcu zakresu.

### <a name="return-value"></a>Wartość zwracana

Dword, który może być zero (nie limity są ustawione) lub kombinacja następujących wartości, które określają informacje o limicie.

|Wartość|Znaczenie|
|-----------|-------------|
|GDTR_MAX|Maksymalny limit jest ustawiony dla formantu; *pMaxRange* jest prawidłowy i zawiera obowiązujące informacje o dacie.|
|GDTR_MIN|Minimalny limit jest ustawiony dla formantu; *pMinRange* jest prawidłowy i zawiera obowiązujące informacje o dacie.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `GetRange`, można `COleDateTime` określić `CTime` użycie, użycie `SYSTEMTIME` lub użycie struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange

Pobiera informacje o dacie reprezentujące górne i dolne granice zakresu dat aktualnie wybranego przez użytkownika.

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Parametry

*refMinRange (rozmieszczenie rozmnażeń)*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu zawierającego minimalną dozwoloną datę.

*refMaxRange (rozmieszczenie) refMaxRange*<br/>
Odwołanie do `COleDateTime` obiektu `CTime` lub obiektu zawierającego maksymalną dozwoloną datę.

*pMinRange (pMinRange)*<br/>
Wskaźnik do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najniższym końcu zakresu.

*pMaxRange (Polski)*<br/>
Wskaźnik do `SYSTEMTIME` struktury zawierającej datę na najwyższym końcu zakresu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)komunikatu Win32, zgodnie z opisem w windows SDK. `GetSelRange`zakończy się niepowodzeniem, jeśli zostanie zastosowany do formantu kalendarza miesiąca, który nie używa stylu MCS_MULTISELECT.

W implementacji MFC `GetSelRange`, można `COleDateTime` określić `CTime` użycie, `SYSTEMTIME` użycie lub użycie struktury.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday

Pobiera informacje o dacie dla daty określonej jako "dzisiaj" dla kontroli kalendarza miesiąca.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Parametry

*refDateTime (refDateTime)*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu wskazując bieżącego dnia.

*pDateTime*<br/>
Wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która otrzyma informacje o dacie. Ten parametr musi być prawidłowym adresem i nie może być null.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `GetToday`, można `COleDateTime` określić `CTime` użycie, użycie `SYSTEMTIME` lub użycie struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest

Określa, który formant kalendarza miesiąca, jeśli istnieje, znajduje się w określonej pozycji.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Parametry

*pMCHitTest (pMCHitTest)*<br/>
Wskaźnik do struktury [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) zawierający punkty testowania trafień dla kontroli kalendarza miesiąca.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD. Równa element członkowski **uHit** `MCHITTESTINFO` struktury.

### <a name="remarks"></a>Uwagi

`HitTest`wykorzystuje strukturę, `MCHITTESTINFO` która zawiera informacje o teście trafień.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView

Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem wieku.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżący widok jest widokiem wieku; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) który jest opisany w windows SDK. Jeśli ten komunikat zwraca MCMV_CENTURY, ta metoda zwraca wartość TRUE.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView

Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem dekady.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżący widok jest widokiem dekady; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) który jest opisany w windows SDK. Jeśli ten komunikat zwraca MCMV_DECADE, ta metoda zwraca wartość TRUE.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView

Wskazuje, czy bieżący widok bieżącego kontrolki kalendarza miesiąca jest widokiem miesiąca.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżący widok jest widokiem miesiąca; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) który jest opisany w windows SDK. Jeśli ten komunikat zwraca MCMV_MONTH, ta metoda zwraca wartość TRUE.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView

Wskazuje, czy bieżący widok formantu kalendarza bieżącego miesiąca jest widokiem roku.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżący widok jest widokiem roku; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) który jest opisany w windows SDK. Jeśli ten komunikat zwraca MCMV_YEAR, ta metoda zwraca wartość TRUE.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder

Ustawia szerokość obramowania bieżącego kontrolki kalendarza miesiąca.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*cxyBorder ( cxyBorder )*|[w] Szerokość obramowania w pikselach.|

### <a name="remarks"></a>Uwagi

Jeśli ta metoda powiedzie się, szerokość obramowania jest ustawiona na *cxyBorder* parametru. W przeciwnym razie szerokość obramowania jest resetowana do wartości domyślnej określonej przez bieżący [motyw](/windows/win32/Controls/visual-styles-overview)lub zero, jeśli motywy nie są używane.

Ta metoda wysyła komunikat [MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia szerokość obramowania kontrolki kalendarza miesiąca na osiem pikseli. Użyj [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) metody, aby ustalić, czy ta metoda powiodła się.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault

Ustawia domyślną szerokość obramowania kontrolki kalendarza bieżącego miesiąca.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Uwagi

Szerokość obramowania jest ustawiona na wartość domyślną określoną przez bieżący [motyw](/windows/win32/Controls/visual-styles-overview)lub zero, jeśli motywy nie są używane.

Ta metoda wysyła komunikat [MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) który jest opisany w windows SDK.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID

Ustawia identyfikator kalendarza dla kontroli kalendarza bieżącego miesiąca.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*kalid*|[w] Jedna ze stałych [identyfikatorów kalendarza.](/windows/win32/Intl/calendar-identifiers)|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Identyfikator kalendarza określa kalendarz specyficzny dla regionu, taki jak kalendarze gregoriański (zlokalizowane), japoński lub hidżry. Użyj `SetCalID` tej metody, aby wyświetlić kalendarz określony przez parametr *calid,* jeśli na komputerze są zainstalowane ustawienia regionalne zawierające kalendarz.

Ta metoda wysyła [komunikat MCM_SETCALID,](/windows/win32/Controls/mcm-setcalid) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia kontrolki kalendarza miesiąca do wyświetlania kalendarza ery cesarza japońskiego. Metoda `SetCalID` powiedzie się tylko wtedy, gdy ten kalendarz jest zainstalowany na komputerze.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView

Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić widok wieku.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody, aby `MCMV_CENTURY`ustawić widok na , który reprezentuje widok wieku.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor

Ustawia kolor określonego obszaru kontrolki kalendarza miesiąca.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Parametry

*nRegion*<br/>
Wartość całkowita określająca kolor kalendarza miesiąca do ustawienia. Ta wartość może być jedną z następujących czynności.

|Wartość|Znaczenie|
|-----------|-------------|
|MCSC_BACKGROUND|Kolor tła wyświetlany między miesiącami.|
|MCSC_MONTHBK|Kolor tła wyświetlany w ciągu miesiąca.|
|MCSC_TEXT|Kolor używany do wyświetlania tekstu w ciągu miesiąca.|
|MCSC_TITLEBK|Kolor tła wyświetlany w tytule kalendarza.|
|MCSC_TITLETEXT|Kolor używany do wyświetlania tekstu w tytule kalendarza.|
|MCSC_TRAILINGTEXT|Kolor używany do wyświetlania nagłówka i tekstu końcowego dnia. Nagłówki i dni końcowe to dni z poprzednich i kolejnych miesięcy, które pojawiają się w bieżącym kalendarzu.|

*ref*<br/>
Wartość COLORREF dla nowego ustawienia koloru dla określonej części formantu kalendarza miesiąca.

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF, która reprezentuje poprzednie ustawienie koloru dla określonej części formantu kalendarza miesiąca, jeśli zakończy się pomyślnie. W przeciwnym razie ten komunikat zwraca -1.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView

Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić określony widok.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwNewWidok*|[w] Jedna z następujących wartości, która określa widok miesięczny, roczny, dekadę lub wiek.<br /><br /> MCMV_MONTH: Widok miesięczny<br /><br /> MCMV_YEAR: Widok roczny<br /><br /> MCMV_DECADE: Widok dekady<br /><br /> MCMV_CENTURY: Widok stulecia|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [MCM_SETCURRENTVIEW,](/windows/win32/Controls/mcm-setcurrentview) który jest opisany w windows SDK.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel

Ustawia aktualnie wybraną datę dla formantu kalendarza miesiąca.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime (refDateTime)*<br/>
Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) lub [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu wskazującego aktualnie wybrany formant kalendarza miesiąca.

*pDateTime*<br/>
Wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która zawiera datę, która ma być ustawiona jako bieżące zaznaczenie.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `SetCurSel`, można `COleDateTime` określić `CTime` użycie, użycie `SYSTEMTIME` lub użycie struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl::SetDayState

Ustawia wyświetlanie dla dni w miesiącu kontrolki kalendarza.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Parametry

*nMiony*<br/>
Wartość wskazująca, ile elementów znajduje się w tablicy, na którą wskazuje *pStates.*

*pPaństwa*<br/>
Wskaźnik do [tablicy MONTHDAYSTATE](/windows/win32/Controls/monthdaystate) wartości, które określają, jak formant kalendarza miesiąca będzie rysowany każdego dnia na ekranie. Typ danych MONTHDAYSTATE jest polem bitowym, w którym każdy bit (od 1 do 31) reprezentuje stan dnia w miesiącu. Jeśli bit jest włączony, odpowiedni dzień będzie wyświetlany pogrubioną czcionką; w przeciwnym razie będzie wyświetlany bez nacisku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView

Ustawia formant kalendarza bieżącego miesiąca na widok dekady.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody, aby `MCMV_DECADE`ustawić widok na , który reprezentuje widok dekady.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek

Ustawia dzień tygodnia, który ma być wyświetlany w lewej kolumnie kalendarza.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Parametry

*Dzień iDay*<br/>
Wartość całkowita reprezentująca dzień ma być ustawiona jako pierwszy dzień tygodnia. Ta wartość musi być jedną z liczb dziennych. Opis numerów dni można znaleźć w [opisie](#getfirstdayofweek) numerów dni.

*lpnStar*<br/>
Wskaźnik do liczby całkowitej wskazujący pierwszy dzień poprzedniego tygodnia.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli poprzedni pierwszy dzień tygodnia jest ustawiony na wartość inną niż wartość LOCALE_IFIRSTDAYOFWEEK, która jest dniem wskazanym w ustawieniu panelu sterowania. W przeciwnym razie ta funkcja zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount

Ustawia maksymalną liczbę dni, które można wybrać w formancie kalendarza miesiąca.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Parametry

*Nmax*<br/>
Wartość, która będzie ustawiona na reprezentującą maksymalną liczbę wybranych dni.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta

Ustawia szybkość przewijania dla kontrolki kalendarza miesiąca.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Parametry

*iDelta ( iDelta )*<br/>
Liczba miesięcy, które mają być ustawione jako szybkość przewijania formantu. Jeśli ta wartość wynosi zero, delta miesiąca jest resetowana do wartości domyślnej, czyli liczby miesięcy wyświetlanych w formancie.

### <a name="return-value"></a>Wartość zwracana

Poprzedni współczynnik przewijania. Jeśli szybkość przewijania nie została wcześniej ustawiona, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView

Ustawia formant kalendarza bieżącego miesiąca, aby wyświetlić widok miesiąca.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody, aby ustawić widok na MCMV_MONTH, który reprezentuje widok miesiąca.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_monthCalCtrl`zmienną , która jest używana do programowego dostępu do formantu kalendarza miesiąca. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia formant kalendarza miesiąca, aby wyświetlić widoki miesiąca, roku, dekady i wieku.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange

Ustawia minimalne i maksymalne dopuszczalne daty dla kontroli kalendarza miesiąca.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange (pMinRange)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najniższym końcu zakresu.

*pMaxRange (Polski)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub `SYSTEMTIME` struktury zawierającej datę na najwyższym końcu zakresu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `SetRange`, można `COleDateTime` określić `CTime` użycie, `SYSTEMTIME` użycie lub użycie struktury.

### <a name="example"></a>Przykład

  Zobacz przykład [CMonthCalCtrl::GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange

Ustawia wybór dla formantu kalendarza miesiąca na dany zakres dat.

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Parametry

*pMinRange (pMinRange)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zawierającej datę na najniższym końcu zakresu.

*pMaxRange (Polski)*<br/>
Wskaźnik do `COleDateTime` obiektu, `CTime` obiektu lub `SYSTEMTIME` struktury zawierającej datę na najwyższym końcu zakresu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)komunikatu Win32, zgodnie z opisem w windows SDK. W implementacji MFC `SetSelRange`, można `COleDateTime` określić `CTime` użycie, `SYSTEMTIME` użycie lub użycie struktury.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday

Ustawia kontrolka kalendarza dla bieżącego dnia.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Parametry

*refDateTime (refDateTime)*<br/>
Odwołanie do [obiektu COleDateTime,](../../atl-mfc-shared/reference/coledatetime-class.md) który zawiera bieżącą datę.

*pDateTime*<br/>
W drugiej wersji wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu zawierającego bieżące informacje o dacie. W trzeciej wersji: wskaźnik do [struktury SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która zawiera bieżące informacje o dacie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)komunikatu Win32, zgodnie z opisem w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CMonthCalCtrl::GetToday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView

Ustawia formant kalendarza bieżącego miesiąca na widok roku.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa [CMonthCalCtrl::SetCurrentView](#setcurrentview) metody, aby ustawić widok na MCMV_YEAR, który reprezentuje widok roczny.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq

Wyświetla kontrolka kalendarza miesiąca do minimalnego rozmiaru wyświetlanego w ciągu jednego miesiąca.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Parametry

*bMalusz*<br/>
Określa, czy formant ma zostać przemalowany. Domyślnie wartość TRUE. Jeśli FAŁD, nie występuje ponowne malowanie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli formant kalendarza miesiąca jest do minimum dopasowywać; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie `SizeMinReq` pomyślnie wyświetla kontrolę całego kalendarza miesiąca dla kalendarza jednego miesiąca.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin

Dla bieżącego kontrolki kalendarza miesiąca oblicza najmniejszy prostokąt, który może zawierać wszystkie kalendarze, które mieszczą się w określonym prostokącie.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Lprect*|[w] Wskaźnik do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która definiuje prostokąt, który zawiera żądaną liczbę kalendarzy.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [RECT,](/previous-versions/dd162897\(v=vs.85\)) która definiuje prostokąt, którego rozmiar jest mniejszy lub równy prostokątowi zdefiniowanemu przez parametr *lpRect.*

### <a name="remarks"></a>Uwagi

Ta metoda oblicza, ile kalendarzy może zmieścić się w prostokącie określonym przez parametr *lpRect,* a następnie zwraca najmniejszy prostokąt, który może zawierać tę liczbę kalendarzy. W efekcie ta metoda zmniejsza określony prostokąt, aby dokładnie dopasować żądaną liczbę kalendarzy.

Ta metoda wysyła komunikat [MCM_SIZERECTTOMIN,](/windows/win32/Controls/mcm-sizerecttomin) który jest opisany w windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)
