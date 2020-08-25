---
title: Klasa CTime
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
ms.openlocfilehash: d551698a81921227dd0d7b7d80436bba960ed176
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832038"
---
# <a name="ctime-class"></a>Klasa CTime

Reprezentuje bezwzględną godzinę i datę.

## <a name="syntax"></a>Składnia

```
class CTime
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime:: CTime](#ctime)|Tworzy `CTime` obiekty na różne sposoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime:: format](#format)|Konwertuje `CTime` obiekt na sformatowany ciąg — na podstawie lokalnej strefy czasowej.|
|[CTime:: FormatGmt](#formatgmt)|Konwertuje `CTime` obiekt na sformatowany ciąg — na podstawie czasu UTC.|
|[CTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|Konwertuje informacje o czasie przechowywane w `CTime` obiekcie na strukturę DBTIMESTAMP zgodną z systemem Win32.|
|[CTime:: GetAsSystemTime](#getassystemtime)|Konwertuje informacje o czasie przechowywane w `CTime` obiekcie na strukturę [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zgodną z systemem Win32.|
|[CTime:: GetCurrentTime](#getcurrenttime)|Tworzy `CTime` obiekt, który reprezentuje bieżący czas (statyczną funkcję członkowską).|
|[CTime:: GetDay](#getday)|Zwraca dzień reprezentujący `CTime` obiekt.|
|[CTime:: GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia reprezentowanego przez `CTime` obiekt.|
|[CTime:: GetGmtTm](#getgmttm)|Dzieli `CTime` obiekt na składniki — na podstawie czasu UTC.|
|[CTime:: GetHour](#gethour)|Zwraca godzinę reprezentowaną przez `CTime` obiekt.|
|[CTime:: GetLocalTm](#getlocaltm)|Dzieli `CTime` obiekt na składniki — na podstawie lokalnej strefy czasowej.|
|[CTime:: GetMinute](#getminute)|Zwraca minutę reprezentowaną przez `CTime` obiekt.|
|[CTime:: GetMonth](#getmonth)|Zwraca miesiąc reprezentowany przez `CTime` obiekt.|
|[CTime:: GetSecond](#getsecond)|Zwraca drugą reprezentowaną przez `CTime` obiekt.|
|[CTime:: GetTime](#gettime)|Zwraca **__time64_t** wartość dla danego `CTime` obiektu.|
|[CTime:: GetYear](#getyear)|Zwraca rok reprezentowane przez `CTime` obiekt.|
|[CTime:: Serialize64](#serialize64)|Serializować dane do lub z archiwum.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator +-](#operator_add_-)|Te operatory dodają i odejmowanie `CTimeSpan` oraz `CTime` obiektów.|
|[operator + =,-=](#operator_add_eq_-_eq)|Te operatory dodają i odejmujeją `CTimeSpan` obiekt do i z tego `CTime` obiektu.|
|[operator =](#operator_eq)|Operator przypisania.|
|[operator = =, < itd.](#ctime_comparison_operators)|Operatory porównania.|

## <a name="remarks"></a>Uwagi

`CTime` nie ma klasy bazowej.

`CTime` wartości są oparte na uniwersalnym czasie koordynowanym (UTC), który jest równoważny uniwersalnym czasowi koordynowanym (czas uniwersalny Greenwich, GMT). Zobacz [Zarządzanie czasem](../../c-runtime-library/time-management.md) , aby uzyskać informacje na temat sposobu określania strefy czasowej.

Podczas tworzenia `CTime` obiektu, należy ustawić wartość `nDST` 0, aby wskazać, że obowiązuje czas standardowy, lub do wartości większej niż 0, aby wskazać, że obowiązuje czas letni lub wartość mniejsza od zera, aby obliczyć kod biblioteki wykonawczej C, niezależnie od tego, czy obowiązuje czas standardowy czy czas letni. `tm_isdst` jest polem wymaganym. Jeśli nie zostanie ustawiona, jego wartość jest niezdefiniowana i wartość zwracana z [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) jest nieprzewidywalne. Jeśli `timeptr` wskazuje strukturę TM zwróconą przez poprzednie wywołanie do [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)lub [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` pole zawiera poprawną wartość.

Klasa pomocnika, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), reprezentuje przedział czasu.

`CTime`Klasy i `CTimeSpan` nie są przeznaczone do wyprowadzania. Ponieważ nie ma żadnych funkcji wirtualnych, rozmiar `CTime` i `CTimeSpan` obiekty są dokładnie 8 bajtami. Większość funkcji składowych jest wbudowanych.

