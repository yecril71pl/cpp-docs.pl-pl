---
title: CTimeSpan, klasa
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
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317501"
---
# <a name="ctimespan-class"></a>CTimeSpan, klasa

Ilość czasu, który jest wewnętrznie przechowywany jako liczba sekund w przedziale czasu.

## <a name="syntax"></a>Składnia

```
class CTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Konstruuje `CTimeSpan` obiekty na różne sposoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Konwertuje `CTimeSpan` a na sformatowany ciąg.|
|[CTimeSpan::GetDays](#getdays)|Zwraca wartość, która reprezentuje liczbę pełnych dni w tym `CTimeSpan`.|
|[CTimeSpan::GetHours](#gethours)|Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (od -23 do 23).|
|[CTimeSpan::Minuty](#getminutes)|Zwraca wartość reprezentującą liczbę minut w bieżącej godzinie (-59 do 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Zwraca wartość, która reprezentuje liczbę sekund w bieżącej minuty (-59 do 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Zwraca wartość `CTimeSpan` obiektu.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Zwraca wartość reprezentującą całkowitą liczbę pełnych `CTimeSpan`godzin w tym pliku .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca wartość reprezentującą całkowitą liczbę ukończonych `CTimeSpan`minut w tym pliku .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca wartość reprezentującą całkowitą liczbę pełnych `CTimeSpan`sekund w tym .|
|[CTimeSpan::Serialize64](#serialize64)|Serializuje dane do lub z archiwum.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator + -](#operator_add_-)|Dodaje i odejmuje `CTimeSpan` obiekty.|
|[operator += -=](#operator_add_eq_-_eq)|Dodaje i odejmuje `CTimeSpan` obiekt `CTimeSpan`do i z tego .|
|[operator == < itp.](#ctimespan_comparison_operators)|Porównuje dwie względne wartości czasu.|

## <a name="remarks"></a>Uwagi

`CTimeSpan`nie ma klasy podstawowej.

`CTimeSpan`funkcje konwertowania sekund na różne kombinacje dni, godzin, minut i sekund.

Obiekt `CTimeSpan` jest przechowywany w **strukturze __time64_t,** która wynosi 8 bajtów.

Klasa towarzysząca, [CTime](../../atl-mfc-shared/reference/ctime-class.md), reprezentuje czas bezwzględny.

Klasy `CTime` `CTimeSpan` i nie są przeznaczone do wyprowadzania. Ponieważ nie ma żadnych funkcji wirtualnych, rozmiar obu `CTime` i `CTimeSpan` obiektów jest dokładnie 8 bajtów. Większość funkcji członkowskich są wbudowane.

Aby uzyskać więcej `CTimeSpan`informacji na temat używania , zobacz artykuły [Data i godzina](../../atl-mfc-shared/date-and-time.md)oraz [Zarządzanie czasem](../../c-runtime-library/time-management.md) w *odwołaniu do biblioteki w czasie wykonywania*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>Operatory porównania CTimeSpan

Operatory porównawcze.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwie względne wartości czasu. Zwracają true, jeśli warunek jest spełniony; w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan::CTimeSpan

Konstruuje `CTimeSpan` obiekty na różne sposoby.

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

*czasSpanSrc*<br/>
Obiekt, `CTimeSpan` który już istnieje.

*Czas*<br/>
**Wartość czasu __time64_t,** która jest liczbą sekund w przedziale czasu.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Odpowiednio dni, godziny, minuty i sekundy.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory utworzyć nowy `CTimeSpan` obiekt zainicjowany z określonym czasem względnym. Każdy konstruktor jest opisany poniżej:

- `CTimeSpan( );`Konstruuje niezainicjowany `CTimeSpan` obiekt.

- `CTimeSpan( const CTimeSpan& );`Konstruuje `CTimeSpan` obiekt `CTimeSpan` z innej wartości.

- `CTimeSpan( __time64_t );`Konstruuje `CTimeSpan` obiekt z **typu __time64_t.**

- `CTimeSpan( LONG, int, int, int );`Tworzy `CTimeSpan` obiekt z komponentów z każdego komponentu ograniczone do następujących zakresów:

   |Składnik|Zakres|
   |---------------|-----------|
   |*lDni*|0-25 000 (w przybliżeniu)|
   |*nGodziny*|0-23|
   |*nMins*|0-59|
   |*nSecs (*|0-59|

Należy zauważyć, że wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza, jeśli jeden lub więcej składników dnia czasu jest poza zakresem. Twoim obowiązkiem jest sprawdzenie poprawności argumentów przed wywołaniem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan::Format

Generuje sformatowany ciąg odpowiadający `CTimeSpan`temu plikowi .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*, *pszFormat*<br/>
Ciąg formatowania podobny `printf` do ciągu formatowania. Kody formatowania, poprzedzone`%`znakiem procentu ( `CTimeSpan` ), są zastępowane przez odpowiedni składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Poniżej wymieniono wartość i `Format` znaczenie kodów formatowania:

- **%D** Łączna liczba dni w tym`CTimeSpan`

- **%H** Godziny w bieżącym dniu

- **%M** Minuty w bieżącej godzinie

- **%S** Sekundy w bieżącej minucie

- **%%** Znak procentowy

*Nid*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający sformatowany czas.

### <a name="remarks"></a>Uwagi

Wersja debugowania biblioteki sprawdza kody formatowania i potwierdza, jeśli kod nie znajduje się na powyższej liście.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan::GetDays

Zwraca wartość, która reprezentuje liczbę pełnych dni w tym `CTimeSpan`.

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę ukończonych 24-godzinnych dni w przedziale czasu. Ta wartość może być ujemna, jeśli przedział czasu jest ujemny.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że `GetDays` czas letni może spowodować zwrócenie potencjalnie zaskakujący wynik. Na przykład, gdy czas 1st jest w mocy, `GetDays` raportuje liczbę dni między 1 kwietnia i 1 maja jako 29, a nie 30, ponieważ jeden dzień w kwietniu jest skrócony o godzinę i dlatego nie jest liczony jako pełny dzień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan::GetHours

Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (od -23 do 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę godzin w bieżącym dniu. Zakres wynosi od -23 do 23.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan::Minuty

Zwraca wartość reprezentującą liczbę minut w bieżącej godzinie (-59 do 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę minut w bieżącej godzinie. Zakres wynosi od -59 do 59.

### <a name="example"></a>Przykład

Zobacz przykład [gethours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan::GetSeconds

Zwraca wartość, która reprezentuje liczbę sekund w bieżącej minuty (-59 do 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę sekund w bieżącej minucie. Zakres wynosi od -59 do 59.

### <a name="example"></a>Przykład

Zobacz przykład [gethours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan::GetTimeSpan

Zwraca wartość `CTimeSpan` obiektu.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą wartość `CTimeSpan` obiektu.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan::GetTotalHours

Zwraca wartość reprezentującą całkowitą liczbę pełnych `CTimeSpan`godzin w tym pliku .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca całkowitą liczbę pełnych `CTimeSpan`godzin w tym .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan::GetTotalMinutes

Zwraca wartość reprezentującą całkowitą liczbę ukończonych `CTimeSpan`minut w tym pliku .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca całkowitą liczbę ukończonych `CTimeSpan`minut w tym .

### <a name="example"></a>Przykład

Zobacz przykład [gettotalhours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan::GetTotalSeconds

Zwraca wartość reprezentującą całkowitą liczbę pełnych `CTimeSpan`sekund w tym .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca całkowitą liczbę pełnych `CTimeSpan`sekund w tym .

### <a name="example"></a>Przykład

Zobacz przykład [gettotalhours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::operator +, -

Dodaje i odejmuje `CTimeSpan` obiekty.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Wartość dodana do `CTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CTimeSpan` reprezentujący wynik operacji.

### <a name="remarks"></a>Uwagi

Te dwa operatory umożliwiają dodawanie `CTimeSpan` i odejmowanie obiektów do i od siebie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan::operator +=, -=

Dodaje i odejmuje `CTimeSpan` obiekt `CTimeSpan`do i z tego .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Wartość dodana do `CTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTimeSpan` obiekt.

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i `CTimeSpan` odejmowanie `CTimeSpan`obiektu do i od tego .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan::Serialize64

> [!NOTE]
> Ta metoda jest dostępna tylko w projektach MFC.

Serializuje dane skojarzone ze zmienną członkowną do lub z archiwum.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
Obiekt, `CArchive` który chcesz zaktualizować.

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
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
