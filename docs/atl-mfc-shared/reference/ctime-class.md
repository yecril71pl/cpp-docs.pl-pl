---
title: Ctime — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8ec195c7733255487b08f8b48379abe58e305f61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ctime-class"></a>Ctime — klasa
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
|[CTime::Format](#format)|Konwertuje `CTime` obiektu na ciąg sformatowany — oparte na podstawie lokalnej strefy czasowej.|  
|[CTime::FormatGmt](#formatgmt)|Konwertuje `CTime` obiektu na ciąg sformatowany — oparte na czas UTC.|  
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Konwertuje przechowywanych w informacje o czasie `CTime` obiektu do struktury odcisk CZASOWY zgodnego Win32.|  
|[CTime::GetAsSystemTime](#getassystemtime)|Konwertuje przechowywanych w informacje o czasie `CTime` obiektu Win32 zgodnych [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.|  
|[CTime::GetCurrentTime](#getcurrenttime)|Tworzy `CTime` obiekt, który reprezentuje bieżący czas (statycznej funkcji członkowskiej).|  
|[CTime::GetDay](#getday)|Zwraca reprezentuje dzień przez `CTime` obiektu.|  
|[CTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia reprezentowany przez `CTime` obiektu.|  
|[CTime::GetGmtTm](#getgmttm)|Dzieli `CTime` obiektu na składniki — oparte na czas UTC.|  
|[CTime::GetHour](#gethour)|Zwraca godzinę reprezentowany przez `CTime` obiektu.|  
|[CTime::GetLocalTm](#getlocaltm)|Dzieli `CTime` obiektu na składniki — oparte na podstawie lokalnej strefy czasowej.|  
|[CTime::GetMinute](#getminute)|Zwraca minutę reprezentowany przez `CTime` obiektu.|  
|[CTime::GetMonth](#getmonth)|Zwraca miesiąc reprezentowany przez `CTime` obiektu.|  
|[CTime::GetSecond](#getsecond)|Zwraca drugie reprezentowany przez `CTime` obiektu.|  
|[CTime::GetTime](#gettime)|Zwraca **__time64_t —** wartość dla danego `CTime` obiektu.|  
|[CTime::GetYear](#getyear)|Zwraca rok reprezentowany przez `CTime` obiektu.|  
|[CTime::Serialize64](#serialize64)|Serializuje dane do lub z archiwum.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator + —](#operator_add_-)|Tych operatorów dodawania i odejmowania `CTimeSpan` i `CTime` obiektów.|  
|[operator +=-=](#operator_add_eq_-_eq)|Tych operatorów dodawania i odejmowania `CTimeSpan` obiekt do i z tego `CTime` obiektu.|  
|[operator =](#operator_eq)|Operator przypisania.|  
|[operator ==, < itp.](#ctime_comparison_operators)|Operatory porównania.|  
  
## <a name="remarks"></a>Uwagi  
 `CTime` nie ma klasy podstawowej.  
  
 `CTime` wartości są oparte na uniwersalny czas koordynowany (UTC), który jest odpowiednikiem uniwersalny czas koordynowany (czas uniwersalny Greenwich, GMT). Zobacz [zarządzanie czasem](../../c-runtime-library/time-management.md) informacji o jak ustalona strefę czasową.  
  
 Po utworzeniu `CTime` obiekt, ustaw `nDST` parametru na wartość 0, aby wskazać, że (czas standardowy) jest włączona, lub na wartość większą niż 0, aby wskazać, że czasu jest włączona, lub na wartość mniejszą niż zero, aby mieć komput kod biblioteki wykonawczej języka C e czy (czas standardowy) lub czas letni jest włączona. `tm_isdst` pole jest wymagane. Jeśli nie jest ustawiona, jej wartości są niezdefiniowane i wartość zwrotną z elementu [mktime —](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) będzie nieprzewidywalny. Jeśli `timeptr` wskazuje na strukturę tm zwrócony przez poprzednie wywołanie [asctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s —](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), lub [localtime_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` pole zawiera poprawną wartość.  
  
 Klasa pomocnika, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), reprezentuje przedział czasu.  
  
 `CTime` i `CTimeSpan` klasy nie są przeznaczone do wyprowadzenia. Ponieważ nie żadnych funkcji wirtualnych rozmiar `CTime` i `CTimeSpan` obiektów jest dokładnie 8 bajtów. Większość funkcji elementów członkowskich są wbudowane.  
  
> [!NOTE]
>  Limit Górna data to 12/31/3000. Dolna granica jest 1/1/1970 12:00:00 AM GMT.  
  
 Aby uzyskać więcej informacji o korzystaniu z `CTime`, zobacz artykuły [Data i godzina](../../atl-mfc-shared/date-and-time.md), i [zarządzanie czasem](../../c-runtime-library/time-management.md) w odwołaniu biblioteki czasu wykonywania.  
  
> [!NOTE]
>  `CTime` Struktury zmieniła się z MFC 7.1 do MFC 8.0. Jeśli można serializować `CTime` struktury przy użyciu `operator <<` w MFC 8.0 lub nowszej wersji, wynikowy plik nie będzie można odczytać na starsze wersje biblioteki MFC.  
  
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
 `time`  
 `CTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tych operatorów porównywania dwa razy bezwzględne i zwracać **true** Jeśli wynikiem warunku jest PRAWDA; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]  
  
##  <a name="ctime"></a>  CTime::CTime  
 Tworzy nową `CTime` obiektu zainicjowane z określonego czasu.  
  
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
 `timeSrc`  
 Wskazuje `CTime` obiektu, który już istnieje.  
  
 `time`  
 A **__time64_t —** wartość czasu, która jest to liczba sekund po 1 stycznia 1970 UTC. Należy pamiętać, że to zostanie dostosowana do czasu lokalnego. Na przykład, jeśli znajdują się w Nowym Jorku i Utwórz `CTime` obiektu przez przekazywanie parametru o wartości 0, [CTime::GetMonth](#getmonth) zwróci 12.  

  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Wskazuje, wartości daty i godziny można skopiować do nowego `CTime` obiektu.  
  
 `nDST`  
 Wskazuje, czy czasu letniego jest włączona. Może mieć jedną z trzech wartości:  
  
- `nDST` wartość czasu 0Standard jest włączona.  
  
- `nDST` ustawiona na wartość większą niż 0Daylight, który czasu jest włączona.  
  
- `nDST` Ustaw na wartość mniejszą niż domyślne 0The. Automatycznie oblicza, czy czas standardowy lub czasu letniego jest włączona.  
  
 `wDosDate`, `wDosTime`  
 Wartości daty i godziny można przekonwertować na wartość daty/godziny i skopiowane do nowego systemu MS-DOS `CTime` obiektu.  
  
 `st`  
 A [SYSTEMTIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d6609fff-1931-4818-8a26-f042630af0b0/locales/en-us) struktury można przekonwertować na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.  
  
 `ft`  
 A [FILETIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/979ce746-dc17-4147-89f8-41d05c5fcc5f/locales/en-us) struktury można przekonwertować na wartość daty/godziny i skopiowane do nowego `CTime` obiektu.  
  
 znacznika dbts  
 Odwołanie do struktury odcisk CZASOWY zawierający bieżącym czasem lokalnym.  
  
### <a name="remarks"></a>Uwagi  
 Poniżej opisano każdy konstruktora:  
  
- **CTime();**  Tworzy niezainicjowany `CTime` obiektu. Ten konstruktor służy do definiowania `CTime` obiekt tablic. Należy zainicjować takie tablic o prawidłowe godziny przed użyciem.  
  
- **Ctime — (const ctime — &);**  Tworzy `CTime` obiektu z innego `CTime` wartość.  
  
- **Ctime — (__time64_t —);**  Tworzy `CTime` obiekt z **__time64_t —** typu. Ten konstruktor oczekuje czas UTC i konwertuje wynik na czas lokalny przed przekazaniem wynik.  
  
- **Ctime — (int, int,...);**  Tworzy `CTime` obiektu ze składników czas lokalny z każdego składnika ograniczone do następujących zakresów:  
  
    |Składnik|Zakres|  
    |---------------|-----------|  
    |`nYear`|1970-3000|  
    |`nMonth`|1-12|  
    |`nDay`|1-31|  
    |`nHour`|0-23|  
    |`nMin`|0-59|  
    |`nSec`|0-59|  
  
     Ten konstruktor sprawia, że odpowiednie konwersji na czas UTC. Wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń, jeśli jeden lub większa liczba instalowanych składników czasu przypada poza zakresem. Należy sprawdzić argumenty przed wywołaniem. Ten konstruktor oczekuje czasu lokalnego.  
  
- **Ctime — (WORD, wyraz);**  Tworzy `CTime` obiektu z określonej wartości daty i godziny systemu MS-DOS. Ten konstruktor oczekuje czasu lokalnego.  
  
- **Ctime — (const SYSTEMTIME &);**  Tworzy `CTime` obiekt z `SYSTEMTIME` struktury. Ten konstruktor oczekuje czasu lokalnego.  
  
- **Ctime — (const FILETIME &);**  Tworzy `CTime` obiekt z `FILETIME` struktury. Prawdopodobnie nie będzie używać `CTime FILETIME` inicjowania bezpośrednio. Jeśli używasz `CFile` obiekt do manipulowania pliku `CFile::GetStatus` pobiera sygnaturę czasową pliku dla użytkownika przez proces `CTime` zainicjować obiektu z `FILETIME` struktury. Ten konstruktor przyjęto założenie, czas, w oparciu o czas UTC i automatycznie konwertuje wartość na czas lokalny przed przekazaniem wynik.  
  
    > [!NOTE]
    >  Za pomocą konstruktora **odcisk CZASOWY** parametru jest dostępna tylko, gdy OLEDB.h jest dołączony.  
  
 Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury w zestawie Windows SDK. Zobacz też [MS-DOS Data i godzina](http://msdn.microsoft.com/library/windows/desktop/ms724503) wejścia w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]  
  
##  <a name="format"></a>  CTime::Format  
 Wywołanie tej funkcji członkowskich można utworzyć sformatowane reprezentację wartości daty i godziny.  
  
```  
CString Format(LPCTSTR pszFormat) const; 
CString Format(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Formatowanie ciąg podobny do `printf` ciąg formatowania. Formatowanie kodów poprzedzone w procentach ( `%`) podpisania, są zastępowane przez odpowiednie `CTime` składnika. Zwrócony ciąg jest kopiowana niezmienione innych znaków w ciągu formatowania. Zobacz opis funkcji środowiska wykonawczego [strftime —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) listę kody formatowania.  
  
 `nFormatID`  
 Identyfikator ciągu, która identyfikuje ten format.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający sformatowany czasu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli stan to `CTime` obiektu ma wartość null, zwracana wartość jest pustym ciągiem.  
  
 Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do formatowania nie należeć do zakresu od północy, 1 stycznia 1970 r. do 31 grudnia 3000 uniwersalnego czasu koordynowanego (UTC).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]  
  
##  <a name="formatgmt"></a>  CTime::FormatGmt  
 Generuje ciąg formatowania, który odpowiada to `CTime` obiektu.  
  
```  
CString FormatGmt(LPCTSTR pszFormat) const; 
CString FormatGmt(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Określa ciąg formatowania, podobnie jak `printf` ciąg formatowania. Zobacz opis funkcji środowiska wykonawczego [strftime —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) szczegółowe informacje.  
  
 `nFormatID`  
 Identyfikator ciągu, która identyfikuje ten format.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający sformatowany czasu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość czasu nie jest konwertowany i w związku z tym odzwierciedla UTC.  
  
 Ta metoda zgłasza wyjątek, jeśli wartość daty i godziny do formatowania nie należeć do zakresu od północy, 1 stycznia 1970 r. do 31 grudnia 3000 uniwersalnego czasu koordynowanego (UTC).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CTime::Format](#format).  
  
##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP  
 Wywołanie tej funkcji członkowskich można przekonwertować czasu informacje przechowywane w `CTime` obiektu do struktury odcisk CZASOWY zgodnego Win32.  
  
```  
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dbts`  
 Odwołanie do struktury odcisk CZASOWY zawierający bieżącym czasem lokalnym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje wynikowy czas w przywoływana `dbts` struktury. **Odcisk CZASOWY** zainicjowane przez tę funkcję struktura danych będzie mieć jego **ułamek** zestaw elementów członkowskich na zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]  
  
##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime  
 Wywołanie tej funkcji członkowskich można przekonwertować czasu informacje przechowywane w `CTime` obiektu Win32 zgodnych [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.  
  
```  
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *timeDest*  
 Odwołanie do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury, który będzie zawierał wartość przekonwertowanego daty/godziny `CTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość true, jeśli pomyślnie; w przeciwnym razie wartość false.  
  
### <a name="remarks"></a>Uwagi  
 `GetAsSystemTime` przechowuje wynikowy czas w przywoływana *timeDest* struktury. `SYSTEMTIME` Zainicjowane przez tę funkcję struktura danych będzie mieć jego **wMilliseconds** zestaw elementów członkowskich na zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]  
  
##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime  
 Zwraca `CTime` obiekt, który reprezentuje bieżący czas.  
  
```  
static CTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca bieżącej systemowej daty i czasu uniwersalnego czasu koordynowanego (UTC).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]  
  
##  <a name="getday"></a>  CTime::GetDay  
 Zwraca reprezentuje dzień przez `CTime` obiektu.  
  
```  
int GetDay() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dzień miesiąca, na podstawie czasu lokalnego, w zakresie od 1 do 31.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa buforu wewnętrznego, statycznie przydzielone. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]  
  
##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek  
 Zwraca dzień tygodnia reprezentowany przez `CTime` obiektu.  
  
```  
int GetDayOfWeek() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dzień tygodnia, w oparciu o czas lokalny; 1 = niedziela, 2 = poniedziałek, 7 = sobota.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]  
  
##  <a name="getgmttm"></a>  CTime::GetGmtTm  
 Pobiera **tm struktury** zawierający rozkładu czasu zawarte w tym `CTime` obiektu.  
  
```  
struct tm* GetGmtTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `ptm`  
 Wskazuje buforu, który będzie odbierać dane czasu. Jeśli ten wskaźnik jest **NULL**, jest zgłaszany wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wypełniane **tm struktury** zgodnie z definicją w pliku dołączanego czasu. H. Zobacz [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) w układzie struktury.  
  
### <a name="remarks"></a>Uwagi  
 `GetGmtTm` Zwraca czas UTC.  
  
 `ptm` nie może być `NULL`. Jeśli chcesz przywrócić poprzednie działanie, w którym `ptm` może być `NULL` do wskazuje, czy bufor wewnętrzny, statycznie przydzielonego powinien być używany, następnie usuń `_SECURE_ATL`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]  
  
##  <a name="gethour"></a>  CTime::GetHour  
 Zwraca godzinę reprezentowany przez `CTime` obiektu.  
  
```  
int GetHour() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca godzinę na podstawie czasu lokalnego, w zakresie od 0 do 23.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]  
  
##  <a name="getlocaltm"></a>  CTime::GetLocalTm  
 Pobiera **tm struktury** zawierający rozkładu czasu zawarte w tym `CTime` obiektu.  
  
```  
struct tm* GetLocalTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `ptm`  
 Wskazuje buforu, który będzie odbierać dane czasu. Jeśli ten wskaźnik jest **NULL**, jest zgłaszany wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wypełniane **tm struktury** zgodnie z definicją w pliku dołączanego czasu. H. Zobacz [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) w układzie struktury.  
  
### <a name="remarks"></a>Uwagi  
 `GetLocalTm` Zwraca czas lokalny.  
  
 `ptm` nie może być `NULL`. Jeśli chcesz przywrócić poprzednie działanie, w którym `ptm` może być `NULL` do wskazuje, czy bufor wewnętrzny, statycznie przydzielonego powinien być używany, następnie usuń `_SECURE_ATL`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]  
  
##  <a name="getminute"></a>  CTime::GetMinute  
 Zwraca minutę reprezentowany przez `CTime` obiektu.  
  
```  
int GetMinute() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę minut, na podstawie czasu lokalnego, w zakresie od 0 do 59.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHour](#gethour).  
  
##  <a name="getmonth"></a>  CTime::GetMonth  
 Zwraca miesiąc reprezentowany przez `CTime` obiektu.  
  
```  
int GetMonth() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca miesiąc, na podstawie czasu lokalnego, w zakresie od 1 do 12 (1 stycznia =).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetDay](#getday).  
  
##  <a name="getsecond"></a>  CTime::GetSecond  
 Zwraca drugie reprezentowany przez `CTime` obiektu.  
  
```  
int GetSecond() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca druga Strona, na podstawie czasu lokalnego, w zakresie od 0 do 59.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHour](#gethour).  
  
##  <a name="gettime"></a>  CTime::GetTime  
 Zwraca **__time64_t —** wartość dla danego `CTime` obiektu.  
  
```  
__time64_t GetTime() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **GetTime** zwróci liczbę sekund między bieżącą `CTime` obiekt i 1 stycznia 1970.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]  
  
##  <a name="getyear"></a>  CTime::GetYear  
 Zwraca rok reprezentowany przez `CTime` obiektu.  
  
```  
int GetYear();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rok, na podstawie czasu lokalnego, w zakresie od stycznia 1,1970 do 18 stycznia 2038 (włącznie).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga `GetLocalTm`, który używa wewnętrznego statycznie przydzielić buforu. Dane w buforze ten zostanie zastąpiony ze względu na wywołania innych `CTime` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetDay](#getday).  
  
##  <a name="operator_eq"></a>  CTime::operator =  
 Operator przypisania.  
  
```  
CTime& operator=(__time64_t time) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `time`  
 Wartość nowego daty/godziny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowany interfejs `CTime` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator przypisania przeciążonej kopiuje czasu źródłowego do tego `CTime` obiektu. Magazyn wewnętrzny czasu w `CTime` obiektu jest niezależna od strefy czasowej. Podczas przypisywania konwersji strefy czasowej nie jest konieczne.  
  
##  <a name="operator_add_-"></a>  CTime::operator +, -  
 Tych operatorów dodawania i odejmowania `CTimeSpan` i `CTime` obiektów.  
  
```  
CTime operator+(CTimeSpan timeSpan) const throw(); 
CTime operator-(CTimeSpan timeSpan) const throw(); 
CTimeSpan operator-(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *Zakres czasu*  
 `CTimeSpan` Obiekt do dodania lub odjęcia.  
  
 `time`  
 `CTime` Obiektu do odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CTime` lub `CTimeSpan` obiekt reprezentujący wynik operacji.  
  
### <a name="remarks"></a>Uwagi  
 `CTime` Bezwzględny czas reprezentować `CTimeSpan` reprezentować względne czasu. Pierwsze dwa operatory pozwala na dodawanie i usuwanie `CTimeSpan` obiekty do i z `CTime` obiektów. Trzeci operator służy do odejmowania jedną `CTime` obiektu z innego umożliwiające uzyskanie `CTimeSpan` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  CTime::operator +=-=  
 Tych operatorów dodawania i odejmowania `CTimeSpan` obiekt do i z tego `CTime` obiektu.  
  
```  
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CTimeSpan` Obiekt do dodania lub odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowany interfejs `CTime` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Operatory te umożliwiają dodawanie i odejmowanie `CTimeSpan` obiekt do i z tego `CTime` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]  
  
##  <a name="serialize64"></a>  CTime::Serialize64  
  
> [!NOTE]
>  Ta metoda jest dostępna tylko w projektach MFC.  
  
 Serializuje dane skojarzone z zmiennej członka do lub z archiwum.  
  
```  
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 `CArchive` Obiekt, który chcesz zaktualizować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowany interfejs `CArchive` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [asctime_s —, _wasctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime_s —, _ftime32_s —, _ftime64_s —](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