> [!NOTE]
> Górny limit dat to 12/31/3000. Dolny limit to 1/1/1970 12:00:00 GMT.

Aby uzyskać więcej informacji o używaniu programu `CTime` , zobacz artykuł [Data i godzina](../../atl-mfc-shared/date-and-time.md)i [Zarządzanie czasem](../../c-runtime-library/time-management.md) w dokumentacji wykonawczej biblioteki.

> [!NOTE]
> `CTime`Struktura zmieniła się z mfc 7,1 na MFC 8,0. W przypadku serializacji `CTime` struktury przy użyciu **operatora <<** w bibliotece MFC 8,0 lub nowszej wersji, otrzymany plik nie będzie można odczytać we wcześniejszych wersjach MFC.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime. h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a> Operatory porównania CTime

Operatory porównania.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*pierwszym*<br/>
`CTime`Obiekt, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwa czasy bezwzględne i zwracają wartość TRUE, jeśli warunek ma wartość true. w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a> CTime:: CTime

Tworzy nowy `CTime` obiekt zainicjowany z określonym czasem.

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

*timeSrc*<br/>
Wskazuje `CTime` obiekt, który już istnieje.

*pierwszym*<br/>
`__time64_t`Wartość czasu, czyli liczba sekund od 1 stycznia 1970 czasu UTC. Należy zauważyć, że zostanie on dostosowany do czasu lokalnego. Na przykład jeśli jesteś w Nowym Jorku i utworzysz `CTime` obiekt przez przekazanie parametru 0, [CTime:: GetMonth](#getmonth) zwróci wartość 12.

*nYear*, *nMonth*, *nbłędny dzień*, *ngodzina*, *Nmin*, *NSEC*<br/>
Wskazuje wartości daty i godziny, które mają zostać skopiowane do nowego `CTime` obiektu.

*nDST*<br/>
Wskazuje, czy obowiązuje oszczędność czasu letniego. Może mieć jedną z trzech wartości:

- *NdSt* jest ustawiony na czas 0Standard.

- *NdSt* ustawiony na wartość większą niż 0Daylight oszczędności czasu.

- *NdSt* ustawiona na wartość mniejszą niż 0The default. Automatycznie oblicza, czy obowiązuje czas standardowy lub oszczędność czasu letniego.

*wDosDate*, *wDosTime*<br/>
Wartości daty i godziny systemu MS-DOS do przekonwertowania na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.

*krótkoterminow*<br/>
Struktura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) do przekonwertowania na wartość daty/godziny i skopiowana do nowego `CTime` obiektu.

*stóp*<br/>
Struktura [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) do przekonwertowania na wartość daty/godziny i skopiowana do nowego `CTime` obiektu.

*dbts*<br/>
Odwołanie do struktury DBTIMESTAMP zawierającego bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Każdy Konstruktor jest opisany poniżej:

- `CTime();` Tworzy niezainicjowany `CTime` obiekt. Ten konstruktor umożliwia definiowanie `CTime` tablic obiektów. Należy inicjować takie tablice z prawidłowymi porachmi przed użyciem.

- `CTime( const CTime& );` Konstruuje `CTime` obiekt z innej `CTime` wartości.

- `CTime( __time64_t );` Konstruuje `CTime` obiekt z typu **__time64_t** . Ten konstruktor oczekuje czasu UTC i konwertuje wynik na czas lokalny przed zapisaniem wyniku.

- `CTime( int, int, ...);` Konstruuje `CTime` obiekt z lokalnych składników czasu za pomocą każdego składnika ograniczonego do następujących zakresów:

   |Składnik|Zakres|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*Nbłędny dzień*|1-31|
   |*Ngodzina*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Ten konstruktor wykonuje odpowiednią konwersję na czas UTC. Wersja do debugowania biblioteka MFC potwierdzeń, jeśli co najmniej jeden składnik czasu jest poza zakresem. Przed wywołaniem należy sprawdzić poprawność argumentów. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( WORD, WORD );` Konstruuje `CTime` obiekt z określonych wartości daty i godziny systemu MS-DOS. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( const SYSTEMTIME& );` Konstruuje `CTime` obiekt ze `SYSTEMTIME` struktury. Ten konstruktor oczekuje czasu lokalnego.

