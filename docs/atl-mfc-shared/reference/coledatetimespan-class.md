---
title: COleDateTimeSpan, klasa
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317741"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan, klasa

Reprezentuje względny czas, przedział czasu.

## <a name="syntax"></a>Składnia

```
class COleDateTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimespan](#coledatetimespan)|Konstruuje `COleDateTimeSpan` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Generuje sformatowaną reprezentację `COleDateTimeSpan` ciągu obiektu.|
|[COleDateTimeSpan::GetDays](#getdays)|Zwraca część dnia zakresu, `COleDateTimeSpan` który reprezentuje ten obiekt.|
|[COleDateTimeSpan::GetHours](#gethours)|Zwraca część godziny zakresu, `COleDateTimeSpan` który reprezentuje ten obiekt.|
|[COleDateTimespan::GetMinutes](#getminutes)|Zwraca część minutową zakresu, który reprezentuje ten `COleDateTimeSpan` obiekt.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Zwraca drugą część zakresu, który reprezentuje ten `COleDateTimeSpan` obiekt.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Pobiera stan (ważność) `COleDateTimeSpan` tego obiektu.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Zwraca liczbę dni, `COleDateTimeSpan` które reprezentuje ten obiekt.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Zwraca liczbę godzin, `COleDateTimeSpan` które reprezentuje ten obiekt.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca liczbę minut, `COleDateTimeSpan` które reprezentuje ten obiekt.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca liczbę sekund, `COleDateTimeSpan` które reprezentuje ten obiekt.|
|[COleDateTimespan::SetDateTimespan](#setdatetimespan)|Ustawia wartość tego `COleDateTimeSpan` obiektu.|
|[COleDateTimespan::SetStatus](#setstatus)|Ustawia stan (ważność) `COleDateTimeSpan` tego obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[operator +, -](#operator_add_-)|Dodawanie, odejmowanie i `COleDateTimeSpan` zmienianie znaku dla wartości.|
|[operator +=, -=](#operator_add_eq_-_eq)|Dodaj i odejmij `COleDateTimeSpan` `COleDateTimeSpan` wartość od tej wartości.|
|[operator =](#operator_eq)|Kopiuje `COleDateTimeSpan` wartość.|
|[operator ==, <, <=](#coledatetimespan_relational_operators)|Porównaj `COleDateTimeSpan` dwie wartości.|
|[operator dwukrotnie](#operator_double)|Konwertuje `COleDateTimeSpan` tę wartość na **podwójną**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Zawiera podstawowe **double** `COleDateTimeSpan` dla tego obiektu.|
|[COleDateTimeSpan::m_status](#m_status)|Zawiera stan tego `COleDateTimeSpan` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTimeSpan`nie ma klasy podstawowej.

A `COleDateTimeSpan` utrzymuje czas w dniach.

