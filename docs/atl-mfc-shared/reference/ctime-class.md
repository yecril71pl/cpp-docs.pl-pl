---
title: CTime, klasa
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317567"
---
# <a name="ctime-class"></a>CTime, klasa

Reprezentuje bezwzględną godzinę i datę.

## <a name="syntax"></a>Składnia

```
class CTime
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime::CTime](#ctime)|Konstruuje `CTime` obiekty na różne sposoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime::Format](#format)|Konwertuje `CTime` obiekt na sformatowany ciąg — na podstawie lokalnej strefy czasowej.|
|[Czas CTime::FormatGmt](#formatgmt)|Konwertuje `CTime` obiekt na sformatowany ciąg — na podstawie czasu UTC.|
|[Czas CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Konwertuje informacje o `CTime` czasie przechowywane w obiekcie na strukturę DBTIMESTAMP zgodną z win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Konwertuje informacje o `CTime` czasie przechowywane w obiekcie na strukturę [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zgodną z win32.|
|[CTime::GetCurrentTime](#getcurrenttime)|Tworzy `CTime` obiekt reprezentujący bieżący czas (funkcja statycznego elementu członkowskiego).|
|[CTime::GetDay](#getday)|Zwraca dzień reprezentowany `CTime` przez obiekt.|
|[CTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia reprezentowanego przez `CTime` obiekt.|
|[Czas CTime::GetGmtTm](#getgmttm)|Dzieli obiekt `CTime` na komponenty — na podstawie czasu UTC.|
|[CTime::GetHour](#gethour)|Zwraca godzinę reprezentowaną `CTime` przez obiekt.|
|[Czas CTime::GetLocalTm](#getlocaltm)|Dzieli obiekt `CTime` na składniki — na podstawie lokalnej strefy czasowej.|
|[Czas CTime::GetMinute](#getminute)|Zwraca minutę reprezentowane `CTime` przez obiekt.|
|[Czas CTime::GetMonth](#getmonth)|Zwraca miesiąc reprezentowany `CTime` przez obiekt.|
|[Czas CTime::GetSecond](#getsecond)|Zwraca drugi reprezentowany `CTime` przez obiekt.|
|[CTime::GetTime](#gettime)|Zwraca **wartość __time64_t** dla danego `CTime` obiektu.|
|[CTime::GetYear](#getyear)|Zwraca rok reprezentowany `CTime` przez obiekt.|
|[Czas CTime::Serialize64](#serialize64)|Serializuje dane do lub z archiwum.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator + -](#operator_add_-)|Te operatory dodawać `CTimeSpan` `CTime` i odejmować i obiektów.|
|[operator +=, -=](#operator_add_eq_-_eq)|Te operatory dodać i `CTimeSpan` odjąć obiekt `CTime` do i z tego obiektu.|
|[operator =](#operator_eq)|Operator przypisania.|
|[operator ==, < itp.](#ctime_comparison_operators)|Operatory porównawcze.|

## <a name="remarks"></a>Uwagi

`CTime`nie ma klasy podstawowej.

`CTime`wartości są oparte na skoordynowanym czasie uniwersalnym (UTC), który jest odpowiednikiem skoordynowanego czasu uniwersalnego (Greenwich Mean Time, GMT). Zobacz [Zarządzanie czasem, aby](../../c-runtime-library/time-management.md) uzyskać informacje o określaniu strefy czasowej.

Podczas tworzenia `CTime` obiektu należy `nDST` ustawić parametr na 0, aby wskazać, że obowiązuje czas standardowy, lub wartość większą niż 0, aby wskazać, że obowiązuje czas letni, lub wartość mniejszą niż zero, aby kod biblioteki czasu wykonywania języka C obliczał, czy obowiązuje czas standardowy czy czas letni. `tm_isdst`jest polem wymaganym. Jeśli nie jest ustawiona, jego wartość jest niezdefiniowana, a wartość zwracana z [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) jest nieprzewidywalna. Jeśli `timeptr` wskazuje strukturę tm zwróconą przez poprzednie wywołanie [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)lub [localtime_s,](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) `tm_isdst` pole zawiera poprawną wartość.

Klasa towarzysząca, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), reprezentuje przedział czasu.

Klasy `CTime` `CTimeSpan` i nie są przeznaczone do wyprowadzania. Ponieważ nie ma żadnych funkcji `CTime` wirtualnych, rozmiar i `CTimeSpan` obiekty jest dokładnie 8 bajtów. Większość funkcji członkowskich są wbudowane.

> [!NOTE]
> Górny limit dat to 12/31/3000. Dolna granica to 1.01.1970 12:00:00 GMT.

Aby uzyskać więcej `CTime`informacji na temat używania , zobacz artykuły [Data i godzina](../../atl-mfc-shared/date-and-time.md)oraz [Zarządzanie czasem](../../c-runtime-library/time-management.md) w odwołaniu do biblioteki w czasie wykonywania.

> [!NOTE]
> Struktura `CTime` zmieniła się z MFC 7.1 na MFC 8.0. Jeśli serializujesz `CTime` strukturę przy użyciu **operatora <<** w obszarze MFC 8.0 lub nowszej wersji, wynikowy plik nie będzie czytelny w starszych wersjach MFC.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>Operatory porównania CTime

Operatory porównawcze.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Czas*<br/>
Obiekt `CTime` do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwa bezwzględne czasy i zwracają wartość PRAWDA, jeśli warunek jest spełniony; w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>CTime::CTime

Tworzy nowy `CTime` obiekt zainicjowany o określonym czasie.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Parametry

*czasSrc*<br/>
Wskazuje obiekt, `CTime` który już istnieje.

*Czas*<br/>
Wartość `__time64_t` czasu, czyli liczba sekund po 1 stycznia 1970 UTC. Należy pamiętać, że zostanie to dostosowane do czasu lokalnego. Na przykład jeśli jesteś w Nowym `CTime` Jorku i utworzyć obiekt, przekazując parametr 0, [CTime::GetMonth](#getmonth) zwróci 12.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Wskazuje wartości daty i godziny, które `CTime` mają zostać skopiowane do nowego obiektu.

*nDST (nDST)*<br/>
Wskazuje, czy czas letni obowiązuje. Może mieć jedną z trzech wartości:

- *nDST* ustawiony na 0Z czasu ustalania czasu.

- *nDST* ustawiona na wartość większą niż 0Czas oszczędzania w ciągu dnia jest w mocy.

- *nDST* ustawiono wartość mniejszą niż 0Oi domyślna. Automatycznie oblicza, czy czas standardowy czy czas letni obowiązuje.

*wDosDate*, *wDosTime*<br/>
Wartości daty i godziny ms-dos, które mają zostać przekonwertowane na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.

*St*<br/>
Struktura [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która ma zostać przekonwertowana na `CTime` wartość daty/godziny i skopiowana do nowego obiektu.

*Ft*<br/>
Struktura [FILETIME,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) która ma zostać przekonwertowana na `CTime` wartość daty/godziny i skopiowana do nowego obiektu.

*dbts (dbts)*<br/>
Odwołanie do struktury DBTIMESTAMP zawierającej bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Każdy konstruktor jest opisany poniżej:

- `CTime();`Konstruuje niezainicjowany `CTime` obiekt. Ten konstruktor umożliwia `CTime` definiowanie tablic obiektów. Przed użyciem należy zainicjować takie tablice z prawidłowymi czasami.

- `CTime( const CTime& );`Konstruuje `CTime` obiekt `CTime` z innej wartości.

- `CTime( __time64_t );`Konstruuje `CTime` obiekt z **typu __time64_t.** Ten konstruktor oczekuje czasu UTC i konwertuje wynik na czas lokalny przed zapisaniem wyniku.

- `CTime( int, int, ...);`Konstruuje `CTime` obiekt z składników czasu lokalnego z każdym komponentem ograniczonym do następujących zakresów:

   |Składnik|Zakres|
   |---------------|-----------|
   |*nRok*|1970-3000|
   |*nMonth*|1-12|
   |*nDzień*|1-31|
   |*nGodzina*|0-23|
   |*nMin (min.*|0-59|
   |*Nsec*|0-59|

   Ten konstruktor sprawia, że odpowiedni konwersji do czasu UTC. Wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza, jeśli jeden lub więcej składników czasu jest poza zakresem. Należy sprawdzić poprawność argumentów przed wywołaniem. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( WORD, WORD );`Konstruuje `CTime` obiekt z określonych wartości daty i godziny ms-dos. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( const SYSTEMTIME& );`Konstruuje `CTime` obiekt `SYSTEMTIME` ze struktury. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( const FILETIME& );`Konstruuje `CTime` obiekt `FILETIME` ze struktury. Najprawdopodobniej nie `CTime FILETIME` będzie używać inicjowania bezpośrednio. Jeśli używasz `CFile` obiektu do manipulowania `CFile::GetStatus` plikiem, pobiera sygnaturę `CTime` czasową `FILETIME` pliku za pośrednictwem obiektu zainicjowanego strukturą. Ten konstruktor zakłada czas oparty na czasie UTC i automatycznie konwertuje wartość na czas lokalny przed zapisaniem wyniku.

   > [!NOTE]
   > Konstruktor `DBTIMESTAMP` używający parametru jest dostępny tylko wtedy, gdy oledb.h jest uwzględniony.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktury w Windows SDK. Zobacz też wpis [Data i godzina systemu MS-DOS](/windows/win32/SysInfo/ms-dos-date-and-time) w sdku windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>CTime::Format

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć sformatowaną reprezentację wartości daty i godziny.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg formatowania podobny `printf` do ciągu formatowania. Kody formatowania, poprzedzone`%`znakiem procentu ( `CTime` ), są zastępowane przez odpowiedni składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Zobacz funkcję wykonawczą [strftime,](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) aby uzyskać listę kodów formatowania.

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