- `CTime( const FILETIME& );` Konstruuje `CTime` obiekt ze `FILETIME` struktury. Najprawdopodobniej nie będzie można użyć `CTime FILETIME` inicjowania bezpośrednio. Jeśli używasz `CFile` obiektu do manipulowania plikiem, `CFile::GetStatus` Pobiera sygnaturę czasową pliku przez `CTime` obiekt zainicjowany przy użyciu `FILETIME` struktury. Ten konstruktor zakłada czas oparty na formacie UTC i automatycznie konwertuje wartość na czas lokalny przed zapisaniem wyniku.

   > [!NOTE]
   > Konstruktor używający `DBTIMESTAMP` parametru jest dostępny tylko wtedy, gdy jest dołączony OLEDB. h.

Aby uzyskać więcej informacji, zobacz strukturę [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) w Windows SDK. Sprawdź również [datę i godzinę systemu MS-DOS](/windows/win32/SysInfo/ms-dos-date-and-time) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a> CTime:: format

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć sformatowaną reprezentację wartości daty i godziny.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg formatowania podobny do `printf` ciągu formatowania. Kody formatowania poprzedzone znakiem procentu ( `%` ) są zastępowane przez odpowiedni `CTime` składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Zapoznaj się z funkcją Run-Time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) , aby uzyskać listę kodów formatowania.

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera sformatowany czas.

### <a name="remarks"></a>Uwagi