`COleDateTimeSpan`jest używany z klasą towarzyszącą [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`hermetyzuje `DATE` typ danych automatyzacji OLE. `COleDateTime`reprezentuje wartości czasu bezwzględnego. Wszystkie `COleDateTime` obliczenia `COleDateTimeSpan` obejmują wartości. Relacja między tymi klasami jest analogiczna do tej między [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej `COleDateTime` `COleDateTimeSpan` informacji na temat i klas, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>Operatory relacyjne COleDateTimespan

Operatory porównawcze.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parametry

*dataSpan*<br/>
Do `COleDateTimeSpan` porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwie wartości daty/przedziału czasu i zwracają wartość TRUE, jeśli warunek jest spełniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Atlassert wystąpi, jeśli jeden operand jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimespan

Konstruuje `COleDateTimeSpan` obiekt.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*dblSpanSrc*<br/>
Liczba dni do skopiowania do `COleDateTimeSpan` nowego obiektu.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Wskaż wartości dnia i czasu, `COleDateTimeSpan` które mają zostać skopiowane do nowego obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory utworzyć nowe `COleDateTimeSpan` obiekty zainicjowane do określonej wartości. Krótki opis każdego z tych konstruktorów jest następujący:

- **COleDateTimespan( )** Konstruuje `COleDateTimeSpan` obiekt zainicjowany do 0.

- **COleDateTimespan(** `dblSpanSrc` **)** Konstruuje `COleDateTimeSpan` obiekt z wartości zmiennoprzecinkowej.

- **COleDateTimespan(** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** Konstruuje `COleDateTimeSpan` obiekt zainicjowany do określonych wartości liczbowych.

Stan nowego `COleDateTimeSpan` obiektu jest ustawiony na prawidłowy.

Aby uzyskać więcej informacji `COleDateTimeSpan` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Format

Generuje sformatowaną reprezentację `COleDateTimeSpan` ciągu obiektu.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*<br/>
Ciąg formatowania podobny `printf` do ciągu formatowania. Kody formatowania, poprzedzone`%`znakiem procentu ( `COleDateTimeSpan` ), są zastępowane przez odpowiedni składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Poniżej wymieniono wartość i `Format` znaczenie kodów formatowania:

- **%H** Godziny w bieżącym dniu

- **%M** Minuty w bieżącej godzinie

- **%S** Sekundy w bieżącej minucie

- **%%** Znak procentowy

Cztery kody formatów wymienione powyżej są jedynymi kodami akceptowanych przez format.

-

*Nid*<br/>
Identyfikator zasobu dla ciągu kontroli formatu.

### <a name="return-value"></a>Wartość zwracana

A, `CString` który zawiera sformatowaną wartość daty/przedziału czasu.

### <a name="remarks"></a>Uwagi

Wywołanie tych funkcji, aby utworzyć sformatowaną reprezentację wartości przedziału czasu. Jeśli stan tego `COleDateTimeSpan` obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określony przez IDS_INVALID_DATETIMESPAN zasobu ciągu.

Krótki opis formularzy dla tej funkcji jest następujący:

**Format(** *pFormat* **)**<br/>
Ten formularz formatuje wartość przy użyciu ciągu formatu zawierającego specjalne kody formatowania `printf`poprzedzone znakiem procentowym (%), jak w pliku . Ciąg formatowania jest przekazywany jako parametr do funkcji.

**Format(** *nID* **)**<br/>
Ten formularz formatuje wartość przy użyciu ciągu formatu zawierającego specjalne kody formatowania `printf`poprzedzone znakiem procentowym (%), jak w pliku . Ciąg formatowania jest zasobem. Identyfikator tego zasobu ciągu jest przekazywany jako parametr.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

Pobiera część dnia tej wartości daty/przedziału czasu.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część dnia tej wartości daty/przedziału czasu.

### <a name="remarks"></a>Uwagi

Zwracane wartości z tej funkcji wahają się od około - 3 615 000 do 3 615 000.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan::GetHours

Pobiera część godziny tej wartości daty/przedziału czasu.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część godzin tej wartości daty/przedziału czasu.

### <a name="remarks"></a>Uwagi

Zwracane wartości z tej funkcji wahają się od - 23 i 23.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimespan::GetMinutes

Pobiera część minutową tej wartości daty/przedziału czasu.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część minut tej wartości daty/przedziału czasu.

### <a name="remarks"></a>Uwagi

Zwracane wartości z tej funkcji wahają się od - 59 i 59.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds

Pobiera drugą część tej wartości daty/przedziału czasu.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część sekund tej wartości daty/przedziału czasu.

### <a name="remarks"></a>Uwagi

Zwracane wartości z tej funkcji wahają się od - 59 i 59.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus

Pobiera stan (ważność) `COleDateTimeSpan` tego obiektu.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Stan tej `COleDateTimeSpan` wartości.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest `DateTimeSpanStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleDateTimeSpan` klasie.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTimeSpan::valid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że `COleDateTimeSpan` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

Stan obiektu `COleDateTimeSpan` jest nieprawidłowy w następujących przypadkach:

- Jeśli ten obiekt doświadczył przepełnienia lub niedopełnienia podczas operacji przypisania arytmetycznego, `+=` a mianowicie lub `-=`.

- Jeśli do tego obiektu została przypisana nieprawidłowa wartość.

- Jeśli stan tego obiektu został jawnie `SetStatus`ustawiony na nieprawidłowy przy użyciu programu .

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Aby uzyskać więcej informacji `COleDateTimeSpan` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Pobiera tę wartość daty/przedziału czasu wyrażoną w dniach.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/przedziału czasu wyrażona w dniach. Mimo że ta funkcja jest prototypowana, aby zwrócić double, zawsze zwróci wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji wahają się od około - 3.65e6 i 3.65e6.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

Pobiera tę wartość daty/przedziału czasu wyrażoną w godzinach.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość data/przedział czasu wyrażona w godzinach. Mimo że ta funkcja jest prototypowana, aby zwrócić double, zawsze zwróci wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji wahają się od około - 8.77e7 i 8.77e7.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład [getTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

Pobiera tę wartość daty/przedziału czasu wyrażoną w minutach.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość data/przedział czasu wyrażona w minutach. Mimo że ta funkcja jest prototypowana, aby zwrócić double, zawsze zwróci wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji wahają się od około - 5.26e9 i 5.26e9.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład [getTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

Pobiera tę wartość daty/przedziału czasu wyrażoną w sekundach.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość data/przedział czasu wyrażona w sekundach. Mimo że ta funkcja jest prototypowana, aby zwrócić double, zawsze zwróci wartość całkowitą.

### <a name="remarks"></a>Uwagi

Zwracane wartości z tej funkcji wahają się od około - 3.16e11 do 3.16e11.

W przypadku innych funkcji, `COleDateTimeSpan` które kwerendy wartość obiektu, zobacz następujące funkcje elementu członkowskiego:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

### <a name="example"></a>Przykład

Zobacz przykład [getTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan::m_span

Podstawowa **podwójna** `COleDateTime` wartość dla tego obiektu.

```
double m_span;
```

### <a name="remarks"></a>Uwagi

Ta wartość wyraża datę/przedział czasu w dniach.

> [!CAUTION]
> Zmiana wartości w **podwójnym** elementem członkowskim danych `COleDateTimeSpan` spowoduje zmianę wartości tego obiektu. Nie zmienia stanu tego `COleDateTimeSpan` obiektu.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan::m_status

Typ dla tego elementu członkowskiego danych jest `DateTimeSpanStatus`typem wyliczonym, który jest zdefiniowany w `COleDateTimeSpan` klasie.

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Uwagi

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTimeSpan::valid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że `COleDateTimeSpan` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

Stan obiektu `COleDateTimeSpan` jest nieprawidłowy w następujących przypadkach:

- Jeśli ten obiekt doświadczył przepełnienia lub niedopełnienia podczas operacji przypisania arytmetycznego, `+=` a mianowicie lub `-=`.

- Jeśli do tego obiektu została przypisana nieprawidłowa wartość.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [setstatus](#setstatus).

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Ten element członkowski danych jest przeznaczony do zaawansowanych sytuacji programowania. Należy użyć wbudowanych funkcji członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dalsze ostrzeżenia dotyczące jawnego ustawiania tego elementu członkowskiego danych.

Aby uzyskać więcej informacji `COleDateTimeSpan` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::operator =

Kopiuje `COleDateTimeSpan` wartość.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Uwagi

Ten przeciążony operator przypisania kopiuje wartość daty `COleDateTimeSpan` źródłowej/zakresu czasu do tego obiektu.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::operator +, -

Dodawanie, odejmowanie i `COleDateTimeSpan` zmienianie znaku dla wartości.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Pierwsze dwa operatory umożliwiają dodawanie i odejmowanie wartości daty/przedziału czasu. Trzeci umożliwia zmianę znaku wartości daty/przedziału czasu.

Jeśli którykolwiek z argumentów ma wartość null, `COleDateTimeSpan` stan wartości wynikowej jest zerowy.

Jeśli którykolwiek z argumentów jest nieprawidłowy, a drugi nie ma `COleDateTimeSpan` wartości null, stan wynikowej wartości jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator +=, -=

Dodaj i odejmij `COleDateTimeSpan` `COleDateTimeSpan` wartość od tej wartości.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i odejmowanie wartości `COleDateTimeSpan` daty/zakresu czasu od tego obiektu. Jeśli którykolwiek z argumentów ma wartość null, `COleDateTimeSpan` stan wartości wynikowej jest zerowy.

Jeśli którykolwiek z argumentów jest nieprawidłowy, a drugi nie ma `COleDateTimeSpan` wartości null, stan wynikowej wartości jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::operator dwukrotnie

Konwertuje `COleDateTimeSpan` tę wartość na **podwójną**.

```
operator double() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wartość `COleDateTimeSpan` tej wartości jako zmiennoprzecinową liczbę dni.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimespan::SetDateTimespan

Ustawia wartość tej wartości daty/przedziału czasu.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Wskazać wartości zakresu daty i przedziału czasu, `COleDateTimeSpan` które mają zostać skopiowane do tego obiektu.

### <a name="remarks"></a>Uwagi

W przypadku funkcji, które `COleDateTimeSpan` kwerendy wartość obiektu, zobacz następujące funkcje członkowskie:

- [GetDays (GetDays)](#getdays)

- [GetHours (GetHours)](#gethours)

- [Minuty GetMinutes](#getminutes)

- [GetSeconds (GetSeconds)](#getseconds)

- [GetTotalDays (GetTotalDays)](#gettotaldays)

- [GetTotalGodziny](#gettotalhours)

- [GetTotalMinutes (Minuty)](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimespan::SetStatus

Ustawia stan (ważność) `COleDateTimeSpan` tego obiektu.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stan*<br/>
Nowa wartość stanu `COleDateTimeSpan` dla tego obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *Status* jest `DateTimeSpanStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleDateTimeSpan` klasie.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTimeSpan::valid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że `COleDateTimeSpan` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że `COleDateTimeSpan` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

   > [!CAUTION]
   > Ta funkcja jest dla zaawansowanych sytuacji programowania. Ta funkcja nie zmienia danych w tym obiekcie. Najczęściej będzie on używany do ustawiania stanu **na null** lub **nieprawidłowy.** Należy zauważyć, że operator przypisania[(operator =](#operator_eq)) i [SetDateTimeSpan](#setdatetimespan) ustawiają stan obiektu na podstawie wartości źródłowych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime, klasa](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