A [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który zawiera sformatowany czas.

### <a name="remarks"></a>Uwagi

Jeśli stan tego `CTime` obiektu ma wartość null, zwracana wartość jest pustym ciągiem.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do formatu nie waha się od północy, 1 stycznia 1970 do 31 grudnia 3000 uniwersalny czas koordynowany (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>Czas CTime::FormatGmt

Generuje sformatowany ciąg odpowiadający `CTime` temu obiektowi.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Określa ciąg formatowania podobny `printf` do ciągu formatowania. Zobacz funkcję wykonywania [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) szczegóły.

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

A [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który zawiera sformatowany czas.

### <a name="remarks"></a>Uwagi

Wartość czasu nie jest konwertowana i w związku z tym odzwierciedla wartość UTC.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do formatu nie waha się od północy, 1 stycznia 1970 do 31 grudnia 3000 uniwersalny czas koordynowany (UTC).

### <a name="example"></a>Przykład

Zobacz przykład [CTime::Format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>Czas CTime::GetAsDBTIMESTAMP

Wywołanie tej funkcji elementu członkowskiego, `CTime` aby przekonwertować informacje o czasie przechowywane w obiekcie do struktury DBTIMESTAMP zgodnej z win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*dbts (dbts)*<br/>
Odwołanie do struktury DBTIMESTAMP zawierającej bieżący czas lokalny.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przechowuje wynikczas w strukturze *dbts,* do których istnieje odwołanie. Struktura `DBTIMESTAMP` danych zainicjowana przez tę `fraction` funkcję będzie miała swój element członkowski ustawiony na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>CTime::GetAsSystemTime

Wywołanie tej funkcji elementu członkowskiego, `CTime` aby przekonwertować informacje o czasie przechowywane w obiekcie do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zgodnej z win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest (czas)*<br/>
Odwołanie do struktury [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) która będzie zawierać przekonwertowane wartości daty/godziny `CTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime`przechowuje wynikczas w strukturze *czas,* do której istnieje odwołanie. Struktura `SYSTEMTIME` danych zainicjowana przez tę `wMilliseconds` funkcję będzie miała swój element członkowski ustawiony na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>CTime::GetCurrentTime

Zwraca `CTime` obiekt reprezentujący bieżący czas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca bieżącą datę i godzinę systemowej w skoordynowanym czasie uniwersalnym (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>CTime::GetDay

Zwraca dzień reprezentowany `CTime` przez obiekt.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień miesiąca, na podstawie czasu lokalnego, w zakresie od 1 do 31.

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrznego, statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>CTime::GetDayOfWeek

Zwraca dzień tygodnia reprezentowanego przez `CTime` obiekt.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień tygodnia na podstawie czasu lokalnego; 1 = niedziela, 2 = poniedziałek, do 7 = sobota.

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>Czas CTime::GetGmtTm

Pobiera **tm struktury,** który zawiera rozkład czasu zawartego `CTime` w tym obiekcie.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Wskazuje bufor, który będzie odbierał dane czasu. Jeśli ten wskaźnik ma wartość NULL, zostanie zgłoszony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełnionej **struktury tm,** zgodnie z definicją w pliku dołączania TIME. H. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) dla układu konstrukcji.

### <a name="remarks"></a>Uwagi

`GetGmtTm`zwraca UTC.

*ptm* nie może być null. Jeśli chcesz przywrócić stare zachowanie, w którym *ptm* może być NULL, aby wskazać, że wewnętrzny, statycznie przydzielony bufor powinien być używany, a następnie undefine _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>CTime::GetHour

Zwraca godzinę reprezentowaną `CTime` przez obiekt.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca godzinę, na podstawie czasu lokalnego, w zakresie od 0 do 23.

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>Czas CTime::GetLocalTm

Pobiera **tm struktury** zawierające rozkład czasu zawarte w tym `CTime` obiekcie.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Wskazuje bufor, który będzie odbierał dane czasu. Jeśli ten wskaźnik ma wartość NULL, zostanie zgłoszony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełnionej **struktury tm,** zgodnie z definicją w pliku dołączania TIME. H. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) dla układu konstrukcji.

### <a name="remarks"></a>Uwagi

`GetLocalTm`zwraca czas lokalny.

*ptm* nie może być null. Jeśli chcesz przywrócić stare zachowanie, w którym *ptm* może być NULL, aby wskazać, że wewnętrzny, statycznie przydzielony bufor powinien być używany, a następnie undefine _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>Czas CTime::GetMinute

Zwraca minutę reprezentowane `CTime` przez obiekt.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca minutę, na podstawie czasu lokalnego, w zakresie od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [gethour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a>Czas CTime::GetMonth

Zwraca miesiąc reprezentowany `CTime` przez obiekt.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca miesiąc, na podstawie czasu lokalnego, w zakresie od 1 do 12 (1 = styczeń).

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [getday](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a>Czas CTime::GetSecond

Zwraca drugi reprezentowany `CTime` przez obiekt.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca drugi, na podstawie czasu lokalnego, w zakresie od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [gethour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a>CTime::GetTime

Zwraca **wartość __time64_t** dla danego `CTime` obiektu.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Wartość zwracana

`GetTime`powróci liczba sekund między bieżącym `CTime` obiektem a 1 stycznia 1970.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>CTime::GetYear

Zwraca rok reprezentowany `CTime` przez obiekt.

```
int GetYear();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rok, na podstawie czasu lokalnego, w zakresie 1 stycznia 1970 r. do 18 stycznia 2038 r. (włącznie).

### <a name="remarks"></a>Uwagi

Ta funkcja `GetLocalTm`wywołuje , który używa buforu wewnętrzna statycznie przydzielone. Dane w tym buforze jest zastępowany `CTime` z powodu wywołań do innych funkcji członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [getday](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>CTime::operator =

Operator przypisania.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*Czas*<br/>
Nowa wartość daty/godziny.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTime` obiekt.

### <a name="remarks"></a>Uwagi

Ten przeciążony operator przypisania kopiuje `CTime` czas źródłowy do tego obiektu. Wewnętrzna pamięć czasu `CTime` w obiekcie jest niezależna od strefy czasowej. Konwersja strefy czasowej nie jest konieczna podczas przypisywania.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::operator +, -

Te operatory dodawać `CTimeSpan` `CTime` i odejmować i obiektów.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Timespan*<br/>
Obiekt, `CTimeSpan` który ma zostać dodany lub odjęty.

*Czas*<br/>
Obiekt `CTime` do odjętego.

### <a name="return-value"></a>Wartość zwracana

A `CTime` `CTimeSpan` lub obiekt reprezentujący wynik operacji.

### <a name="remarks"></a>Uwagi

`CTime`obiekty reprezentują czas `CTimeSpan` bezwzględny, obiekty reprezentują względny czas. Pierwsze dwa operatory umożliwiają dodawanie i `CTimeSpan` odejmowanie obiektów do i z `CTime` obiektów. Trzeci operator umożliwia odjąć jeden `CTime` obiekt od drugiego, aby uzyskać `CTimeSpan` obiekt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>CTime::operator +=, -=

Te operatory dodać i `CTimeSpan` odjąć obiekt `CTime` do i z tego obiektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Obiekt, `CTimeSpan` który ma zostać dodany lub odjęty.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTime` obiekt.

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i `CTimeSpan` odejmowanie `CTime` obiektu do i z tego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>Czas CTime::Serialize64

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

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
