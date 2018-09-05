---
title: CTime, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTime
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
dev_langs:
- C++
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 758a62b0d93b93798004470de47af2fd3a7ca2eb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765213"
---
# <a name="ctime-class"></a>CTime, klasa

Reprezentuje bezwzględnego czasu i daty.

## <a name="syntax"></a>Składnia

```
class CTime  
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime::CTime](#ctime)|Konstruuje `CTime` obiektów na różne sposoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTime::Format](#format)|Konwertuje `CTime` obiekt na ciąg sformatowany — oparte na podstawie lokalnej strefy czasowej.|
|[CTime::FormatGmt](#formatgmt)|Konwertuje `CTime` obiekt na ciąg sformatowany — oparty na czasie UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Konwertuje czas informacji przechowywanych w `CTime` obiektu do struktury odcisk CZASOWY zgodnego z Win32.|
|[CTime::GetAsSystemTime](#getassystemtime)|Konwertuje czas informacji przechowywanych w `CTime` obiektu Win32 zgodnych [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.|
|[CTime::GetCurrentTime](#getcurrenttime)|Tworzy `CTime` obiekt, który reprezentuje bieżący czas (statyczny element członkowski funkcji).|
|[CTime::GetDay](#getday)|Zwraca reprezentują dnia przez `CTime` obiektu.|
|[CTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia, reprezentowane przez `CTime` obiektu.|
|[CTime::GetGmtTm](#getgmttm)|Dzieli `CTime` obiektu na składniki — oparty na czasie UTC.|
|[CTime::GetHour](#gethour)|Zwraca wartość godziny w postaci `CTime` obiektu.|
|[CTime::GetLocalTm](#getlocaltm)|Dzieli `CTime` obiektu na składniki — oparte na podstawie lokalnej strefy czasowej.|
|[CTime::GetMinute](#getminute)|Zwraca minuty, reprezentowane przez `CTime` obiektu.|
|[CTime::GetMonth](#getmonth)|Zwraca miesiąc, reprezentowane przez `CTime` obiektu.|
|[CTime::GetSecond](#getsecond)|Zwraca sekundy, reprezentowane przez `CTime` obiektu.|
|[CTime::GetTime](#gettime)|Zwraca **__time64_t —** wartość danego `CTime` obiektu.|
|[CTime::GetYear](#getyear)|Zwraca rok, reprezentowane przez `CTime` obiektu.|
|[CTime::Serialize64](#serialize64)|Serializuje dane do / z archiwum.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator + —](#operator_add_-)|Te operatory dodawania i odejmowania `CTimeSpan` i `CTime` obiektów.|
|[operator +=-=](#operator_add_eq_-_eq)|Te operatory dodawania i odejmowania `CTimeSpan` obiektów do i z tego `CTime` obiektu.|
|[operator =](#operator_eq)|Operator przypisania.|
|[operator ==, < itp.](#ctime_comparison_operators)|Operatory porównania.|

## <a name="remarks"></a>Uwagi

`CTime` nie ma klasy bazowej.

`CTime` wartości są oparte na uniwersalny czas koordynowany (UTC), który jest odpowiednikiem uniwersalny czas koordynowany (czas uniwersalny Greenwich, GMT). Zobacz [zarządzanie czasem](../../c-runtime-library/time-management.md) informacji o sposobie strefy czasowej.

Po utworzeniu `CTime` obiektu, należy ustawić `nDST` parametru na wartość 0, aby wskazać, że obowiązuje (czas standardowy) lub na wartość większą niż 0, aby wskazać, że czasu letniego obowiązuje lub wartość niższą niż zero, aby komput kodu biblioteki wykonawczej języka C e czy (czas standardowy) lub czasu jest aktywna. `tm_isdst` pole jest wymagane. Jeśli nie jest ustawiona, jej wartość jest niezdefiniowana i wartość zwrotną z elementu [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) jest nieprzewidywalne. Jeśli `timeptr` wskazuje na strukturę tm zwrócony przez poprzednie wywołanie [asctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s —](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), lub [localtime_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` pole zawiera poprawnej wartości.

Klasa pomocnika, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), reprezentuje przedział czasu.

`CTime` i `CTimeSpan` klasy nie są przeznaczone do tworzenie wartości pochodnych. Ponieważ żadnych funkcji wirtualnych rozmiaru `CTime` i `CTimeSpan` obiektów jest dokładnie 8 bajtów. Większość elementów członkowskich są wbudowane.

> [!NOTE]
>  Limit górny data to 12/31/3000. Dolna granica jest 1/1/1970 r. 00:00:00 GMT.

