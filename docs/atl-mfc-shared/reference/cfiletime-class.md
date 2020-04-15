---
title: CFileTime, klasa
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: bc9fe752898a5dfde2631352abd8c3cf5f8b378c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317890"
---
# <a name="cfiletime-class"></a>CFileTime, klasa

Ta klasa zawiera metody zarządzania wartościami daty i godziny skojarzonymi z plikiem.

## <a name="syntax"></a>Składnia

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Wywołanie tej funkcji statycznej, aby pobrać `CFileTime` obiekt, który reprezentuje bieżącą datę i godzinę systemu.|
|[CFileTime::GetTime](#gettime)|Wywołanie tej metody, aby `CFileTime` pobrać czas z obiektu.|
|[CFileTime::LocalToUTC](#localtoutc)|Wywołanie tej metody, aby przekonwertować czas pliku lokalnego na czas pliku na podstawie skoordynowanego czasu uniwersalnego (UTC).|
|[CFileTime::SetTime](#settime)|Wywołanie tej metody, aby ustawić `CFileTime` datę i godzinę przechowywane przez obiekt.|
|[CFileTime::UTCToLocal](#utctolocal)|Wywołanie tej metody, aby przekonwertować czas na podstawie skoordynowanego czasu uniwersalnego (UTC) do lokalnego czasu pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::operator -](#operator_-)|Ten operator jest używany do odejmowania na `CFileTime` lub `CFileTimeSpan` obiektu.|
|[CFileTime::operator !=](#operator_neq)|Ten operator porównuje `CFileTime` dwa obiekty dla nierówności.|
|[CFileTime::operator +](#operator_add)|Ten operator jest używany do `CFileTimeSpan` wykonywania dodawania na obiekcie.|
|[CFileTime::operator +=](#operator_add_eq)|Ten operator jest używany do `CFileTimeSpan` dodawania obiektu i przypisywania wyniku do bieżącego obiektu.|
|[CFileTime:operator&lt;](#operator_lt)|Ten operator porównuje `CFileTime` dwa obiekty, aby określić mniejsze.|
|[CFileTime:operator&lt;=](#operator_lt_eq)|Ten operator porównuje `CFileTime` dwa obiekty do określenia równości lub mniejsze.|
|[CFileTime::operator =](#operator_eq)|Operator przypisania.|
|[CFileTime::operator -=](#operator_-_eq)|Ten operator jest używany do wykonywania `CFileTimeSpan` odejmowania obiektu i przypisywania wyniku do bieżącego obiektu.|
|[CFileTime::operator ==](#operator_eq_eq)|Ten operator porównuje `CFileTime` dwa obiekty dla równości.|
|[CFileTime:operator&gt;](#operator_gt)|Ten operator porównuje `CFileTime` dwa obiekty, aby określić większe.|
|[CFileTime:operator&gt;=](#operator_gt_eq)|Ten operator porównuje `CFileTime` dwa obiekty do określenia równości lub większe.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::Day](#day)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które składają się na jeden dzień.|
|[CFileTime::Godzina](#hour)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną godzinę.|
|[CFileTime::Milisekunda](#millisecond)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną milisekundę.|
|[CFileTime::Minuta](#minute)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną minutę.|
|[CFileTime::Drugi](#second)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną sekundę.|
|[CFileTime::Tydzień](#week)|Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jeden tydzień.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody zarządzania wartościami daty i godziny skojarzonymi z tworzeniem, dostępem i modyfikacją plików. Metody i dane tej klasy są często `CFileTimeSpan` używane w połączeniu z obiektami, które dotyczą względnych wartości czasu.

Wartość daty i godziny jest przechowywana jako wartość 64-bitowa reprezentująca liczbę 100 interwałów nanosekund od 1 stycznia 1601. Jest to format skoordynowanego czasu uniwersalnego (UTC).

Następujące statyczne zmienne członkowskie są dostarczane w celu uproszczenia obliczeń:

|Zmienna elementu członkowskiego|Liczba interwałów 100 nanosekund|
|---------------------|-----------------------------------------|
|Milisekundy|10 000|
|Sekunda|Milisekunda \* 1000|
|Minuta|Drugi \* 60|
|Godzina|Minuta \* 60|
|Day|Godzina \* 24|
|Tydzień|Dzień \* 7.|

**Uwaga** Nie wszystkie systemy plików mogą rejestrować czas tworzenia i ostatniego dostępu, a nie wszystkie systemy plików rejestrują je w ten sam sposób. Na przykład w systemie plików Windows NT FAT czas tworzenia ma rozdzielczość 10 milisekund, czas zapisu ma rozdzielczość 2 sekund, a czas dostępu ma rozdzielczość 1 dzień (data dostępu). W systemie plików NTFS czas dostępu ma rozdzielczość 1 godzinę. Ponadto fat rejestruje czasy na dysku w czasie lokalnym, ale NTFS rejestruje czasy na dysku w utc. Aby uzyskać więcej informacji, zobacz [Czasy plików](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>CFileTime::CFileTime

Konstruktor.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Struktura [FILETIME.](/windows/win32/api/minwinbase/ns-minwinbase-filetime)

*nCzas*<br/>
Data i godzina wyrażona jako wartość 64-bitowa.

### <a name="remarks"></a>Uwagi

Obiekt `CFileTime` można utworzyć przy użyciu istniejącej `FILETIME` daty i godziny ze struktury lub wyrażonej jako wartość 64-bitowa (w formatach czasu lokalnego lub skoordynowanego czasu uniwersalnego (UTC). Domyślny konstruktor ustawia czas na 0.

## <a name="cfiletimeday"></a><a name="day"></a>CFileTime::Day

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które składają się na jeden dzień.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](#millisecond).

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Wywołanie tej funkcji statycznej, aby pobrać `CFileTime` obiekt, który reprezentuje bieżącą datę i godzinę systemu.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą datę i godzinę systemowej w formacie Skoordynowany czas uniwersalny (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>CFileTime::GetTime

Wywołanie tej metody, aby `CFileTime` pobrać czas z obiektu.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca datę i godzinę jako liczbę 64-bitową, która może być w formacie lokalnym lub koordynowanym czasie uniwersalnym (UTC).

## <a name="cfiletimehour"></a><a name="hour"></a>CFileTime::Godzina

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną godzinę.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](#millisecond).

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>CFileTime::LocalToUTC

Wywołanie tej metody, aby przekonwertować czas pliku lokalnego na czas pliku na podstawie skoordynowanego czasu uniwersalnego (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt zawierający czas w formacie UTC.

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::UTCToLocal](#utctolocal).

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>CFileTime::Milisekunda

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną milisekundę.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>CFileTime::Minuta

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jedną minutę.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](#millisecond).

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>CFileTime::operator -

Ten operator jest używany do odejmowania na `CFileTime` lub `CFileTimeSpan` obiektu.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt `CFileTimeSpan`.

*Ft*<br/>
Obiekt `CFileTime`.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt lub `CFileTimeSpan` obiekt reprezentujący wynik różnicy czasu między tymi dwoma obiektami.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>CFileTime::operator !=

Ten operator porównuje `CFileTime` dwa obiekty dla nierówności.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CFileTime` element nie jest równy obiektowi, w przeciwnym razie FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>CFileTime::operator +

Ten operator jest używany do `CFileTimeSpan` wykonywania dodawania na obiekcie.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt reprezentujący wynik oryginalnego czasu plus względny czas.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>CFileTime::operator +=

Ten operator jest używany do `CFileTimeSpan` dodawania obiektu i przypisywania wyniku do bieżącego obiektu.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiekt, reprezentujący wynik oryginalnego czasu plus względny czas.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>CFileTime:operator&lt;

Ten operator porównuje `CFileTime` dwa obiekty, aby określić mniejsze.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy (wcześniej w czasie) niż drugi, FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>CFileTime:operator&lt;=

Ten operator porównuje `CFileTime` dwa obiekty do określenia równości lub mniejsze.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy niż (wcześniej w czasie) lub równy drugiemu, w przeciwnym razie FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>CFileTime::operator =

Operator przypisania.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` zawierający nową godzinę i datę.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiekt.

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>CFileTime::operator -=

Ten operator jest używany do wykonywania `CFileTimeSpan` odejmowania obiektu i przypisywania wyniku do bieżącego obiektu.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt `CFileTimeSpan` zawierający względny czas odejmowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiekt.

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>CFileTime::operator ==

Ten operator porównuje `CFileTime` dwa obiekty dla równości.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe, w przeciwnym razie FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>CFileTime:operator&gt;

Ten operator porównuje `CFileTime` dwa obiekty, aby określić większe.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (później w czasie) niż drugi, w przeciwnym razie FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>CFileTime:operator&gt;=

Ten operator porównuje `CFileTime` dwa obiekty do określenia równości lub większe.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Obiekt `CFileTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (później w czasie) lub równy drugiemu, w przeciwnym razie FALSE.

## <a name="cfiletimesecond"></a><a name="second"></a>CFileTime::Drugi

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które składają się na jeden dzień.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](#millisecond).

## <a name="cfiletimesettime"></a><a name="settime"></a>CFileTime::SetTime

Wywołanie tej metody, aby ustawić `CFileTime` datę i godzinę przechowywane przez obiekt.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*nCzas*<br/>
Wartość 64-bitowa reprezentująca datę i godzinę w formacie lokalnym lub koordynowanym czasie uniwersalnym (UTC).

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>CFileTime::UTCToLocal

Wywołanie tej metody, aby przekonwertować czas na podstawie skoordynowanego czasu uniwersalnego (UTC) do lokalnego czasu pliku.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt zawierający czas w lokalnym formacie czasu pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>CFileTime::Tydzień

Element członkowski danych statycznych przechowujący liczbę interwałów 100 nanosekund, które tworzą jeden tydzień.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](#millisecond).

## <a name="see-also"></a>Zobacz też

[Filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan, klasa](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
