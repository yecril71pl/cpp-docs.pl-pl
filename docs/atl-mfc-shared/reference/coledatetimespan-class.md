---
title: COleDateTimeSpan, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee7ccca718a05529e5ebc88bccc7d23d258810c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758365"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan, klasa

Reprezentuje względne czasu, przedział czasu.

## <a name="syntax"></a>Składnia

```
class COleDateTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Konstruuje `COleDateTimeSpan` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Generuje reprezentację ciągu sformatowaną `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan::GetDays](#getdays)|Zwraca część dotyczącą dnia z zakresu, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetHours](#gethours)|Zwraca część godzin z zakresu, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Zwraca część minut z zakresu, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Zwraca część drugiego zakresu, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Pobiera stan (ważność) to `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Zwraca liczbę dni, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Zwraca liczbę godzin, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca liczbę minut, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca liczbę sekund, to `COleDateTimeSpan` obiekt reprezentuje.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Ustawia wartość tego `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Ustawia stan (ważność) to `COleDateTimeSpan` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[operator +, -](#operator_add_-)|Dodawanie, odejmowanie i zmienić logowania dla `COleDateTimeSpan` wartości.|
|[operator +=-=](#operator_add_eq_-_eq)|Dodawanie i odejmowanie `COleDateTimeSpan` wartości z tego `COleDateTimeSpan` wartość.|
|[operator =](#operator_eq)|Kopiuje `COleDateTimeSpan` wartość.|
|[operator ==, <, < =](#coledatetimespan_relational_operators)|Porównanie dwóch `COleDateTimeSpan` wartości.|
|[double — operator](#operator_double)|Konwertuje to `COleDateTimeSpan` wartość **double**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Zawiera podstawowe **double** tego `COleDateTimeSpan` obiektu.|
|[COleDateTimeSpan::m_status](#m_status)|Zawiera informacje o stanie tego `COleDateTimeSpan` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTimeSpan` nie ma klasy bazowej.

A `COleDateTimeSpan` utrzymuje czasu w dniach.

`COleDateTimeSpan` jest używany z klasą Pomocnika [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime` hermetyzuje `DATE` typ danych w automatyzacji OLE. `COleDateTime` reprezentuje bezwzględne wartości czasu. Wszystkie `COleDateTime` obliczeń obejmują `COleDateTimeSpan` wartości. Relacja między tymi klasami jest analogiczna do jednego między [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej informacji na temat `COleDateTime` i `COleDateTimeSpan` klas, zapoznaj się z artykułem [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime.h

##  <a name="coledatetimespan_relational_operators"></a>  COleDateTimeSpan, operatory relacyjne

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

*dateSpan*  
`COleDateTimeSpan` Do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównania dwóch wartości daty/godziny — zakres i zwracają wartość TRUE, jeśli warunek jest prawdziwy; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  ATLASSERT wystąpi, jeśli jeden z operandów jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan

Konstruuje `COleDateTimeSpan` obiektu.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*dblSpanSrc*  
Liczba dni do skopiowania w nowe `COleDateTimeSpan` obiektu.

*lDays*, *nHours*, *nMins*, *nSecs*  
Wskazuje wartości dnia i godziny, które mają zostać skopiowane do nowego `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleDateTimeSpan` obiektów inicjowane z podaną wartością. Krótki opis każdego z tych konstruktorów następująco:

- **(COleDateTimeSpan)** tworzy `COleDateTimeSpan` obiektu inicjowane na wartość 0.

- **COleDateTimeSpan (** `dblSpanSrc` **)** tworzy `COleDateTimeSpan` obiekt z wartością zmiennoprzecinkową.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)**  Konstruuje `COleDateTimeSpan` obiekt został zainicjowany do określonej wartości liczbowe.

Stan nowego `COleDateTimeSpan` obiekt jest ustawiony na prawidłowy.

Aby uzyskać więcej informacji na temat granice dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

##  <a name="format"></a>  COleDateTimeSpan::Format

Generuje reprezentację ciągu sformatowaną `COleDateTimeSpan` obiektu.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*  
Formatowanie ciągów podobne do `printf` ciąg formatowania. Formatowanie kodów, poprzedzony procent (`%`) Zaloguj się, są zastępowane przez odpowiednie `COleDateTimeSpan` składnika. Inne znaki do ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Wartość i znaczenie kody formatowania `Format` są wymienione poniżej:

- **%H** godz. w bieżącym dniu

- **%M** minut w bieżącej godziny

- **%S** sekund w ciągu bieżącej minuty

- **%%** Znak procentu

Cztery kodów formatu wymienione powyżej są tylko kody, które będzie akceptować formatu.

-

*nID*  
Identyfikator zasobu ciąg formantu formatu.

### <a name="return-value"></a>Wartość zwracana

A `CString` który zawiera sformatowaną wartość daty/godziny — zakres.

### <a name="remarks"></a>Uwagi

Wywołania tych funkcji, aby utworzyć sformatowany reprezentacja wartości zakresu czasu. Jeśli stan to `COleDateTimeSpan` obiekt ma wartość null, wartość zwracana jest ciągiem pustym. Jeśli stan jest nieprawidłowa, zwracanego ciągu jest określany przez zasób ciągu IDS_INVALID_DATETIMESPAN.

Krótki opis formularzy dla tej funkcji są następujące:

**Format (** *pFormat* **)**  
Ten formularz, formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest przekazywany jako parametr do funkcji.

**Format (** *nID* **)**  
Ten formularz, formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest zasobem. Identyfikator zasobu ciągu jest przekazywany jako parametr.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

##  <a name="getdays"></a>  COleDateTimeSpan::GetDays

Pobiera część dotyczącą dnia z tej wartości daty/godziny — zakres.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część dotyczącą dnia z tej wartości daty/godziny — zakres.

### <a name="remarks"></a>Uwagi

Zwracania wartości z tego zakresu funkcji między około - 3,615,000 i 3,615,000.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

##  <a name="gethours"></a>  COleDateTimeSpan::GetHours

Pobiera część dotyczącą godziny z tej wartości daty/godziny — zakres.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część godzin tej wartości daty/godziny — zakres.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji, od - 23 do 23.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes

Pobiera część dotyczącą minut tej wartości daty/godziny — zakres.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część minut tej wartości daty/godziny — zakres.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji, od - 59 do 59.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds

Pobiera część dotyczącą sekund tej wartości daty/godziny — zakres.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Część sekund tej wartości daty/godziny — zakres.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji, od - 59 do 59.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus

Pobiera stan (ważność) to `COleDateTimeSpan` obiektu.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Stan to `COleDateTimeSpan` wartość.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowany przez `DateTimeSpanStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleDateTimeSpan` klasy.

```
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```

Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:

- `COleDateTimeSpan::valid` Wskazuje, że `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid` Wskazuje, że `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.

- `COleDateTimeSpan::null` Wskazuje, że `COleDateTimeSpan` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTimeSpan` obiekt jest nieprawidłowy w następujących przypadkach:

- Ten obiekt ma spowodować przepełnienie lub niedopełnienie podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.

- Jeśli wartość jest nieprawidłowa został przypisany do tego obiektu.

- Jeśli stan tego obiektu jawnie ustawiono nieprawidłowy przy użyciu `SetStatus`.

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Aby uzyskać więcej informacji na temat granice dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays

Pobiera tę wartość daty/godziny — zakres wyrażona w dniach.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/godziny — zakres wyrażona w dniach. Mimo że ta funkcja jest prototypowane zwracać wartość o podwójnej precyzji, która zawsze zwraca wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji między około - 3.65e6 i 3.65e6.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours

Pobiera tę wartość daty/godziny — zakres wyrażonych w godzinach.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/godziny — zakres wyrażonych w godzinach. Mimo że ta funkcja jest prototypowane zwracać wartość o podwójnej precyzji, która zawsze zwraca wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji między około - 8.77e7 i 8.77e7.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład [GetTotalDays](#gettotaldays).

##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes

Pobiera tę wartość daty/godziny — zakres wyrażone w ciągu kilku minut.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/godziny — zakres wyrażone w ciągu kilku minut. Mimo że ta funkcja jest prototypowane zwracać wartość o podwójnej precyzji, która zawsze zwraca wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tego zakresu funkcji między około - 5.26e9 i 5.26e9.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Przykład

Zobacz przykład [GetTotalDays](#gettotaldays).

##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds

Pobiera tę wartość daty/godziny — zakres wyrażony w sekundach.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Ta wartość daty/godziny — zakres wyrażony w sekundach. Mimo że ta funkcja jest prototypowane zwracać wartość o podwójnej precyzji, która zawsze zwraca wartość całkowitą.

### <a name="remarks"></a>Uwagi

Wartości zwracane z tej funkcji w zakresie od około — 3.16e11 do 3.16e11.

Do innych funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Przykład

Zobacz przykład [GetTotalDays](#gettotaldays).

##  <a name="m_span"></a>  COleDateTimeSpan::m_span

Podstawowe **double** wartość to `COleDateTime` obiektu.

```
double m_span;
```

### <a name="remarks"></a>Uwagi

Ta wartość określa Data /-przedział czasu w dniach.

> [!CAUTION]
>  Zmiana wartości w **double** element członkowski danych zmieni się wartość tego `COleDateTimeSpan` obiektu. Nie zmienia się jego stan to `COleDateTimeSpan` obiektu.

##  <a name="m_status"></a>  COleDateTimeSpan::m_status

Typ dla tego elementu członkowskiego danych jest Typ wyliczany `DateTimeSpanStatus`, który jest zdefiniowany w obrębie `COleDateTimeSpan` klasy.

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

Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:

- `COleDateTimeSpan::valid` Wskazuje, że `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid` Wskazuje, że `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.

- `COleDateTimeSpan::null` Wskazuje, że `COleDateTimeSpan` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTimeSpan` obiekt jest nieprawidłowy w następujących przypadkach:

- Ten obiekt ma spowodować przepełnienie lub niedopełnienie podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.

- Jeśli wartość jest nieprawidłowa został przypisany do tego obiektu.

- Jeśli stan tego obiektu jawnie ustawiono nieprawidłowy przy użyciu [SetStatus](#setstatus).

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
>  Ten element członkowski danych dotyczy zaawansowane sytuacjach programistycznych. Skorzystaj z wbudowanych funkcji elementów członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszych ostrzeżenia dotyczące jawne ustawienie ten element członkowski danych.

Aby uzyskać więcej informacji na temat granice dla `COleDateTimeSpan` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =

Kopiuje `COleDateTimeSpan` wartość.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Uwagi

Ten operator przypisania przeciążona kopiuje wartość daty/godziny — zakres źródła do tego `COleDateTimeSpan` obiektu.

##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +, -

Dodawanie, odejmowanie i zmienić logowania dla `COleDateTimeSpan` wartości.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Uwagi

Pierwsze dwa operatory pozwalają na dodawanie i odejmowanie wartości daty/godziny — zakres. Trzeci pozwala zmienić znak wartości daty/godziny — zakres.

Jeśli jeden z operandów jest null, stan wynikowy `COleDateTimeSpan` ma wartość null.

Jeśli jeden z operandów jest nieprawidłowa, a druga nie ma wartość null, stan wynikowy `COleDateTimeSpan` wartość jest nieprawidłowa.

Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator +=-=

Dodawanie i odejmowanie `COleDateTimeSpan` wartości z tego `COleDateTimeSpan` wartość.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory pozwalają na dodawanie i odejmowanie wartości daty/godziny — zakres z tego `COleDateTimeSpan` obiektu. Jeśli jeden z operandów jest null, stan wynikowy `COleDateTimeSpan` ma wartość null.

Jeśli jeden z operandów jest nieprawidłowa, a druga nie ma wartość null, stan wynikowy `COleDateTimeSpan` wartość jest nieprawidłowa.

Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

##  <a name="operator_double"></a>  COleDateTimeSpan::operator double

Konwertuje to `COleDateTimeSpan` wartość **double**.

```
operator double() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca wartość tego `COleDateTimeSpan` wartości zmiennoprzecinkowej liczba dni.

##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan

Ustawia wartość tej wartości daty/godziny — zakres.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*lDays*, *nHours*, *nMins*, *nSecs*  
Wskazuje wartości zakresu dat i przedział czasu, który ma być skopiowany do tego `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

Dla funkcji, które tworzą zapytania dotyczące wartości `COleDateTimeSpan` obiektu, zobacz następujące funkcje elementów członkowskich:

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

##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus

Ustawia stan (ważność) to `COleDateTimeSpan` obiektu.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parametry

*status*  
Nowa wartość stanu w tym `COleDateTimeSpan` obiektu.

### <a name="remarks"></a>Uwagi

*Stan* wartość parametru jest definiowana przez `DateTimeSpanStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleDateTimeSpan` klasy.

```
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```

Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:

- `COleDateTimeSpan::valid` Wskazuje, że `COleDateTimeSpan` obiekt jest prawidłowy.

- `COleDateTimeSpan::invalid` Wskazuje, że `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.

- `COleDateTimeSpan::null` Wskazuje, że `COleDateTimeSpan` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).

   > [!CAUTION]
   > Ta funkcja jest zaawansowane sytuacjach programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. W większości przypadków posłuży do ustawiania stanu **null** lub **nieprawidłowy**. Należy pamiętać, że operator przypisania ( [operator =](#eq)) i [SetDateTimeSpan](#setdatetimespan) ustawić stan obiektu, w oparciu o wartości źródła.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Zobacz też

[COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md)   
[CTime, klasa](../../atl-mfc-shared/reference/ctime-class.md)   
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)   
[Diagram hierarchii](../../mfc/hierarchy-chart.md)   
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