Aby uzyskać więcej informacji o korzystaniu z `CTime`, zobacz artykuły [daty i godziny](../../atl-mfc-shared/date-and-time.md), i [zarządzanie czasem](../../c-runtime-library/time-management.md) w odwołaniu biblioteki wykonawczej.

> [!NOTE]
>  `CTime` Struktury zmieniła się z MFC 7.1 do MFC 8.0. Jeśli serializujesz `CTime` struktury za pomocą **operator <<** w ramach MFC 8.0 lub nowszej, wynikowy plik nie będzie można odczytać na starsze wersje biblioteki MFC.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

##  <a name="ctime_comparison_operators"></a>  Ctime — operatory

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

*czas*  
`CTime` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Te operatory porównują dwa razy bezwzględne i zwracają wartość TRUE, jeśli warunek jest prawdziwy; w przeciwnym razie wartość FALSE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

Tworzy nową `CTime` obiekt został zainicjowany przy użyciu określonego czasu.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts,int nDST = -1) throw();
```

### <a name="parameters"></a>Parametry

*timeSrc*  
Wskazuje `CTime` obiekt, który już istnieje.

*czas*  
A **__time64_t —** wartość czasu, która jest to liczba sekund po 1 stycznia 1970 r. UTC. Należy pamiętać, że to zostaną skorygowane czasu lokalnego. Na przykład, jeśli znajdują się w Nowym Jorku i Utwórz `CTime` obiektu przez przekazanie parametru 0, [CTime::GetMonth](#getmonth) zwróci 12.  


*nYear*, *nMonth*, *nbłędny dzień*, *Ngodzina*, *nMin*, *nSec*  
Wskazuje wartości daty i godziny do skopiowania w nowe `CTime` obiektu.

*nDST*  
Wskazuje, czy czas letni jest aktywna. Może mieć jedną z trzech wartości:

- *nDST* zestaw 0Standard czasu jest aktywna.

- *nDST* ustawiona na wartość większą niż 0Daylight czasu jest aktywna.

- *nDST* ustawiony na wartość mniejszą niż domyślne 0The. Automatycznie oblicza, czy (czas standardowy) lub czas letni jest aktywna.

*wDosDate*, *wDosTime*  
Wartości daty i godziny może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego systemu MS-DOS `CTime` obiektu.

*St*  
A [SYSTEMTIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d6609fff-1931-4818-8a26-f042630af0b0/locales/en-us) struktura może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.

*FT*  
A [FILETIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/979ce746-dc17-4147-89f8-41d05c5fcc5f/locales/en-us) struktura może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.

znacznika dbts  
Odwołanie do struktury odcisk CZASOWY zawierającej bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Poniżej opisano każdy Konstruktor:

- `CTime();` Tworzy niezainicjowany `CTime` obiektu. Ten konstruktor pozwala na zdefiniowanie `CTime` obiektu tablic. Należy zainicjować tymi macierzami prawidłowy czas przed użyciem.

- `CTime( const CTime& );` Konstruuje `CTime` obiektu z innego `CTime` wartość.

- `CTime( __time64_t );` Konstruuje `CTime` obiektu z **__time64_t —** typu. Ten konstruktor oczekuje, że czas UTC i konwertuje wynik na czas lokalny przed zachowaniem wyniku.

- `CTime( int, int, ...);` Konstruuje `CTime` obiektu na podstawie czasu lokalnego składników za pomocą każdego składnika ograniczone do następujących zakresów:

   |Składnik|Zakres|  
   |---------------|-----------|  
   |*nYear*|1970-3000|  
   |*nMonth*|1-12|  
   |*nbłędny dzień*|1-31|  
   |*Ngodzina*|0-23|  
   |*Nmin.*|0-59|  
   |*rekordy nSec*|0-59|

   Ten konstruktor sprawia, że odpowiednie konwersji na czas UTC. Wersję debugowania biblioteki klas Microsoft Foundation potwierdzenia, jeśli jeden lub więcej składników czasu są poza zakresem. Należy sprawdzić, argumenty przed wywołaniem. Ten konstruktor oczekuje, że czas lokalny.

- `CTime( WORD, WORD );` Konstruuje `CTime` obiektu z określonej wartości daty i godziny systemu MS-DOS. Ten konstruktor oczekuje, że czas lokalny.

- `CTime( const SYSTEMTIME& );` Konstruuje `CTime` obiektu z `SYSTEMTIME` struktury. Ten konstruktor oczekuje, że czas lokalny.

- `CTime( const FILETIME& );` Konstruuje `CTime` obiektu z `FILETIME` struktury. Najprawdopodobniej nie będzie używać `CTime FILETIME` inicjowania bezpośrednio. Jeśli używasz `CFile` obiekt do manipulowania plikiem `CFile::GetStatus` pobiera sygnatury czasowej pliku dla Ciebie za pośrednictwem `CTime` obiekt inicjowany za pomocą `FILETIME` struktury. Ten konstruktor przyjmuje czasu, oparty na czasie UTC i automatycznie konwertuje wartość na czas lokalny, przed zachowaniem wyniku.

   > [!NOTE]
   > Za pomocą konstruktora `DBTIMESTAMP` parametr jest dostępna tylko, gdy OLEDB.h jest dołączony.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) struktury w zestawie Windows SDK. Zobacz też [MS-DOS daty i godziny](/windows/desktop/SysInfo/ms-dos-date-and-time) wejścia w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć sformatowany reprezentację wartości daty / godziny.

```
CString Format(LPCTSTR pszFormat) const; 
CString Format(UINT nFormatID) const; 
```

### <a name="parameters"></a>Parametry

*pszFormat*  
Formatowanie ciągów podobne do `printf` ciąg formatowania. Formatowanie kodów, poprzedzony procent (`%`) Zaloguj się, są zastępowane przez odpowiednie `CTime` składnika. Inne znaki do ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Zobacz opis funkcji wykonawczej [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) listę kody formatowania.

*nFormatID*  
Identyfikator ciąg, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawiera sformatowaną czasu.

### <a name="remarks"></a>Uwagi

Jeśli stan to `CTime` obiekt ma wartość null, wartość zwracana jest ciągiem pustym.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do sformatowania mieści się w zakresie od północy 1 stycznia 1970 r. do 31 grudnia 3000 uniwersalnego czasu koordynowanego (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

Generuje sformatowany ciąg, który odnosi się do tego `CTime` obiektu.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*  
Określa ciąg formatowania, podobnie jak `printf` ciąg formatowania. Zobacz opis funkcji wykonawczej [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać szczegółowe informacje.

*nFormatID*  
Identyfikator ciąg, który identyfikuje ten format.

### <a name="return-value"></a>Wartość zwracana

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawiera sformatowaną czasu.

### <a name="remarks"></a>Uwagi

Wartość czasu nie jest konwertowany i dlatego odzwierciedla UTC.

Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do sformatowania mieści się w zakresie od północy 1 stycznia 1970 r. do 31 grudnia 3000 uniwersalnego czasu koordynowanego (UTC).

### <a name="example"></a>Przykład

Zobacz przykład [CTime::Format](#format).

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

Wywołaj tę funkcję elementu członkowskiego, aby przekonwertować czasu informacji przechowywanych w `CTime` obiektu do struktury odcisk CZASOWY zgodnego z Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*znacznika dbts*  
Odwołanie do struktury odcisk CZASOWY zawierającej bieżący czas lokalny.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zapisuje wynikowy czas w występujących w odwołaniu *znacznika dbts* struktury. `DBTIMESTAMP` Struktury danych, które inicjowane przez tę funkcję będzie miał jego `fraction` element członkowski należy ustawić na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

Wywołaj tę funkcję elementu członkowskiego, aby przekonwertować czasu informacji przechowywanych w `CTime` obiektu Win32 zgodnych [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest*  
Odwołanie do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która będzie przechowywać wartość daty/godziny przekonwertowanego `CTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime` zapisuje wynikowy czas w występujących w odwołaniu *timeDest* struktury. `SYSTEMTIME` Struktury danych, które inicjowane przez tę funkcję będzie miał jego `wMilliseconds` element członkowski należy ustawić na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

Zwraca `CTime` obiekt, który reprezentuje bieżący czas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Uwagi

Zwraca datę i godzinę w uniwersalnego czasu koordynowanego (UTC).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

Zwraca reprezentują dnia przez `CTime` obiektu.

```
int GetDay() const throw(); 
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień miesiąca, w oparciu o czas lokalny, w zakresie od 1 do 31.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa buforu wewnętrznego, statycznie przydzielanego. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

