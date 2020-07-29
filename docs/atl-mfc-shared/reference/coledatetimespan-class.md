---
title: Klasa COleDateTimeSpan
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
ms.openlocfilehash: a3a59971ec57378aee2ec4f65f221b96c46300b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219108"
---
# <a name="coledatetimespan-class"></a>Klasa COleDateTimeSpan

Reprezentuje czas względny, przedział czasu.

## <a name="syntax"></a>Składnia

```
class COleDateTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Konstruuje `COleDateTimeSpan` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan:: format](#format)|Generuje sformatowaną reprezentację obiektu w postaci ciągu `COleDateTimeSpan` .|
|[COleDateTimeSpan:: GetDays](#getdays)|Zwraca część dnia zakresu, którą reprezentuje ten `COleDateTimeSpan` obiekt.|
|[COleDateTimeSpan:: getgodz.](#gethours)|Zwraca część godziny z zakresu `COleDateTimeSpan` reprezentowanego przez ten obiekt.|
|[COleDateTimeSpan:: getmin](#getminutes)|Zwraca część minuty z zakresu `COleDateTimeSpan` reprezentowanego przez ten obiekt.|
|[COleDateTimeSpan:: getSeconds](#getseconds)|Zwraca drugą część zakresu reprezentowanego przez ten `COleDateTimeSpan` obiekt.|
|[COleDateTimeSpan:: GetStatus](#getstatus)|Pobiera stan (ważność) tego `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Zwraca liczbę dni, przez którą `COleDateTimeSpan` reprezentuje ten obiekt.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Zwraca liczbę godzin `COleDateTimeSpan` reprezentowanego przez ten obiekt.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca liczbę minut `COleDateTimeSpan` reprezentowanego przez ten obiekt.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca liczbę sekund, przez jaką ten `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Ustawia wartość tego `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan:: SetStatus](#setstatus)|Ustawia stan (ważność) tego `COleDateTimeSpan` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[operator +,-](#operator_add_-)|Dodawanie, odejmowanie i zmiana znaku dla `COleDateTimeSpan` wartości.|
|[operator + =,-=](#operator_add_eq_-_eq)|Dodaj i Odejmij `COleDateTimeSpan` wartość z tej `COleDateTimeSpan` wartości.|
|[operator =](#operator_eq)|Kopiuje `COleDateTimeSpan` wartość.|
|[operator = =, <, <=](#coledatetimespan_relational_operators)|Porównaj dwie `COleDateTimeSpan` wartości.|
|[operator Double](#operator_double)|Konwertuje tę `COleDateTimeSpan` wartość na **`double`** .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan:: m_span](#m_span)|Zawiera podstawową **`double`** dla tego `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan:: m_status](#m_status)|Zawiera stan tego `COleDateTimeSpan` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTimeSpan`nie ma klasy bazowej.

`COleDateTimeSpan`Czas w dniach.

`COleDateTimeSpan`jest używany z klasą pomocnika [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`hermetyzuje `DATE` Typ danych automatyzacji OLE. `COleDateTime`reprezentuje bezwzględne wartości czasu. Wszystkie `COleDateTime` obliczenia obejmują `COleDateTimeSpan` wartości. Relacja między tymi klasami jest analogiczna do jednego z [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej informacji na `COleDateTime` temat `COleDateTimeSpan` klas i, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime. h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>Operatory relacyjne COleDateTimeSpan

Operatory porównania.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parametry

*dateSpan*<br/>
`COleDateTimeSpan`Do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwie wartości typu Data/godzina i zwracają wartość TRUE, jeśli warunek ma wartość true. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> ATLASSERT wystąpi, jeśli oba operandy są nieprawidłowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan

Konstruuje `COleDateTimeSpan` obiekt.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*dblSpanSrc*<br/>
Liczba dni, które mają zostać skopiowane do nowego `COleDateTimeSpan` obiektu.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Wskaż wartości daty i godziny, które mają zostać skopiowane do nowego `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleDateTimeSpan` obiekty zainicjowane do określonej wartości. Poniżej znajduje się krótki opis każdego z następujących konstruktorów:

- **COleDateTimeSpan ()** Konstruuje `COleDateTimeSpan` obiekt zainicjowany do 0.

- **COleDateTimeSpan (** `dblSpanSrc` **)** konstruuje `COleDateTimeSpan` obiekt z wartości zmiennoprzecinkowej.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** konstruuje `COleDateTimeSpan` obiekt zainicjowany do określonych wartości liczbowych.

Stan nowego `COleDateTimeSpan` obiektu jest ustawiony na prawidłowy.

Aby uzyskać więcej informacji na temat granic dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan:: format

Generuje sformatowaną reprezentację obiektu w postaci ciągu `COleDateTimeSpan` .

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*<br/>
Ciąg formatowania podobny do `printf` ciągu formatowania. Kody formatowania poprzedzone znakiem procentu ( `%` ) są zastępowane przez odpowiedni `COleDateTimeSpan` składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Poniżej przedstawiono wartość i znaczenie kodów formatowania dla programu `Format` :

- **% H** Godz. w bieżącym dniu

- **% M** Minuty w bieżącej godzinie

- **% S** Sekundy w bieżącej minucie

- **%%** Znak procentu

Cztery kody formatu wymienione powyżej są jedynymi kodami, które będą akceptowane przez format.

-

*nID*<br/>
Identyfikator zasobu dla ciągu sterującego formatu.

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera sformatowaną wartość daty/zakresu czasu.

### <a name="remarks"></a>Uwagi

Wywołaj te funkcje, aby utworzyć sformatowaną reprezentację wartości zakresu czasu. Jeśli stan tego `COleDateTimeSpan` obiektu ma wartość null, zwracana wartość jest ciągiem pustym. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określany przez zasób ciągu IDS_INVALID_DATETIMESPAN.

Poniżej znajduje się krótki opis formularzy dla tej funkcji:

**Format (** *pFormat* **)**<br/>
Ten formularz służy do formatowania wartości przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, poprzedzone znakiem procentu (%), jak w `printf` . Ciąg formatowania jest przenoszona jako parametr do funkcji.

**Format (** *NID* **)**<br/>
Ten formularz służy do formatowania wartości przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, poprzedzone znakiem procentu (%), jak w `printf` . Ciąg formatowania jest zasobem. Identyfikator tego zasobu ciągu jest przekazaniem jako parametr.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan:: GetDays

Pobiera część dnia z tej wartości daty/godziny.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część dnia tej wartości daty/godziny.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w zakresie od około 3 615 000 do 3 615 000.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan:: getgodz.

Pobiera część godziny z tej wartości daty/godziny.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część godzin tej wartości daty/godziny.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w zakresie od-23 do 23.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan:: getmin

Pobiera część minuty tej wartości daty/godziny.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część minut tej wartości daty/godziny.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w zakresie od-59 do 59.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan:: getSeconds

Pobiera drugą część tej wartości daty/zakresu czasu.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część sekund tej wartości typu Data/godzina.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w zakresie od-59 do 59.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan:: GetStatus

Pobiera stan (ważność) tego `COleDateTimeSpan` obiektu.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Stan tej `COleDateTimeSpan` wartości.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowana przez `DateTimeSpanStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleDateTimeSpan` klasie.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTimeSpan::valid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że ten `COleDateTimeSpan` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTimeSpan` obiektu jest nieprawidłowy w następujących przypadkach:

- Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji przypisywania arytmetycznego, mianowicie `+=` lub `-=` .

- Jeśli nieprawidłowa wartość została przypisana do tego obiektu.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu `SetStatus` .

Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowe, zobacz [COleDateTimeSpan:: operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan:: operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Aby uzyskać więcej informacji na temat granic dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Pobiera wartość daty/zakresu czasu wyrażoną w dniach.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość daty/zakresu czasu wyrażona w dniach. Chociaż ta funkcja jest prototypem, aby zwracała wartość podwójną, zawsze zwróci liczbę całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w przedziale około-3.65 E6 i 3.65 E6.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

Pobiera tę wartość daty/zakresu czasu wyrażoną w godzinach.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/zakresu czasu wyrażona w godzinach. Chociaż ta funkcja jest prototypem, aby zwracała wartość podwójną, zawsze zwróci liczbę całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w przedziale około-8.77 E7 i 8.77 E7.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład dla [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

Pobiera wartość daty/zakresu czasu wyrażoną w minutach.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość daty/zakresu czasu wyrażona w minutach. Chociaż ta funkcja jest prototypem, aby zwracała wartość podwójną, zawsze zwróci liczbę całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w przedziale około-5.26 E9 i 5.26 E9.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład dla [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

Pobiera wartość daty/zakresu czasu wyrażoną w sekundach.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość daty/zakresu czasu wyrażona w sekundach. Chociaż ta funkcja jest prototypem, aby zwracała wartość podwójną, zawsze zwróci liczbę całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji mieszczą się w przedziale od E11 do ppkt 3.16 E11.

W przypadku innych funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Przykład

Zobacz przykład dla [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan:: m_span

Wartość bazowa **`double`** dla tego `COleDateTime` obiektu.

```
double m_span;
```

### <a name="remarks"></a>Uwagi

Ta wartość wyraża zakres daty/godziny w dniach.

> [!CAUTION]
> Zmiana wartości w **`double`** elemencie członkowskim danych spowoduje zmianę wartości tego `COleDateTimeSpan` obiektu. Nie powoduje zmiany stanu tego `COleDateTimeSpan` obiektu.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan:: m_status

Typ tego elementu członkowskiego danych jest typem wyliczanym `DateTimeSpanStatus` , który jest zdefiniowany w `COleDateTimeSpan` klasie.

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

- `COleDateTimeSpan::valid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że ten `COleDateTimeSpan` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTimeSpan` obiektu jest nieprawidłowy w następujących przypadkach:

- Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji przypisywania arytmetycznego, mianowicie `+=` lub `-=` .

- Jeśli nieprawidłowa wartość została przypisana do tego obiektu.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu [SetStatus](#setstatus).

Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowe, zobacz [COleDateTimeSpan:: operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan:: operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Ten element członkowski danych ma na celu zaawansowaną sytuację programistyczną. Należy użyć wbudowanej funkcji składowej [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz, `SetStatus` Aby uzyskać dalsze ostrzeżenie dotyczące jawnego ustawiania tego elementu członkowskiego danych.

Aby uzyskać więcej informacji na temat granic dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan:: operator =

Kopiuje `COleDateTimeSpan` wartość.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Uwagi

Ten przeciążony operator przypisania kopiuje wartość Data/czas zakresu źródłowego do tego `COleDateTimeSpan` obiektu.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan:: operator +,-

Dodawanie, odejmowanie i zmiana znaku dla `COleDateTimeSpan` wartości.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Pierwsze dwa operatory umożliwiają dodawanie i odejmowanie wartości daty/godziny. Trzecia pozwala zmienić znak wartości daty/zakresu.

Jeśli jeden z operandów ma wartość null, stan `COleDateTimeSpan` wartości wyników jest równy null.

Jeśli jeden z operandów jest nieprawidłowy, a drugi nie ma wartości null, stan wartości uzyskanej `COleDateTimeSpan` jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan:: operator + =,-=

Dodaj i Odejmij `COleDateTimeSpan` wartość z tej `COleDateTimeSpan` wartości.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i odejmowanie wartości typu Data/godzina z tego `COleDateTimeSpan` obiektu. Jeśli jeden z operandów ma wartość null, stan `COleDateTimeSpan` wartości wyników jest równy null.

Jeśli jeden z operandów jest nieprawidłowy, a drugi nie ma wartości null, stan wartości uzyskanej `COleDateTimeSpan` jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan:: operator Double

Konwertuje tę `COleDateTimeSpan` wartość na **`double`** .

```
operator double() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wartość tej `COleDateTimeSpan` wartości jako zmiennoprzecinkową liczbę dni.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan

Ustawia wartość tej wartości daty/godziny.

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Wskaż wartości daty i zakresu czasu, które mają być skopiowane do tego `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

Dla funkcji, które wysyłają zapytania do wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan:: SetStatus

Ustawia stan (ważność) tego `COleDateTimeSpan` obiektu.

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Nowa wartość stanu dla tego `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *status* jest definiowana przez `DateTimeSpanStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleDateTimeSpan` klasie.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTimeSpan::valid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid`Wskazuje, że ten `COleDateTimeSpan` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTimeSpan::null`Wskazuje, że ten `COleDateTimeSpan` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

   > [!CAUTION]
   > Ta funkcja jest dla zaawansowanych sytuacji programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. Będzie najczęściej używany do ustawienia stanu na **wartość null** lub **nieprawidłowy**. Należy zauważyć, że operator przypisania ([operator =](#operator_eq)) i [SetDateTimeSpan](#setdatetimespan) ustawia stan obiektu na podstawie wartości źródłowych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[Klasa CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
