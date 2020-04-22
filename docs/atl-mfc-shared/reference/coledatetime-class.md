---
title: COleDateTime, klasa
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 8ba09430427b6ece8ae5956912cbcc40fb33fcf2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747160"
---
# <a name="coledatetime-class"></a>COleDateTime, klasa

Hermetyzuje `DATE` typ danych, który jest używany w automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleDateTime
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Konstruuje `COleDateTime` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::Format](#format)|Generuje sformatowaną reprezentację `COleDateTime` ciągu obiektu.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Wywołanie tej metody, aby `COleDateTime` uzyskać `DBTIMESTAMP` czas w obiekcie jako struktury danych.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Wywołanie tej metody, aby `COleDateTime` uzyskać czas w obiekcie jako [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury danych.|
|[COleDateTime::GetAsUDATE](#getasudate)|Wywołanie tej metody, aby `COleDateTime` uzyskać `UDATE` czas w strukturze danych jako.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Tworzy `COleDateTime` obiekt reprezentujący bieżący czas (funkcja statycznego elementu członkowskiego).|
|[COleDateTime::GetDay](#getday)|Zwraca dzień, `COleDateTime` który reprezentuje ten obiekt (1 - 31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia, `COleDateTime` który reprezentuje ten obiekt (niedziela = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Zwraca dzień roku, `COleDateTime` który reprezentuje ten obiekt (1 stycznia = 1).|
|[COleDateTime::GetHour](#gethour)|Zwraca godzinę, `COleDateTime` która reprezentuje ten obiekt (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Zwraca minutę, `COleDateTime` która reprezentuje ten obiekt (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Zwraca miesiąc, `COleDateTime` który reprezentuje ten obiekt (1 - 12).|
|[COleDateTime::GetSecond](#getsecond)|Zwraca drugi `COleDateTime` ten obiekt reprezentuje (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Pobiera stan (ważność) `COleDateTime` tego obiektu.|
|[COleDateTime::GetYear](#getyear)|Zwraca rok, `COleDateTime` który reprezentuje ten obiekt.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Odczytuje wartość daty/godziny z ciągu `COleDateTime`i ustawia wartość .|
|[COleDateTime::SetDate](#setdate)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość tylko do daty.|
|[COleDateTime::SetDateTime](#setdatetime)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość daty/godziny.|
|[COleDateTime::SetStatus](#setstatus)|Ustawia stan (ważność) `COleDateTime` tego obiektu.|
|[COleDateTime::SetTime](#settime)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość tylko czas.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::operator ==, COleDateTime::operator < itp.](#coledatetime_relational_operators)|Porównaj `COleDateTime` dwie wartości.|
|[COleDateTime::operator +, COleDateTime::operator -](#operator_add_-)|Dodawanie i odejmowanie `COleDateTime` wartości.|
|[COleDateTime::operator +=, COleDateTime::operator -=](#operator_add_eq_-_eq)|Dodaj i odejmij `COleDateTime` `COleDateTime` wartość od tego obiektu.|
|[COleDateTime::operator =](#operator_eq)|Kopiuje `COleDateTime` wartość.|
|[COleDateTime::operator DATE, COleDateTime::operator Data*](#operator_date)|Konwertuje `COleDateTime` wartość `DATE` na `DATE*`a lub .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Zawiera podstawę `DATE` tego `COleDateTime` obiektu.|
|[COleDateTime::m_status](#m_status)|Zawiera stan tego `COleDateTime` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTime`nie ma klasy podstawowej.

Jest to jeden z możliwych typów dla typu danych [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) automatyzacji OLE. Wartość `COleDateTime` reprezentuje bezwzględną datę i wartość godziny.

Typ `DATE` jest implementowany jako wartość zmiennoprzecinkowa. Dni są mierzone od 30 grudnia 1899 roku, o północy. W poniższej tabeli przedstawiono niektóre daty i skojarzone z nimi wartości:

|Date|Wartość|
|----------|-----------|
|29 grudnia 1899, północ|-1.0|
|29 grudnia 1899, godz.|-1.25|
|30 grudnia 1899, północ|0.0|
|31 grudnia 1899, północ|1.0|
|1 stycznia 1900, godz.|2.25|

> [!CAUTION]
> W powyższej tabeli, chociaż wartości dzienne stają się ujemne przed północą 30 grudnia 1899 r., wartości czasu dnia nie. Na przykład 6:00 AM jest zawsze reprezentowana przez wartość ułamkową 0,25, niezależnie od tego, czy liczba całkowita reprezentująca dzień jest dodatnia (po 30 grudnia 1899) lub ujemna (przed 30 grudnia 1899). Oznacza to, że proste porównanie zmiennoprzecinkowe błędnie sortować `COleDateTime` reprezentujących 6:00 AM na 12/29/1899 jako **później** niż jeden reprezentujących 7:00 AM w tym samym dniu.

Zajęcia `COleDateTime` zajęć pochodzą z 1 stycznia 100 do 31 grudnia 9999. Klasa `COleDateTime` używa kalendarza gregoriańskiego; nie obsługuje dat juliańskimi. `COleDateTime`ignoruje czas letni. (Zobacz [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Za pomocą `%y` tego formatu można pobrać dwucyfrowy rok tylko dla dat rozpoczynających się od 1900 roku. Jeśli używasz `%y` formatu w dniu przed 1900, kod generuje błąd ASSERT.

Ten typ jest również używany do reprezentowania wartości tylko do daty lub tylko do czasu. Zgodnie z konwencją data 0 (30 grudnia 1899) jest używana dla wartości tylko do czasu, a godzina 00:00 (północ) jest używana dla wartości tylko do daty.

Jeśli obiekt `COleDateTime` zostanie utworzony przy użyciu daty mniejszej niż 100, `GetYear`data `GetMonth` `GetDay`zostanie `GetHour` `GetMinute`zaakceptowana, ale kolejne wywołania do , , , , , i `GetSecond` zakończyć się niepowodzeniem i zwrócić -1. Wcześniej można było użyć dat dwucyfrowych, ale daty muszą być 100 lub większe w MFC 4.2 i nowszych.

Aby uniknąć problemów, należy określić datę czterocyfrową. Przykład:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Podstawowe operacje arytmetyczne `COleDateTime` dla wartości używają klasy towarzyszącej [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`wartości definiują przedział czasu. Relacja między tymi klasami jest podobna do tej między [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej `COleDateTime` `COleDateTimeSpan` informacji na temat i klas, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>Operatory relacyjne COleDateTime

Operatory porównawcze.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parametry

*Data*<br/>
Obiekt `COleDateTime` do porównania.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Atlassert wystąpi, jeśli którykolwiek z dwóch argumentów jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Przykład

Operatory **>=** ** \< **, **>**, **<** i , `COleDateTime` będzie potwierdzać, jeśli obiekt jest ustawiony na null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDateTime::COleDateTime

Konstruuje `COleDateTime` obiekt.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Parametry

*dataSrc*<br/>
Istniejący `COleDateTime` obiekt do skopiowania `COleDateTime` do nowego obiektu.

*varSrc ( varSrc )*<br/>
Istniejąca `VARIANT` struktura danych `COleVariant` (ewentualnie obiekt) ma zostać przekonwertowana na wartość daty/godziny `COleDateTime` (VT_DATE) i skopiowana do nowego obiektu.

*dtSrc ( dtSrc )*<br/>
Wartość daty/godziny (`DATE`) do skopiowania do nowego `COleDateTime` obiektu.

*czasSrc*<br/>
A `time_t` `__time64_t` lub wartość, która ma zostać przekonwertowana `COleDateTime` na wartość daty/godziny i skopiowana do nowego obiektu.

*systimeSrc*<br/>
Struktura, `SYSTEMTIME` która ma zostać przekonwertowana na wartość `COleDateTime` daty/godziny i skopiowana do nowego obiektu.

*filetimeSrc*<br/>
Struktura, `FILETIME` która ma zostać przekonwertowana na wartość `COleDateTime` daty/godziny i skopiowana do nowego obiektu. A `FILETIME` używa uniwersalnego czasu skoordynowanego (UTC), więc jeśli zdasz czas lokalny w strukturze, wyniki będą niepoprawne. Aby uzyskać więcej informacji, zobacz [Czasy plików](/windows/win32/SysInfo/file-times) w programie Windows SDK.

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Wskaż wartości daty i godziny, `COleDateTime` które mają zostać skopiowane do nowego obiektu.

*wDosDate*, *wDosTime*<br/>
Wartości daty i godziny ms-dos, które mają zostać przekonwertowane na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.

*Sygnatury czasowej*<br/>
Odwołanie do [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) struktury zawierającej bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory utworzyć nowe `COleDateTime` obiekty zainicjowane do określonej wartości. W poniższej tabeli przedstawiono prawidłowe zakresy dla każdego składnika daty i godziny:

|Składnik daty/godziny|Prawidłowy zakres|
|--------------------------|-----------------|
|rok|100 - 9999|
|miesiąc|0 - 12|
|dzień|0 - 31|
|godzina|0 - 23|
|minuta|0 - 59|
|sekunda|0 - 59|

Należy zauważyć, że rzeczywista górna granica składnika dnia różni się w zależności od składników miesiąca i roku. Aby uzyskać szczegółowe `SetDate` `SetDateTime` informacje, zobacz lub funkcji członkowskich.

Poniżej znajduje się krótki opis każdego konstruktora:

- `COleDateTime(`**)** Konstruuje `COleDateTime` obiekt zainicjowany do 0 (północ, 30 grudnia 1899 r.).

- `COleDateTime(``dateSrc` **)** Tworzy `COleDateTime` obiekt z `COleDateTime` istniejącego obiektu.

- `COleDateTime(`*varSrc* **)** Konstruuje `COleDateTime` obiekt. Próbuje przekonwertować strukturę `VARIANT` lub [COleVariant](../../mfc/reference/colevariant-class.md) `VT_DATE`obiektu do wartości daty /godziny ( ) . Jeśli ta konwersja zakończy się pomyślnie, przekonwertowana wartość jest kopiowana do nowego `COleDateTime` obiektu. Jeśli tak nie jest, `COleDateTime` wartość obiektu jest ustawiona na 0 (północ, 30 grudnia 1899) i jego stan jest nieprawidłowy.

- `COleDateTime(``dtSrc` **)** Tworzy `COleDateTime` obiekt z `DATE` wartości.

- `COleDateTime(``timeSrc` **)** Tworzy `COleDateTime` obiekt z `time_t` wartości.

- `COleDateTime(`*systimeSrc* **)** Konstruuje `COleDateTime` obiekt z `SYSTEMTIME` wartości.

- `COleDateTime(``filetimeSrc` **)** Tworzy `COleDateTime` obiekt z `FILETIME` wartości. . A `FILETIME` używa uniwersalnego czasu skoordynowanego (UTC), więc jeśli zdasz czas lokalny w strukturze, wyniki będą niepoprawne. Aby uzyskać więcej informacji, zobacz [Czasy plików](/windows/win32/SysInfo/file-times) w programie Windows SDK.

- `COleDateTime(``nYear`, `nMonth` `nDay`, `nHour` `nMin`, `nSec` , , `COleDateTime` **)** Konstruuje obiekt z określonych wartości liczbowych.

- `COleDateTime(``wDosDate`), `wDosTime` **)** Konstruuje `COleDateTime` obiekt z określonych wartości daty i godziny ms-dos.

Aby uzyskać więcej `time_t` informacji na temat typu danych, zobacz funkcję [czasu](../../c-runtime-library/reference/time-time32-time64.md) w *odwołaniu do biblioteki w czasie wykonywania*.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktur w Windows SDK.

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Konstruktor `DBTIMESTAMP` używający parametru jest dostępny tylko wtedy, gdy oledb.h jest uwzględniony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::Format

Tworzy sformatowaną reprezentację wartości daty/godziny.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Wskazuje jedną z następujących flag ustawień regionalnych:

- LOCALE_NOUSEROVERRIDE Użyj domyślnych ustawień ustawień regionalnych systemu zamiast niestandardowych ustawień użytkownika.

- VAR_TIMEVALUEONLY Ignoruj część daty podczas analizowania.

- VAR_DATEVALUEONLY Ignoruj część czasu podczas analizowania.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych, który ma być używany do konwersji. Aby uzyskać więcej informacji na temat identyfikatorów języka, zobacz [Identyfikatory języków](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Ciąg formatowania podobny `printf` do ciągu formatowania. Każdy kod formatowania, poprzedzony `%`znakiem procentu ( `COleDateTime` ), jest zastępowany odpowiednim składnikiem. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Aby uzyskać więcej informacji, zobacz funkcję czasu wykonywania [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Wartość i znaczenie kodów formatowania `Format` są następujące:

- `%H`Godziny w bieżącym dniu

- `%M`Minuty w bieżącej godzinie

- `%S`Sekundy w bieżącej minucie

- `%%`Znak procentowy

*nFormatID*<br/>
Identyfikator zasobu dla ciągu kontroli formatu.

### <a name="return-value"></a>Wartość zwracana

A `CString` zawierający sformatowaną wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Jeśli stan tego `COleDateTime` obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określony przez ATL_IDS_DATETIME_INVALID zasobu ciągu.

Krótki opis trzech formularzy dla tej funkcji jest następujący:

`Format`( *dwFlags*, *lcid*)<br/>
Ten formularz formatuje wartość przy użyciu specyfikacji języka (identyfikatory ustawień regionalnych) dla daty i godziny. Przy użyciu parametrów domyślnych ten formularz wydrukuje datę i godzinę, chyba że część czasu wynosi 0 (północ), w którym to przypadku wydrukuje tylko datę, lub część daty to 0 (30 grudnia 1899 r.), w którym to przypadku będzie drukowana tylko czas. Jeśli wartość daty/godziny wynosi 0 (30 grudnia 1899 r., północ), ten formularz z domyślnymi parametrami zostanie wydrukowany o północy.

`Format`( *lpszFormat*)<br/>
Ten formularz formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), jak w `printf`. Ciąg formatowania jest przekazywany jako parametr do funkcji. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w odwołaniu do biblioteki w czasie wykonywania.

`Format`( *nFormatID*)<br/>
Ten formularz formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), jak w `printf`. Ciąg formatowania jest zasobem. Identyfikator tego zasobu ciągu jest przekazywany jako parametr. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w *odwołaniu do biblioteki w czasie wykonywania*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Wywołanie tej metody, aby `COleDateTime` uzyskać `DBTIMESTAMP` czas w obiekcie jako struktury danych.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parametry

*Sygnatury czasowej*<br/>
Odwołanie do struktury [DBTimeStamp.](/dotnet/api/system.data.oledb.oledbtype)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przechowuje wynikczas w strukturze *sygnatury czasowej,* do której istnieje odwołanie. Struktura `DBTIMESTAMP` danych zainicjowana przez tę `fraction` funkcję będzie miała swój element członkowski ustawiony na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDateTime::GetAsSystemTime

Wywołanie tej metody, aby `COleDateTime` uzyskać `SYSTEMTIME` czas w obiekcie jako struktury danych.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*sysCzas*<br/>
Odwołanie do struktury [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) aby otrzymać przekonwertowane wartości daty/godziny z `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie; FAŁSZ, jeśli konwersja `COleDateTime` nie powiedzie się lub jeśli obiekt ma wartość NULL lub nieprawidłowy.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime`przechowuje wynikowy czas w obiekcie *sysTime,* do którego istnieje odwołanie. Struktura `SYSTEMTIME` danych zainicjowana przez tę `wMilliseconds` funkcję będzie miała swój element członkowski ustawiony na zero.

Aby uzyskać więcej informacji na `COleDateTime` temat informacji o stanie przechowywanych w obiekcie, zobacz [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDateTime::GetAsUDATE

Wywołanie tej metody, aby `COleDateTime` uzyskać `UDATE` czas w obiekcie jako struktury danych.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parametry

*uDlat*<br/>
Odwołanie do `UDATE` struktury, aby otrzymać przekonwertowane `COleDateTime` wartości daty/godziny z obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie; FAŁSZ, jeśli konwersja `COleDateTime` nie powiedzie się lub jeśli obiekt ma wartość NULL lub nieprawidłowy.

### <a name="remarks"></a>Uwagi

Struktura `UDATE` reprezentuje datę "rozpakowane".

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Wywołanie tej statycznej funkcji elementu członkowskiego, aby zwrócić bieżącą wartość daty/godziny.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime::GetDay

Pobiera dzień miesiąca reprezentowane przez tę wartość daty/godziny.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień miesiąca reprezentowany przez wartość tego `COleDateTime` obiektu `COleDateTime::error` lub jeśli nie można uzyskać dnia.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 1 do 31.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDateTime::GetDayOfWeek

Pobiera dzień miesiąca reprezentowane przez tę wartość daty/godziny.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień tygodnia reprezentowany przez wartość tego `COleDateTime` obiektu `COleDateTime::error` lub jeśli nie można było uzyskać dnia tygodnia.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 1 do 7, gdzie 1 =niedziela, 2=poniedziałek i tak dalej.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Pobiera dzień roku reprezentowane przez tę wartość daty/godziny.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień roku reprezentowany przez wartość tego `COleDateTime` przedmiotu lub `COleDateTime::error` jeśli nie można było uzyskać dnia roku.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 1 do 366, gdzie 1 stycznia = 1.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDateTime::GetHour

Pobiera godzinę reprezentowaną przez tę wartość daty/godziny.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Godzina reprezentowana przez wartość `COleDateTime` tego `COleDateTime::error` obiektu lub jeśli nie można uzyskać godziny.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 0 do 23.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDateTime::GetMinute

Pobiera minutę reprezentowane przez tę wartość daty/godziny.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Minuta reprezentowana przez wartość `COleDateTime` tego `COleDateTime::error` obiektu lub jeśli nie można uzyskać minuty.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 0 do 59.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [gethour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime::GetMonth

Pobiera miesiąc reprezentowany przez tę wartość daty/godziny.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Miesiąc reprezentowany przez wartość `COleDateTime` tego `COleDateTime::error` obiektu lub jeśli nie można uzyskać miesiąca.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 1 do 12.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [getday](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime::GetSecond

Pobiera drugi reprezentowane przez tę wartość daty/godziny.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Drugi reprezentowany przez wartość `COleDateTime` tego `COleDateTime::error` obiektu lub jeśli nie można uzyskać drugiego.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 0 do 59.

> [!NOTE]
> Klasa `COleDateTime` nie obsługuje sekund przestępu.

Aby uzyskać więcej informacji `COleDateTime`na temat implementacji dla , zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [gethour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime::GetStatus

Pobiera stan (ważność) danego `COleDateTime` obiektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan tej `COleDateTime` wartości. Jeśli wywołasz `GetStatus` `COleDateTime` obiekt zbudowany z ustawieniem domyślnym, zwróci prawidłowe. Jeśli wywołasz `GetStatus` `COleDateTime` obiekt zainicjowany z konstruktorem `GetStatus` ustawionym na null, zwróci wartość null.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest `DateTimeStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleDateTime` klasie.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Aby uzyskać krótki opis tych wartości stanu, zobacz następującą listę:

- `COleDateTime::error`Wskazuje, że wystąpił błąd podczas próby uzyskania części wartości daty/godziny.

- `COleDateTime::valid`Wskazuje, że `COleDateTime` ten obiekt jest prawidłowy.

- `COleDateTime::invalid`Wskazuje, że `COleDateTime` ten obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTime::null`Wskazuje, że `COleDateTime` ten obiekt ma wartość null, oznacza to, że nie podano żadnej wartości dla tego obiektu. (Jest to "null" w sensie bazy danych "nie ma wartości", w przeciwieństwie do C++ NULL.)

Stan obiektu `COleDateTime` jest nieprawidłowy w następujących przypadkach:

- Jeśli jego wartość jest `VARIANT` `COleVariant` ustawiona na podstawie wartości lub wartości, której nie można przekonwertować na wartość daty/godziny.

- Jeśli jego wartość jest `time_t` `SYSTEMTIME`ustawiona `FILETIME` na podstawie wartości , lub wartości, której nie można przekonwertować na prawidłową wartość daty/godziny.

- Jeśli jego wartość `SetDateTime` jest ustawiona przez nieprawidłowe wartości parametrów.

- Jeśli ten obiekt doświadczył przepełnienia lub niedopełnienia podczas operacji przypisania arytmetycznego, `+=` a mianowicie lub `-=`.

- Jeśli do tego obiektu została przypisana nieprawidłowa wartość.

- Jeśli stan tego obiektu został jawnie `SetStatus`ustawiony na nieprawidłowy przy użyciu programu .

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan na nieprawidłowy, zobacz następujące funkcje członkowskie:

- [Coledatetime](#coledatetime)

- [SetDateTime (Ustaw czas 2018)](#setdatetime)

- [operator +, -](#operator_add_-)

- [operator +=, -=](#operator_add_eq_-_eq)

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDateTime::GetYear

Pobiera rok reprezentowany przez tę wartość daty/godziny.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Rok reprezentowany przez wartość `COleDateTime` tego `COleDateTime::error` obiektu lub jeśli nie można było uzyskać roku.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane wahają się od 100 do 9999, który obejmuje wieku.

Aby uzyskać informacje na temat innych `COleDateTime` funkcji członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [getday](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDateTime::m_dt

Podstawowa `DATE` struktura `COleDateTime` tego obiektu.

```
DATE m_dt;
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w `DATE` obiekcie, do który uzyskuje dostęp wskaźnik zwracany przez tę funkcję, spowoduje zmianę wartości tego `COleDateTime` obiektu. Nie zmienia stanu tego `COleDateTime` obiektu.

Aby uzyskać więcej informacji `DATE` na temat implementacji obiektu, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDateTime::m_status

Zawiera stan tego `COleDateTime` obiektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Uwagi

Typ tego elementu członkowskiego danych jest typem `DateTimeStatus`wyliczonym, który jest zdefiniowany w `COleDateTime` klasie. Aby uzyskać więcej informacji, zobacz [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
> Ten element członkowski danych jest przeznaczony do zaawansowanych sytuacji programowania. Należy użyć wbudowanych funkcji członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dalsze ostrzeżenia dotyczące jawnego ustawiania tego elementu członkowskiego danych.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::operator =

Kopiuje `COleDateTime` wartość.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Uwagi

Te przeciążonych operatorów przypisania kopiują `COleDateTime` wartość daty/godziny źródła do tego obiektu. Krótki opis każdego z tych przeciążonych operatorów przypisania jest następujący:

- **operator =(** `dateSrc` **)** Wartość i stan operandu są kopiowane do tego `COleDateTime` obiektu.

- **operator =(** *varSrc* **)** Jeśli konwersja [variant](/windows/win32/api/oaidl/ns-oaidl-variant) wartość (lub [COleVariant](../../mfc/reference/colevariant-class.md) obiektu) do daty/godziny (VT_DATE) jest pomyślny, przekonwertowana wartość jest kopiowana do tego `COleDateTime` obiektu i jego stan jest ustawiony na prawidłowe. Jeśli konwersja nie powiedzie się, wartość tego obiektu jest ustawiona na zero (30 grudnia 1899, północ), a jego stan jest nieprawidłowy.

- **operator =(** `dtSrc` **)** Wartość `DATE` jest kopiowana `COleDateTime` do tego obiektu, a jego stan jest ustawiony na prawidłowy.

- **operator =(** `timeSrc` **)** Wartość `time_t` `__time64_t` lub wartość jest konwertowana i kopiowana do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; jeśli nie powiedzie się, jest ustawiona na nieprawidłową.

- **operator =(** *systimeSrc* **)** Wartość [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) jest konwertowana `COleDateTime` i kopiowana do tego obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; jeśli nie powiedzie się, jest ustawiona na nieprawidłową.

- **operator =(** `uDate` **)** Wartość `UDATE` jest konwertowana i `COleDateTime` kopiowana do tego obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; jeśli nie powiedzie się, jest ustawiona na nieprawidłową. Struktura `UDATE` reprezentuje datę "rozpakowane". Aby uzyskać więcej informacji, zobacz funkcję [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **operator =(** `filetimeSrc` **)** Wartość [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) jest konwertowana `COleDateTime` i kopiowana do tego obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; w przeciwnym razie jest ustawiona na nieprawidłową. `FILETIME`używa uniwersalnego czasu skoordynowanego (UTC), więc jeśli miniesz czas UTC w strukturze, wyniki zostaną przekonwertowane z czasu UTC na czas lokalny i będą przechowywane jako czas wariantu. To zachowanie jest takie samo jak w języku Visual C++ 6.0 i Visual C++.NET 2003 SP2. Aby uzyskać więcej informacji, zobacz [Czasy plików](/windows/win32/SysInfo/file-times) w programie Windows SDK.

Aby uzyskać więcej informacji, zobacz wpis [WARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) w windows SDK.

Aby uzyskać więcej `time_t` informacji na temat typu danych, zobacz funkcję [czasu](../../c-runtime-library/reference/time-time32-time64.md) w *odwołaniu do biblioteki w czasie wykonywania*.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktur w Windows SDK.

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::operator +, -

Dodawanie i odejmowanie `ColeDateTime` wartości.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Uwagi

`COleDateTime`obiekty reprezentują czasy bezwzględne. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) obiekty reprezentują względne razy. Pierwsze dwa operatory umożliwiają dodawanie i `COleDateTimeSpan` odejmowanie wartości od `COleDateTime` wartości. Trzeci operator umożliwia odjąć jedną `COleDateTime` wartość od drugiej, aby uzyskać `COleDateTimeSpan` wartość.

Jeśli którykolwiek z argumentów ma wartość null, `COleDateTime` stan wartości wynikowej jest zerowy.

Jeśli wynikowa `COleDateTime` wartość wykracza poza granice dopuszczalnych wartości, `COleDateTime` stan tej wartości jest nieprawidłowy.

Jeśli którykolwiek z argumentów jest nieprawidłowy, a drugi nie ma `COleDateTime` wartości null, stan wynikowej wartości jest nieprawidłowy.

I **+** **-** operatorów będzie `COleDateTime` potwierdzać, jeśli obiekt jest ustawiony na null. Zobacz [COleDateTime relacyjnych operatorów](#coledatetime_relational_operators) na przykład.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTime::operator +=, -=

Dodaj i odejmij `ColeDateTime` `COleDateTime` wartość od tego obiektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Operatory te umożliwiają dodawanie i `COleDateTimeSpan` odejmowanie `COleDateTime`wartości do i od tego . Jeśli którykolwiek z argumentów ma wartość null, `COleDateTime` stan wartości wynikowej jest zerowy.

Jeśli wynikowa `COleDateTime` wartość wykracza poza granice dopuszczalnych wartości, `COleDateTime` stan tej wartości jest ustawiony na nieprawidłowy.

Jeśli którykolwiek z argumentów jest nieprawidłowy, a inne nie `COleDateTime` ma wartości null, stan wynikowej wartości jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych, nieprawidłowych i zerowych wartości stanu, zobacz [zmienną m_status](#m_status) elementu członkowskiego.

I **+=** **-=** operatorów będzie `COleDateTime` potwierdzać, jeśli obiekt jest ustawiony na null. Zobacz [COleDateTime relacyjnych operatorów](#coledatetime_relational_operators) na przykład.

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDateTime::operator DATE

Konwertuje `ColeDateTime` wartość `DATE`na plik .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator `DATE` zwraca obiekt, którego wartość `COleDateTime` jest kopiowana z tego obiektu. Aby uzyskać więcej informacji `DATE` na temat implementacji obiektu, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

Operator `DATE` będzie potwierdzać, `COleDateTime` jeśli obiekt jest ustawiony na null. Zobacz [COleDateTime relacyjnych operatorów](#coledatetime_relational_operators) na przykład.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::ParseDateTime

Analizuje ciąg, aby odczytać wartość daty/godziny.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*lpszDate*<br/>
Wskaźnik do ciągu zakończonego wartością null, który ma być analizowany. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

*Dwflags*<br/>
Wskazuje flagi dla ustawień regionalnych i analizowania. Co najmniej jedna z następujących flag:

- LOCALE_NOUSEROVERRIDE Use the system default locale settings, rather than custom user settings.

- VAR_TIMEVALUEONLY Ignoruj część daty podczas analizowania.

- VAR_DATEVALUEONLY Ignoruj część czasu podczas analizowania.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych, który ma być używany do konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg został pomyślnie przekonwertowany na wartość daty/godziny, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli ciąg został pomyślnie przekonwertowany na wartość `COleDateTime` daty/godziny, wartość tego obiektu jest ustawiona na tę wartość, a jego stan na prawidłowy.

> [!NOTE]
> Wartości roku muszą wynosić od 100 do 9999, włącznie.

Parametr *lpszDate* może przyjmować różne formaty. Na przykład następujące ciągi zawierają dopuszczalne formaty daty/godziny:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

Identyfikator ustawień regionalnych będzie również mieć wpływ na to, czy format ciągu jest dopuszczalny dla konwersji na wartość daty/godziny.

W przypadku VAR_DATEVALUEONLY wartość czasu jest ustawiona na czas 0 lub północy. W przypadku VAR_TIMEVALUEONLY wartość daty jest ustawiona na datę 0, czyli 30 grudnia 1899.

Jeśli nie można przekonwertować ciągu na wartość daty/godziny lub jeśli wystąpiło `COleDateTime` przepełnienie numeryczne, stan tego obiektu jest nieprawidłowy.

Aby uzyskać więcej informacji na `COleDateTime` temat granic i implementacji wartości, zobacz artykuł Data i [godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDateTime::SetDate

Ustawia datę tego `COleDateTime` obiektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nYear*, *nMonth*, *nDzień*<br/>
Wskaż składniki daty, `COleDateTime` które mają zostać skopiowane do tego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość `COleDateTime` tego obiektu została ustawiona pomyślnie; w przeciwnym razie, 1. Ta wartość zwracana `DateTimeStatus` jest oparta na typie wyliczonym. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Data jest ustawiona na określone wartości. Czas jest ustawiony na czas 0, północ.

Zobacz następującą tabelę dla granic dla wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nRok*|100 - 9999|
|*nMonth*|1 - 12|
|*nDzień*|0 - 31|

Jeśli dzień miesiąca przepełnia się, jest on konwertowany na prawidłowy dzień następnego miesiąca, a miesiąc i/lub rok jest odpowiednio zwiększany. Wartość dnia zero wskazuje ostatni dzień poprzedniego miesiąca. Zachowanie jest takie `SystemTimeToVariantTime`samo jak .

Jeśli wartość daty określona przez parametry jest nieprawidłowa, `COleDateTime::invalid`stan tego obiektu jest ustawiony na . Należy użyć [GetStatus,](#getstatus) aby sprawdzić `DATE` ważność wartości i nie należy zakładać, że wartość [m_dt](#m_dt) pozostanie niezmodyfikowana.

Oto kilka przykładów wartości dat:

|*nRok*|*nMonth*|*nDzień*|Wartość|
|-------------|--------------|------------|-----------|
|2000|2|29|29 lutego 2000 r.|
|1776|7|4|4 lipca 1776 r.|
|1925|4|35|35 kwietnia 1925 r. (data nieważna)|
|10 000|1|1|1 stycznia 10000 r. (nieprawidłowa data)|

Aby ustawić zarówno datę, jak i godzinę, zobacz [COleDateTime::SetDateTime](#setdatetime).

Aby uzyskać informacje na temat funkcji `COleDateTime` członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDateTime::SetDateTime

Ustawia datę i godzinę `COleDateTime` tego obiektu.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Wskaż składniki daty i godziny, które mają zostać skopiowane do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość `COleDateTime` tego obiektu została ustawiona pomyślnie; w przeciwnym razie, 1. Ta wartość zwracana `DateTimeStatus` jest oparta na typie wyliczonym. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Zobacz następującą tabelę dla granic dla wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nRok*|100 - 9999|
|*nMonth*|1 - 12|
|*nDzień*|0 - 31|
|*nGodzina*|0 - 23|
|*nMin (min.*|0 - 59|
|*Nsec*|0 - 59|

Jeśli dzień miesiąca przepełnia się, jest on konwertowany na prawidłowy dzień następnego miesiąca, a miesiąc i/lub rok jest odpowiednio zwiększany. Wartość dnia zero wskazuje ostatni dzień poprzedniego miesiąca. Zachowanie jest takie samo jak [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Jeśli wartość daty lub godziny określona przez parametry jest nieprawidłowa, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu nie zostanie zmieniona.

Oto kilka przykładów wartości czasu:

|*nGodzina*|*nMin (min.*|*Nsec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Oto kilka przykładów wartości dat:

|*nRok*|*nMonth*|*nDzień*|Wartość|
|-------------|--------------|------------|-----------|
|1995|4|15|15 kwietnia 1995 r.|
|1789|7|14|17 lipca 1789 r.|
|1925|2|30|Nieprawidłowy|
|10 000|1|1|Nieprawidłowy|

Aby ustawić tylko datę, zobacz [COleDateTime::SetDate](#setdate). Aby ustawić tylko czas, zobacz [COleDateTime::SetTime](#settime).

Aby uzyskać informacje na temat funkcji `COleDateTime` członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [getstatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDateTime::SetStatus

Ustawia stan tego `COleDateTime` obiektu.

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stan*<br/>
Nowa wartość stanu `COleDateTime` dla tego obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *stanu* jest `DateTimeStatus` definiowana przez typ wyliczony, który jest zdefiniowany w `COleDateTime` klasie. Zobacz [COleDateTime::GetStatus](#getstatus) szczegóły.

> [!CAUTION]
> Ta funkcja jest dla zaawansowanych sytuacji programowania. Ta funkcja nie zmienia danych w tym obiekcie. Najczęściej będzie on używany do ustawiania stanu **na null** lub **nieprawidłowy.** Operator przypisania[(operator =](#operator_eq)) i [SetDateTime](#setdatetime) ustawia stan obiektu na podstawie wartości źródłowych.

### <a name="example"></a>Przykład

Zobacz przykład [getstatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::SetTime

Ustawia czas tego `COleDateTime` obiektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nGodzina*, *nMin*, *nSec*<br/>
Wskazać składniki czasu, które mają `COleDateTime` zostać skopiowane do tego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość `COleDateTime` tego obiektu została ustawiona pomyślnie; w przeciwnym razie, 1. Ta wartość zwracana `DateTimeStatus` jest oparta na typie wyliczonym. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Czas jest ustawiony na określone wartości. Data jest ustawiona na datę 0, czyli 30 grudnia 1899.

Zobacz następującą tabelę dla granic dla wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nGodzina*|0 - 23|
|*nMin (min.*|0 - 59|
|*Nsec*|0 - 59|

Jeśli wartość czasu określona przez parametry jest nieprawidłowa, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu nie zostanie zmieniona.

Oto kilka przykładów wartości czasu:

|*nGodzina*|*nMin (min.*|*Nsec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Aby ustawić zarówno datę, jak i godzinę, zobacz [COleDateTime::SetDateTime](#setdatetime).

Aby uzyskać informacje na temat funkcji `COleDateTime` członkowskich, które kwerendy wartość tego obiektu, zobacz następujące funkcje członkowskie:

- [GetDay (GetDay)](#getday)

- [Getmonth](#getmonth)

- [GetYear (własówce](#getyear)

- [GetHour (GetHour)](#gethour)

- [GetMinute (własna)](#getminute)

- [GetSecond (GetSecond)](#getsecond)

- [Tydzień GetDayOf](#getdayofweek)

- [Getdayofyear](#getdayofyear)

Aby uzyskać więcej informacji `COleDateTime` na temat granic wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [setdate](#setdate).

## <a name="see-also"></a>Zobacz też

[Klasa COleVariant](../../mfc/reference/colevariant-class.md)<br/>
[CTime, klasa](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