Zwraca dzień tygodnia, reprezentowane przez `CTime` obiektu.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dzień tygodnia, w oparciu o czas lokalny; 1 = niedziela, 2 = poniedziałek, sobota = 7.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

Pobiera **tm struktury** zawierający rozkładu czasu zawarte w tym `CTime` obiektu.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*  
Wskazuje buforu, który będzie otrzymywać dane czasu. Jeśli ten wskaźnik ma wartość NULL, jest zgłaszany wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełniane **tm struktury** zgodnie z definicją w dołączanym pliku czasu. H. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) w układzie struktury.

### <a name="remarks"></a>Uwagi

`GetGmtTm` Zwraca wartość czasu UTC.

*ptm* nie może mieć wartości NULL. Jeśli chcesz powrócić do starego zachowania, w którym *ptm* wartości NULL, aby wskazać, że może być wewnętrzny statycznie przydzielonego buforu powinien być używany, następnie usuń _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

Zwraca wartość godziny w postaci `CTime` obiektu.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca godzinę na podstawie czasu lokalnego, w zakresie od 0 do 23.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

Pobiera **tm struktury** zawierający rozkładu czasu zawarte w tym `CTime` obiektu.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*  
Wskazuje buforu, który będzie otrzymywać dane czasu. Jeśli ten wskaźnik ma wartość NULL, jest zgłaszany wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wypełniane **tm struktury** zgodnie z definicją w dołączanym pliku czasu. H. Zobacz [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) w układzie struktury.

