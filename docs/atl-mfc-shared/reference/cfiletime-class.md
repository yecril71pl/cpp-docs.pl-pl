---
title: CFileTime, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36e71cd975ff138343770b80e60b0287faa32558
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808826"
---
# <a name="cfiletime-class"></a>CFileTime, klasa

Ta klasa dostarcza metody do zarządzania skojarzonych z plikiem wartości daty i godziny.

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|Wywołaj tę funkcję statycznych do pobrania `CFileTime` obiekt, który reprezentuje bieżącej systemowej daty i godziny.|
|[CFileTime::GetTime](#gettime)|Wywołanie tej metody do pobierania czasu z `CFileTime` obiektu.|
|[CFileTime::LocalToUTC](#localtoutc)|Wywołaj tę metodę, aby przekonwertować czasu lokalnego pliku na czas pliku, oparty na uniwersalny czas koordynowany (UTC).|
|[CFileTime::SetTime](#settime)|Wywołanie tej metody można ustawić datę i godzinę przechowywane przez `CFileTime` obiektu.|
|[CFileTime::UTCToLocal](#utctolocal)|Wywołaj tę metodę, aby skonwertować czas w oparciu o uniwersalnego czasu koordynowanego (UTC) do pliku lokalnego czasu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::operator-](#operator_-)|Ten operator jest używany do przeprowadzania odejmowania `CFileTime` lub `CFileTimeSpan` obiektu.|
|[CFileTime::operator! =](#operator_neq)|Ten operator porównuje dwa `CFileTime` obiekty pod kątem nierówności.|
|[CFileTime::operator +](#operator_add)|Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu.|
|[CFileTime::operator +=](#operator_add_eq)|Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|
|[CFileTime::operator &lt;](#operator_lt)|Ten operator porównuje dwa `CFileTime` obiektów, aby określić mniejszy.|
|[CFileTime::operator &lt;=](#operator_lt_eq)|Ten operator porównuje dwa `CFileTime` obiektów, aby określić równości lub mniejszy.|
|[CFileTime::operator =](#operator_eq)|Operator przypisania.|
|[CFileTime::operator-=](#operator_-_eq)|Ten operator jest używany do przeprowadzania odejmowania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|
|[CFileTime::operator ==](#operator_eq_eq)|Ten operator porównuje dwa `CFileTime` obiekty pod kątem równości.|
|[CFileTime::operator &gt;](#operator_gt)|Ten operator porównuje dwa `CFileTime` obiektów, aby określić wyższy.|
|[CFileTime::operator &gt;=](#operator_gt_eq)|Ten operator porównuje dwa `CFileTime` obiektów, aby określić równości lub większy.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[CFileTime::Day](#day)|Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jeden dzień.|
|[CFileTime::Hour](#hour)|Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jedną godzinę.|
|[CFileTime::Millisecond](#millisecond)|Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jeden milisekund.|
|[CFileTime::Minute](#minute)|Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jedną minutę.|
|[CFileTime::Second](#second)|Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jedną sekundę.|
|[CFileTime::Week](#week)|Element członkowski danych statycznych, przechowywania liczbę 100-nanosekundowych interwałów, które składają się co tydzień.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody do zarządzania wartości daty i godziny związane z tworzenia, dostępu i modyfikacji plików. Metody i danych tej klasy są często używane w połączeniu z `CFileTimeSpan` obiektów, które dotyczy względne wartości czasu.

Wartość daty i godziny są przechowywane jako 64-bitowych reprezentującą liczbę 100-nanosekundowych interwałów, od 1 stycznia 1601. Ten format jest używany uniwersalny czas koordynowany (UTC).

Następujące statyczny const zmienne Członkowskie są dostarczane do uproszczenia obliczeń:

|Zmienna składowa|Liczbę 100-nanosekundowych interwałów|
|---------------------|-----------------------------------------|
|Milisekundy|10 000|
|Sekunda|Milisekunda \* 1000|
|Minuta|Drugi \* 60|
|Godzina|Minuty \* 60|
|Dzień|Godzina \* 24|
|Tydzień|Dzień \* 7|

**Uwaga** nie wszystkie systemy plików mogą rejestrować tworzenia i czas ostatniego dostępu i nie wszystkie systemy plików zarejestruj je w taki sam sposób. Na przykład w systemie plików FAT Windows NT, utworzyć czasu ma rozdzielczość 10 milisekund, czas zapisu ma rozdzielczość 2 sekundy, a czas dostępu ma rozdzielczość 1 dzień (data access). W systemie plików NTFS czas dostępu ma rozdzielczość równej 1 godz. Ponadto system plików FAT rejestruje czas na dysku w czasie lokalnym, ale NTFS rejestruje czas na dysku w formacie UTC. Aby uzyskać więcej informacji, zobacz [czasy](/windows/desktop/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

Konstruktor.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
A [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) struktury.

*nTime*<br/>
Data i godzina wyrażonej w postaci wartości 64-bitowych.

### <a name="remarks"></a>Uwagi

`CFileTime` Obiektu można utworzyć przy użyciu istniejących daty i godziny z `FILETIME` struktury lub wyrażony jako wartość 64-bitowych (lokalnego lub w formacie czasu uniwersalnego czasu koordynowanego (UTC)). Domyślny konstruktor ustawia czas na 0.

##  <a name="day"></a>  CFileTime::Day

Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jeden dzień.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](#millisecond).

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

Wywołaj tę funkcję statycznych do pobrania `CFileTime` obiekt, który reprezentuje bieżącej systemowej daty i godziny.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca datę i godzinę w formacie uniwersalnego czasu koordynowanego (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

Wywołanie tej metody do pobierania czasu z `CFileTime` obiektu.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca datę i godzinę jako liczbę 64-bitowych, które mogą okazać się w lokalnej lub w formacie uniwersalnego czasu koordynowanego (UTC).

##  <a name="hour"></a>  CFileTime::Hour

Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jedną godzinę.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](#millisecond).

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

Wywołaj tę metodę, aby przekonwertować czasu lokalnego pliku na czas pliku, oparty na uniwersalny czas koordynowany (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt zawierający godzinę w formacie UTC.

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>  CFileTime::Millisecond

Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jeden milisekund.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jedną minutę.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](#millisecond).

##  <a name="operator_-"></a>  CFileTime::operator-

Ten operator jest używany do przeprowadzania odejmowania `CFileTime` lub `CFileTimeSpan` obiektu.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

*FT*<br/>
Element `CFileTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiektu lub `CFileTimeSpan` obiekt reprezentujący wynik różnica czasu między dwoma obiektami.

##  <a name="operator_neq"></a>  CFileTime::operator! =

Ten operator porównuje dwa `CFileTime` obiekty pod kątem nierówności.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany nie jest równa `CFileTime` obiektu, w przeciwnym razie wartość FALSE.

##  <a name="operator_add"></a>  CFileTime::operator +

Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt reprezentujący wynik pierwotny czas, a także względne czasu.

##  <a name="operator_add_eq"></a>  CFileTime::operator +=

Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiekt reprezentujący wynik pierwotny czas, a także względne czasu.

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

Ten operator porównuje dwa `CFileTime` obiektów, aby określić mniejszy.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejsza (wcześniej w czasie) niż druga Strona, FALSE w przeciwnym razie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

Ten operator porównuje dwa `CFileTime` obiektów, aby określić równości lub mniejszy.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy niż (wcześniej w czasie) lub równe drugiemu, w przeciwnym razie wartość FALSE.

##  <a name="operator_eq"></a>  CFileTime::operator =

Operator przypisania.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
A `CFileTime` obiekt, który zawiera nową wartość czasu i daty.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiektu.

##  <a name="operator_-_eq"></a>  CFileTime::operator-=

Ten operator jest używany do przeprowadzania odejmowania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
A `CFileTimeSpan` obiekt zawierający wartość względna czasu do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTime` obiektu.

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

Ten operator porównuje dwa `CFileTime` obiekty pod kątem równości.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

Ten operator porównuje dwa `CFileTime` obiektów, aby określić wyższy.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (w dalszej części godziny) od drugiej, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

Ten operator porównuje dwa `CFileTime` obiektów, aby określić równości lub większy.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (w dalszej części czasu) lub równe drugiemu, w przeciwnym razie wartość FALSE.

##  <a name="second"></a>  CFileTime::Second

Element członkowski danych statycznych, która umożliwia przechowywanie liczbę 100-nanosekundowych interwałów, które tworzą jeden dzień.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](#millisecond).

##  <a name="settime"></a>  CFileTime::SetTime

Wywołanie tej metody można ustawić datę i godzinę przechowywane przez `CFileTime` obiektu.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*nTime*<br/>
Wartość 64-bitowy, reprezentująca datę i godzinę w lokalnej lub w formacie uniwersalnego czasu koordynowanego (UTC).

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

Wywołaj tę metodę, aby skonwertować czas w oparciu o uniwersalnego czasu koordynowanego (UTC) do pliku lokalnego czasu.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTime` obiekt zawierający godzinę w formacie czasu lokalnego pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

Element członkowski danych statycznych, przechowywania liczbę 100-nanosekundowych interwałów, które składają się co tydzień.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](#millisecond).

## <a name="see-also"></a>Zobacz też

[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)<br/>
[CFileTimeSpan, klasa](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