Jeśli stan tego `CTime` obiektu ma wartość null, zwracana wartość jest ciągiem pustym.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do sformatowania nie należy do zakresu od północy, 1 stycznia 1970 do 31 grudnia 3000 uniwersalny czas koordynowany (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a> CTime:: FormatGmt

Generuje sformatowany ciąg, który odnosi się do tego `CTime` obiektu.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Określa ciąg formatowania podobny do `printf` ciągu formatowania. Aby uzyskać szczegółowe informacje, zobacz Funkcja Run-Time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*nFormatID*<br/>
Identyfikator ciągu, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

[CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera sformatowany czas.

### <a name="remarks"></a>Uwagi

Wartość czasu nie jest konwertowana i w ten sposób odzwierciedla czas UTC.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do sformatowania nie należy do zakresu od północy, 1 stycznia 1970 do 31 grudnia 3000 uniwersalny czas koordynowany (UTC).

### <a name="example"></a>Przykład

Zobacz przykład dla [CTime:: format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> CTime:: GetAsDBTIMESTAMP

Wywołaj tę funkcję elementu członkowskiego, aby przekonwertować informacje o czasie przechowywane w `CTime` obiekcie na strukturę DBTIMESTAMP zgodną z systemem Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*dbts*<br/>
Odwołanie do struktury DBTIMESTAMP zawierającego bieżący czas lokalny.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zapisuje wyniki w strukturze *DBTS* , w której występuje odwołanie. `DBTIMESTAMP`Struktura danych zainicjowana przez tę funkcję będzie mieć swój `fraction` element członkowski ustawiony na wartość zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a> CTime:: GetAsSystemTime

Wywołaj tę funkcję elementu członkowskiego, aby przekonwertować informacje o czasie przechowywane w `CTime` obiekcie na strukturę [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zgodną z systemem Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
Odwołanie do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , która będzie zawierać przekonwertowaną wartość daty/godziny `CTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime` zapisuje wyniki w strukturze *timeDest* , w której występuje odwołanie. `SYSTEMTIME`Struktura danych zainicjowana przez tę funkcję będzie mieć swój `wMilliseconds` element członkowski ustawiony na wartość zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a> CTime:: GetCurrentTime

Zwraca `CTime` obiekt, który reprezentuje bieżący czas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca bieżącą datę i godzinę systemową w uniwersalnym czasie koordynowanym (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a> CTime:: GetDay

Zwraca dzień reprezentujący `CTime` obiekt.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień miesiąca, na podstawie czasu lokalnego, z zakresu od 1 do 31.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a> CTime:: GetDayOfWeek

Zwraca dzień tygodnia reprezentowanego przez `CTime` obiekt.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień tygodnia na podstawie czasu lokalnego; 1 = niedziela, 2 = poniedziałek, do 7 = Sobota.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a> CTime:: GetGmtTm

Pobiera **strukturę TM** , która zawiera dekompozycję czasu zawartego w tym `CTime` obiekcie.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Wskazuje bufor, który będzie otrzymywał dane czasu. Jeśli ten wskaźnik ma wartość NULL, zostanie zgłoszony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełnionej **struktury TM** , zgodnie z definicją w polu Uwzględnij plik. C. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) do układu struktury.

### <a name="remarks"></a>Uwagi

`GetGmtTm` Zwraca wartość czasu UTC.

*PTM* nie może mieć wartości null. Jeśli chcesz przywrócić stare zachowanie, w którym *PTM* może mieć wartość null, aby wskazać, że należy użyć wewnętrznego, statycznie przydzieloną bufora, a następnie usuń definicję _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a> CTime:: GetHour

Zwraca godzinę reprezentowaną przez `CTime` obiekt.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca godzinę w oparciu o czas lokalny, w zakresie od 0 do 23.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a> CTime:: GetLocalTm

Pobiera **strukturę** , która zawiera dekompozycję czasu zawartego w tym `CTime` obiekcie.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Wskazuje bufor, który będzie otrzymywał dane czasu. Jeśli ten wskaźnik ma wartość NULL, zostanie zgłoszony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełnionej **struktury TM** , zgodnie z definicją w polu Uwzględnij plik. C. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) do układu struktury.

### <a name="remarks"></a>Uwagi

`GetLocalTm` Zwraca czas lokalny.

*PTM* nie może mieć wartości null. Jeśli chcesz przywrócić stare zachowanie, w którym *PTM* może mieć wartość null, aby wskazać, że należy użyć wewnętrznego, statycznie przydzieloną bufora, a następnie usuń definicję _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a> CTime:: GetMinute

Zwraca minutę reprezentowaną przez `CTime` obiekt.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca minutę na podstawie czasu lokalnego, z zakresu od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a> CTime:: GetMonth

Zwraca miesiąc reprezentowany przez `CTime` obiekt.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca miesiąc, na podstawie czasu lokalnego, z zakresu od 1 do 12 (1 = styczeń).

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład dla [getDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a> CTime:: GetSecond

Zwraca drugą reprezentowaną przez `CTime` obiekt.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca sekundę, na podstawie czasu lokalnego, z zakresu od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a> CTime:: GetTime

Zwraca **__time64_t** wartość dla danego `CTime` obiektu.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Wartość zwracana

`GetTime` zwróci liczbę sekund między bieżącym `CTime` obiektem a 1 stycznia 1970.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a> CTime:: GetYear

Zwraca rok reprezentowane przez `CTime` obiekt.

```
int GetYear();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rok, w oparciu o czas lokalny, w zakresie od 1 stycznia 1970 r. do 18 stycznia 2038 (włącznie).

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm` , która używa wewnętrznego, statycznie przydzielony bufor. Dane w tym buforze są zastępowane ze względu na wywołania innych `CTime` funkcji Członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład dla [getDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a> CTime:: operator =

Operator przypisania.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*pierwszym*<br/>
Nowa wartość daty/godziny.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTime` obiekt.

### <a name="remarks"></a>Uwagi

Ten przeciążony operator przypisania kopiuje czas źródłowy do tego `CTime` obiektu. Wewnętrzny magazyn czasu w `CTime` obiekcie jest niezależny od strefy czasowej. Konwersja strefy czasowej nie jest konieczna podczas przypisywania.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a> CTime:: operator +,-

Te operatory dodają i odejmowanie `CTimeSpan` oraz `CTime` obiektów.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Czasu*<br/>
`CTimeSpan`Obiekt, który ma zostać dodany lub ododejmowany.

*pierwszym*<br/>
`CTime`Obiekt, który ma zostać odjęty.

### <a name="return-value"></a>Wartość zwracana

`CTime`Obiekt lub `CTimeSpan` reprezentujący wynik operacji.

### <a name="remarks"></a>Uwagi

`CTime` obiekty reprezentują czas bezwzględny, `CTimeSpan` obiekty reprezentują czas względny. Pierwsze dwa operatory umożliwiają dodawanie i odejmowanie `CTimeSpan` obiektów do i z `CTime` obiektów. Trzeci operator umożliwia odjęcie jednego `CTime` obiektu od drugiego w celu uzyskania `CTimeSpan` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a> CTime:: operator + =,-=

Te operatory dodają i odejmujeją `CTimeSpan` obiekt do i z tego `CTime` obiektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CTimeSpan`Obiekt, który ma zostać dodany lub ododejmowany.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany `CTime` obiekt.

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i odejmowanie `CTimeSpan` obiektu do i z tego `CTime` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a> CTime:: Serialize64

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

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
