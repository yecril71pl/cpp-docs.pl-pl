---
title: Klasa CTimeSpan
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 0c13aa0d8f6c46db3b018283ab2a408a3f9531e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832025"
---
# <a name="ctimespan-class"></a>Klasa CTimeSpan

Czas, który jest wewnętrznie przechowywany jako liczba sekund w przedziale czasu.

## <a name="syntax"></a>Składnia

```
class CTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Tworzy `CTimeSpan` obiekty na różne sposoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTimeSpan:: format](#format)|Konwertuje `CTimeSpan` do sformatowanego ciągu.|
|[CTimeSpan:: GetDays](#getdays)|Zwraca wartość reprezentującą liczbę pełnych dni w tym elemencie `CTimeSpan` .|
|[CTimeSpan:: getgodz.](#gethours)|Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (-23 do 23).|
|[CTimeSpan:: getmin](#getminutes)|Zwraca wartość reprezentującą liczbę minut w bieżącej godzinie (-59 do 59).|
|[CTimeSpan:: getSeconds](#getseconds)|Zwraca wartość reprezentującą liczbę sekund w bieżącej minucie (-59 do 59).|
|[CTimeSpan:: GetTimeSpan](#gettimespan)|Zwraca wartość `CTimeSpan` obiektu.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Zwraca wartość reprezentującą łączną liczbę godzin w tym elemencie `CTimeSpan` .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca wartość reprezentującą łączną liczbę pełnych minut w tym elemencie `CTimeSpan` .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca wartość reprezentującą łączną liczbę pełnych sekund w tym elemencie `CTimeSpan` .|
|[CTimeSpan::Serialize64](#serialize64)|Serializować dane do lub z archiwum.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator +-](#operator_add_-)|Dodaje i odejmuje `CTimeSpan` obiekty.|
|[operator + =-=](#operator_add_eq_-_eq)|Dodaje i odejmuje `CTimeSpan` obiekt do i od `CTimeSpan` .|
|[operator = = < itd.](#ctimespan_comparison_operators)|Porównuje dwie względne wartości czasu.|

## <a name="remarks"></a>Uwagi

`CTimeSpan` nie ma klasy bazowej.

`CTimeSpan` funkcje konwertują sekundy na różne kombinacje dni, godzin, minut i sekund.

`CTimeSpan`Obiekt jest przechowywany w strukturze **__time64_t** , która wynosi 8 bajtów.

Klasa pomocnika, [CTime](../../atl-mfc-shared/reference/ctime-class.md), reprezentuje bezwzględny czas.

`CTime`Klasy i `CTimeSpan` nie są przeznaczone do wyprowadzania. Ponieważ nie ma żadnych funkcji wirtualnych, rozmiar obu `CTime` i `CTimeSpan` obiektów wynosi dokładnie 8 bajtów. Większość funkcji składowych jest wbudowanych.

Aby uzyskać więcej informacji na temat korzystania z programu `CTimeSpan` , zobacz artykuł [Data i godzina](../../atl-mfc-shared/date-and-time.md)i [Zarządzanie czasem](../../c-runtime-library/time-management.md) w *dokumentacji w czasie wykonywania*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime. h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a> Operatory porównania CTimeSpan

Operatory porównania.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwie względne wartości czasu. Zwraca wartość TRUE, jeśli warunek ma wartość true; w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a> CTimeSpan::CTimeSpan

Tworzy `CTimeSpan` obiekty na różne sposoby.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*timeSpanSrc*<br/>
`CTimeSpan`Obiekt, który już istnieje.

*pierwszym*<br/>
**__Time64_t** wartość czasu, czyli liczbę sekund w przedziale czasu.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Odpowiednio dni, godziny, minuty i sekundy.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowy `CTimeSpan` obiekt zainicjowany z określonym względnym czasem. Każdy Konstruktor jest opisany poniżej:

- `CTimeSpan( );` Tworzy niezainicjowany `CTimeSpan` obiekt.

- `CTimeSpan( const CTimeSpan& );` Konstruuje `CTimeSpan` obiekt z innej `CTimeSpan` wartości.

- `CTimeSpan( __time64_t );` Konstruuje `CTimeSpan` obiekt z typu **__time64_t** .

- `CTimeSpan( LONG, int, int, int );` Konstruuje `CTimeSpan` obiekt ze składników, które są ograniczone do następujących zakresów:

   |Składnik|Zakres|
   |---------------|-----------|
   |*lDays*|0 – 25000 (w przybliżeniu)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Należy zauważyć, że wersja do debugowania biblioteka MFC zostanie potwierdzona, jeśli co najmniej jeden z elementów czasu jest poza zakresem. Przed wywołaniem można sprawdzić poprawność argumentów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a> CTimeSpan:: format

Generuje sformatowany ciąg, który odpowiada temu `CTimeSpan` .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*, *pszFormat*<br/>
Ciąg formatowania podobny do `printf` ciągu formatowania. Kody formatowania poprzedzone znakiem procentu ( `%` ) są zastępowane przez odpowiedni `CTimeSpan` składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Poniżej przedstawiono wartość i znaczenie kodów formatowania dla programu `Format` :

- **% D** Łączna liczba dni w tym `CTimeSpan`

- **% H** Godz. w bieżącym dniu

- **% M** Minuty w bieżącej godzinie

- **% S** Sekundy w bieżącej minucie

- **%%** Znak procentu

*nID*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt, który zawiera sformatowany czas.

### <a name="remarks"></a>Uwagi

Wersja do debugowania biblioteki sprawdza kody formatowania i potwierdzenia, jeśli kod nie znajduje się na liście powyżej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a> CTimeSpan:: GetDays

Zwraca wartość reprezentującą liczbę pełnych dni w tym elemencie `CTimeSpan` .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pełnych 24-godzinnych dni w przedziale czasu. Ta wartość może być ujemna, jeśli przedział czasu jest ujemny.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że czas letni może spowodować `GetDays` zwrócenie potencjalnie zaskakujące wyniku. Na przykład gdy obowiązuje czas letni, program `GetDays` zgłasza liczbę dni od 1 kwietnia do 1 maja, a nie 30, ponieważ jeden dzień w kwietniu został skrócony o godzinę i dlatego nie liczy się jako pełny dzień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a> CTimeSpan:: getgodz.

Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (-23 do 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę godzin w bieżącym dniu. Zakresem jest-23 do 23.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a> CTimeSpan:: getmin

Zwraca wartość reprezentującą liczbę minut w bieżącej godzinie (-59 do 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę minut w bieżącej godzinie. Zakresem jest-59 do 59.

### <a name="example"></a>Przykład

Zobacz przykład dla [getHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a> CTimeSpan:: getSeconds

Zwraca wartość reprezentującą liczbę sekund w bieżącej minucie (-59 do 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę sekund w bieżącej minucie. Zakresem jest-59 do 59.

### <a name="example"></a>Przykład

Zobacz przykład dla [getHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a> CTimeSpan:: GetTimeSpan

Zwraca wartość `CTimeSpan` obiektu.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą wartość `CTimeSpan` obiektu.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a> CTimeSpan::GetTotalHours

Zwraca wartość reprezentującą łączną liczbę godzin w tym elemencie `CTimeSpan` .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca łączną liczbę godzin w tym elemencie `CTimeSpan` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a> CTimeSpan::GetTotalMinutes

Zwraca wartość reprezentującą łączną liczbę pełnych minut w tym elemencie `CTimeSpan` .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca łączną liczbę pełnych minut w tym elemencie `CTimeSpan` .

### <a name="example"></a>Przykład

Zobacz przykład dla [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a> CTimeSpan::GetTotalSeconds

Zwraca wartość reprezentującą łączną liczbę pełnych sekund w tym elemencie `CTimeSpan` .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca łączną liczbę pełnych sekund w tym elemencie `CTimeSpan` .

### <a name="example"></a>Przykład

Zobacz przykład dla [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a> CTimeSpan:: operator +,-

Dodaje i odejmuje `CTimeSpan` obiekty.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Wartość, która ma zostać dodana do `CTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CTimeSpan`Obiekt reprezentujący wynik operacji.

### <a name="remarks"></a>Uwagi

Te dwa operatory umożliwiają dodawanie i odejmowanie `CTimeSpan` obiektów do i od siebie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> CTimeSpan:: operator + =,-=

Dodaje i odejmuje `CTimeSpan` obiekt do i od `CTimeSpan` .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Wartość, która ma zostać dodana do `CTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTimeSpan` obiekt.

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i odejmowanie `CTimeSpan` obiektu do i z tego elementu `CTimeSpan` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a> CTimeSpan::Serialize64

> [!NOTE]
> Ta metoda jest dostępna tylko w projektach MFC.

Serializować dane skojarzone ze zmienną członkowską do lub z archiwum.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
`CArchive`Obiekt, który chcesz zaktualizować.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CArchive` obiekt.

## <a name="see-also"></a>Zobacz też

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