### <a name="remarks"></a>Uwagi

`GetLocalTm` Zwraca czas lokalny.

*ptm* nie może mieć wartości NULL. Jeśli chcesz powrócić do starego zachowania, w którym *ptm* wartości NULL, aby wskazać, że może być wewnętrzny statycznie przydzielonego buforu powinien być używany, następnie usuń _SECURE_ATL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

Zwraca minuty, reprezentowane przez `CTime` obiektu.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę minut, na podstawie czasu lokalnego, w zakresie od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [GetHour](#gethour).

##  <a name="getmonth"></a>  CTime::GetMonth

Zwraca miesiąc, reprezentowane przez `CTime` obiektu.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca miesiąc w oparciu o czas lokalny, w zakresie od 1 do 12 (1 stycznia =).

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [GetDay](#getday).

##  <a name="getsecond"></a>  CTime::GetSecond

Zwraca sekundy, reprezentowane przez `CTime` obiektu.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca sekundy w oparciu o czas lokalny, w zakresie od 0 do 59.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [GetHour](#gethour).

##  <a name="gettime"></a>  CTime::GetTime

Zwraca **__time64_t —** wartość danego `CTime` obiektu.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Wartość zwracana

`GetTime` Zwraca liczbę sekund między bieżącą `CTime` obiektu i 1 stycznia 1970.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

Zwraca rok, reprezentowane przez `CTime` obiektu.

```
int GetYear();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rok, na podstawie czasu lokalnego, w zakresie stycznia 1,1970 do 18 stycznia 2038 (włącznie).

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje `GetLocalTm`, który używa wewnętrznego statycznie przydzielonych buforu. Dane w buforze ten zostanie zastąpiony z powodu wywołań do innych `CTime` funkcji elementów członkowskich.

### <a name="example"></a>Przykład

Zobacz przykład [GetDay](#getday).

##  <a name="operator_eq"></a>  CTime::operator =

Operator przypisania.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*czas*  
Wartość nowego daty/godziny.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany interfejs `CTime` obiektu.

### <a name="remarks"></a>Uwagi

Ten operator przypisania przeciążona kopiuje źródła czasu do tego `CTime` obiektu. Czas wewnętrznego magazynu `CTime` obiektu jest niezależna od stref czasowych. Podczas przypisywania konwersji strefy czasowej nie jest konieczne.

##  <a name="operator_add_-"></a>  CTime::operator +, -

Te operatory dodawania i odejmowania `CTimeSpan` i `CTime` obiektów.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Przedział czasu*  
`CTimeSpan` Obiekt, aby być dodawane lub odejmowane.

*czas*  
`CTime` Obiektu do odjęcia.

### <a name="return-value"></a>Wartość zwracana

A `CTime` lub `CTimeSpan` obiekt reprezentujący wynik operacji.

### <a name="remarks"></a>Uwagi

`CTime` obiekty reprezentują bezwzględnego czasu `CTimeSpan` obiekty reprezentują godziny względne. Pierwsze dwa operatory pozwalają na dodawanie i odejmowanie `CTimeSpan` obiektów do i z `CTime` obiektów. Trzeci operator pozwala na potrzeby odejmowania jeden `CTime` obiektu z innego umożliwiające uzyskanie `CTimeSpan` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator +=-=

Te operatory dodawania i odejmowania `CTimeSpan` obiektów do i z tego `CTime` obiektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*  
`CTimeSpan` Obiekt, aby być dodawane lub odejmowane.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany interfejs `CTime` obiektu.

### <a name="remarks"></a>Uwagi

Te operatory pozwalają na dodawanie i odejmowanie `CTimeSpan` obiektów do i z tego `CTime` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> Ta metoda jest dostępna tylko w projektach MFC.

Serializuje dane skojarzone ze zmienną elementu członkowskiego do lub z archiwum.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*  
`CArchive` Obiekt, który chcesz zaktualizować.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany interfejs `CArchive` obiektu.

## <a name="see-also"></a>Zobacz też

[asctime_s —, _wasctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
[_ftime_s _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
[localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)   
[Diagram hierarchii](../../mfc/hierarchy-chart.md)   
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
