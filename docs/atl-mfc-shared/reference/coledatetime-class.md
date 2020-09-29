---
title: Klasa COleDateTime
description: Dokumentacja interfejsu API dla klasy COleDateTime MFC, która hermetyzuje `DATE` Typ danych używany w automatyzacji OLE.
ms.date: 08/27/2020
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
ms.openlocfilehash: 38c98793e7e1b22d166de8a869c57f510de7b284
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500175"
---
# <a name="coledatetime-class"></a>Klasa COleDateTime

Hermetyzuje `DATE` Typ danych, który jest używany w automatyzacji OLE.

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
|[COleDateTime:: format](#format)|Generuje sformatowaną reprezentację obiektu w postaci ciągu `COleDateTime` .|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` obiekcie jako `DBTIMESTAMP` strukturę danych.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` obiekcie jako strukturę danych [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[COleDateTime::GetAsUDATE](#getasudate)|Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` postaci jako `UDATE` struktury danych.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Tworzy `COleDateTime` obiekt, który reprezentuje bieżący czas (statyczną funkcję członkowską).|
|[COleDateTime:: GetDay](#getday)|Zwraca dzień reprezentowany przez ten `COleDateTime` obiekt (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia, jaki reprezentuje ten `COleDateTime` obiekt (niedziela = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Zwraca dzień roku reprezentowanego przez ten `COleDateTime` obiekt (1 stycznia = 1).|
|[COleDateTime:: GetHour](#gethour)|Zwraca godzinę reprezentowane przez ten `COleDateTime` obiekt (0-23).|
|[COleDateTime:: GetMinute](#getminute)|Zwraca minutę, którą ten `COleDateTime` obiekt reprezentuje (0-59).|
|[COleDateTime:: GetMonth](#getmonth)|Zwraca miesiąc reprezentowany przez ten `COleDateTime` obiekt (1-12).|
|[COleDateTime:: GetSecond](#getsecond)|Zwraca sekundę, gdy ten `COleDateTime` obiekt reprezentuje (0-59).|
|[COleDateTime:: GetStatus](#getstatus)|Pobiera stan (ważność) tego `COleDateTime` obiektu.|
|[COleDateTime:: GetYear](#getyear)|Zwraca rok reprezentowany przez ten `COleDateTime` obiekt.|
|[COleDateTime::P arseDateTime](#parsedatetime)|Odczytuje wartość daty/godziny z ciągu i ustawia wartość `COleDateTime` .|
|[COleDateTime:: SetDate](#setdate)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość daty.|
|[COleDateTime:: SetDateTime](#setdatetime)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość daty/godziny.|
|[COleDateTime:: SetStatus](#setstatus)|Ustawia stan (ważność) tego `COleDateTime` obiektu.|
|[COleDateTime:: SetTime](#settime)|Ustawia wartość tego `COleDateTime` obiektu na określoną wartość tylko czasu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime:: operator = =, COleDateTime:: operator < itd.](#coledatetime_relational_operators)|Porównaj dwie `COleDateTime` wartości.|
|[COleDateTime:: operator +, COleDateTime:: operator-](#operator_add_-)|Dodawanie i odejmowanie `COleDateTime` wartości.|
|[COleDateTime:: operator + =, COleDateTime:: operator-=](#operator_add_eq_-_eq)|Dodaj i Odejmij `COleDateTime` wartość z tego `COleDateTime` obiektu.|
|[COleDateTime:: operator =](#operator_eq)|Kopiuje `COleDateTime` wartość.|
|[COleDateTime:: operator — Data, COleDateTime:: operator — Data *](#operator_date)|Konwertuje `COleDateTime` wartość na `DATE` lub `DATE*` .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime:: m_dt](#m_dt)|Zawiera podstawową `DATE` dla tego `COleDateTime` obiektu.|
|[COleDateTime:: m_status](#m_status)|Zawiera stan tego `COleDateTime` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTime` nie ma klasy bazowej.

Jest to jeden z możliwych typów dla typu danych [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) automatyzacji OLE. `COleDateTime`Wartość reprezentuje bezwzględną wartość daty i godziny.

`DATE`Typ jest zaimplementowany jako wartość zmiennoprzecinkowa. Dni są mierzone od 30 grudnia 1899, o północy. W poniższej tabeli przedstawiono niektóre daty i ich skojarzone wartości:

|Date|Wartość|
|----------|-----------|
|29 grudnia 1899, północy|-1,0|
|29 grudnia 1899, 6 A M|-1,25|
|30 grudnia 1899, północy|0,0|
|31 grudnia 1899, północy|1,0|
|1 stycznia 1900, rano|2.25|

> [!CAUTION]
> W powyższej tabeli, chociaż wartości dni stają się ujemne przed północy w dniu 30 grudnia 1899, wartości pory dnia nie są. Na przykład 6:00 AM jest zawsze reprezentowana przez wartość ułamkową 0,25 niezależnie od tego, czy liczba całkowita reprezentująca dzień jest dodatnia (po 30 grudnia 1899) czy ujemna (przed 30 grudnia 1899). Oznacza to, że proste porównanie liczb zmiennoprzecinkowych błędnie sortuje `COleDateTime` reprezentującą 6:00 am na 7:00 **later** 12/29/1899.

`COleDateTime`Klasa obsługuje daty od 1 stycznia 100 do 31 grudnia 9999. `COleDateTime`Klasa używa kalendarza gregoriańskiego; nie obsługuje dat juliańskim. `COleDateTime` ignoruje czas letni. (Zobacz [Data i godzina: Obsługa automatyzacji](../date-and-time.md)).

> [!NOTE]
> Możesz użyć formatu, `%y` Aby pobrać dwucyfrowy rok tylko dla dat, rozpoczynając od 1900. Jeśli używasz `%y` formatu w dniu przed 1900, kod generuje błąd potwierdzenia.

Ten typ jest również używany do reprezentowania wartości tylko daty lub godziny. Zgodnie z Konwencją Data 0 (30 grudnia 1899) jest używana jako wartość tylko czasu, a godzina 00:00 (północ) jest używana tylko dla wartości typu Date.

Jeśli utworzysz Obiekt przy `COleDateTime` użyciu daty mniejszej niż 100, data zostanie zaakceptowana, ale kolejne wywołania,, `GetYear` `GetMonth` ,, `GetDay` `GetHour` `GetMinute` , i `GetSecond` Return-1. Wcześniej można użyć dwóch cyfr, ale daty muszą być 100 lub większe w MFC 4,2 i nowszych.

Aby uniknąć problemów, określ datę z czterema cyframi. Na przykład:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Podstawowe operacje arytmetyczne dla `COleDateTime` wartości używają klasy pomocnika [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` wartości definiują przedział czasu. Relacja między tymi klasami jest podobna do między [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej informacji na `COleDateTime` temat `COleDateTimeSpan` klas i, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime. h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a> Operatory relacyjne COleDateTime

Operatory porównania.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parametry

*dniu*<br/>
`COleDateTime`Obiekt, który ma zostać porównany.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> ATLASSERT pojawi się, jeśli jeden z dwóch operandów jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Przykład

Operatory **>=** , **\<=**, **>** , i **<** , spowodują, że `COleDateTime` obiekt jest ustawiony na wartość null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a> COleDateTime::COleDateTime

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

*dateSrc*<br/>
Istniejący `COleDateTime` obiekt do skopiowania do nowego `COleDateTime` obiektu.

*varSrc*<br/>
Istniejąca `VARIANT` Struktura danych (prawdopodobnie `COleVariant` obiekt) do przekonwertowania na wartość daty/godziny (VT_DATE) i skopiowana do nowego `COleDateTime` obiektu.

*dtSrc*<br/>
Wartość daty/godziny ( `DATE` ) do skopiowania do nowego `COleDateTime` obiektu.

*timeSrc*<br/>
`time_t`Wartość lub, `__time64_t` która ma zostać przekonwertowana na wartość daty/godziny i skopiowana do nowego `COleDateTime` obiektu.

*systimeSrc*<br/>
`SYSTEMTIME`Struktura, która ma zostać przekonwertowana na wartość daty/godziny i skopiowana do nowego `COleDateTime` obiektu.

*filetimeSrc*<br/>
`FILETIME`Struktura, która ma zostać przekonwertowana na wartość daty/godziny i skopiowana do nowego `COleDateTime` obiektu. Przy użyciu `FILETIME` uniwersalnego czasu koordynowanego (UTC), dlatego w przypadku przekazania czasu lokalnego do struktury wyniki będą nieprawidłowe. Aby uzyskać więcej informacji, zobacz [czasy plików](/windows/win32/SysInfo/file-times) w Windows SDK.

*nYear*, *nMonth*, *nbłędny dzień*, *ngodzina*, *Nmin*, *NSEC*<br/>
Wskaż wartości daty i godziny, które mają zostać skopiowane do nowego `COleDateTime` obiektu.

*wDosDate*, *wDosTime*<br/>
Wartości daty i godziny systemu MS-DOS do przekonwertowania na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.

*Znacznik czasu*<br/>
Odwołanie do struktury [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) zawierającego bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleDateTime` obiekty zainicjowane do określonej wartości. W poniższej tabeli przedstawiono prawidłowe zakresy dla każdego składnika daty i godziny:

|Składnik daty/godziny|Prawidłowy zakres|
|--------------------------|-----------------|
|rok|100 – 9999|
|miesiąc|0 - 12|
|dzień|0 - 31|
|godzina|0 - 23|
|minuta|0 - 59|
|sekunda|0 - 59|

Należy zauważyć, że rzeczywiste górne ograniczenie składnika Day różni się w zależności od składników miesiąca i roku. Aby uzyskać szczegółowe informacje, zobacz `SetDate` lub `SetDateTime` funkcje członkowskie.

Poniżej znajduje się krótki opis każdego konstruktora:

- `COleDateTime(`**)** Konstruuje `COleDateTime` obiekt zainicjowany do wartości 0 (północ, 30 grudnia 1899).

- `COleDateTime(``dateSrc` **)** Konstruuje `COleDateTime` obiekt z istniejącego `COleDateTime` obiektu.

- `COleDateTime(`*varSrc* **)** konstruuje `COleDateTime` obiekt. Próbuje skonwertować `VARIANT` strukturę lub obiekt [COleVariant](../../mfc/reference/colevariant-class.md) na wartość daty/godziny ( `VT_DATE` ). Jeśli ta konwersja zakończyła się pomyślnie, przekonwertowana wartość jest kopiowana do nowego `COleDateTime` obiektu. Jeśli tak nie jest, wartość `COleDateTime` obiektu jest ustawiona na 0 (północ, 30 grudnia 1899) i jego stan jest nieprawidłowy.

- `COleDateTime(``dtSrc` **)** Konstruuje `COleDateTime` obiekt z `DATE` wartości.

- `COleDateTime(``timeSrc` **)** Konstruuje `COleDateTime` obiekt z `time_t` wartości.

- `COleDateTime(`*systimeSrc* **)** konstruuje `COleDateTime` obiekt z `SYSTEMTIME` wartości.

- `COleDateTime(``filetimeSrc` **)** Konstruuje `COleDateTime` obiekt z `FILETIME` wartości. . Przy użyciu `FILETIME` uniwersalnego czasu koordynowanego (UTC), dlatego w przypadku przekazania czasu lokalnego do struktury wyniki będą nieprawidłowe. Aby uzyskać więcej informacji, zobacz [czasy plików](/windows/win32/SysInfo/file-times) w Windows SDK.

- `COleDateTime(``nYear`, `nMonth` ,,, `nDay` `nHour` `nMin` , `nSec` **)** Konstruuje `COleDateTime` obiekt z określonych wartości liczbowych.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Konstruuje `COleDateTime` obiekt z określonych wartości daty i godziny systemu MS-DOS.

Aby uzyskać więcej informacji na temat `time_t` typu danych, zobacz [Time](../../c-runtime-library/reference/time-time32-time64.md) function in the *Run-Time Library Reference*.

Aby uzyskać więcej informacji, zobacz struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) w Windows SDK.

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

> [!NOTE]
> Konstruktor używający `DBTIMESTAMP` parametru jest dostępny tylko wtedy, gdy jest dołączony OLEDB. h.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a> COleDateTime:: format

Tworzy sformatowaną reprezentację wartości daty/godziny.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Wskazuje jedną z następujących flag ustawień regionalnych:

- LOCALE_NOUSEROVERRIDE Użyj domyślnych ustawień regionalnych systemu zamiast niestandardowych ustawień użytkownika.

- VAR_TIMEVALUEONLY zignorować część daty podczas analizowania.

- VAR_DATEVALUEONLY zignorować części czasu podczas analizowania.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych do użycia podczas konwersji. Aby uzyskać więcej informacji o identyfikatorach języka, zobacz [identyfikatory języków](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Ciąg formatowania podobny do `printf` ciągu formatowania. Każdy kod formatowania, poprzedzony znakiem procentu ( `%` ), jest zastępowany przez odpowiedni `COleDateTime` składnik. Inne znaki w ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Aby uzyskać więcej informacji, zobacz Funkcja Run-Time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Wartość i znaczenie kodów formatowania dla `Format` są następujące:

- `%H` Godz. w bieżącym dniu

- `%M` Minuty w bieżącej godzinie

- `%S` Sekundy w bieżącej minucie

- `%%` Znak procentu

*nFormatID*<br/>
Identyfikator zasobu dla ciągu sterującego formatu.

### <a name="return-value"></a>Wartość zwracana

A `CString` , który zawiera sformatowaną wartość daty/godziny.

### <a name="remarks"></a>Uwagi

Jeśli stan tego `COleDateTime` obiektu ma wartość null, zwracana wartość jest ciągiem pustym. Jeśli stan jest nieprawidłowy, ciąg zwracany jest określany przez zasób ciągu ATL_IDS_DATETIME_INVALID.

Poniżej znajduje się krótki opis trzech formularzy dla tej funkcji:

`Format`( *flagiDW*, *LCID*)<br/>
Ten formularz służy do formatowania wartości przy użyciu specyfikacji języka (identyfikatorów ustawień regionalnych) dla daty i godziny. Przy użyciu parametrów domyślnych ten formularz drukuje datę i godzinę, chyba że część czasu jest równa 0 (północ), w tym przypadku zostanie wydrukowany tylko data lub część daty równa 0 (30 grudnia 1899), w tym przypadku zostanie wydrukowany tylko czas. Jeśli wartość daty/godziny jest równa 0 (30 grudnia 1899, północy), ten formularz z domyślnymi parametrami będzie drukować o północy.

`Format`( *lpszFormat*)<br/>
Ten formularz służy do formatowania wartości przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, poprzedzone znakiem procentu (%), jak w `printf` . Ciąg formatowania jest przenoszona jako parametr do funkcji. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w dokumentacji dotyczącej biblioteki wykonawczej.

`Format`( *nFormatID*)<br/>
Ten formularz służy do formatowania wartości przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, poprzedzone znakiem procentu (%), jak w `printf` . Ciąg formatowania jest zasobem. Identyfikator tego zasobu ciągu jest przekazaniem jako parametr. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> COleDateTime::GetAsDBTIMESTAMP

Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` obiekcie jako `DBTIMESTAMP` strukturę danych.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parametry

*Znacznik czasu*<br/>
Odwołanie do struktury [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zapisuje wyniki w strukturze *sygnatur czasowych* , do których się odwołuje. `DBTIMESTAMP`Struktura danych zainicjowana przez tę funkcję będzie mieć swój `fraction` element członkowski ustawiony na wartość zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a> COleDateTime::GetAsSystemTime

Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` obiekcie jako `SYSTEMTIME` strukturę danych.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*SysTime —*<br/>
Odwołanie do struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , aby otrzymać przekonwertowaną wartość daty/godziny z `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli powodzenie; FAŁSZ, jeśli konwersja nie powiedzie się lub jeśli `COleDateTime` obiekt ma wartość null lub jest nieprawidłowy.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime` Zapisuje czas, który powstaje w przywoływanym obiekcie *SysTime —* . `SYSTEMTIME`Struktura danych zainicjowana przez tę funkcję będzie mieć swój `wMilliseconds` element członkowski ustawiony na wartość zero.

Aby uzyskać więcej informacji na temat informacji o stanie przechowywanych w `COleDateTime` obiekcie, zobacz [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a> COleDateTime::GetAsUDATE

Wywołaj tę metodę, aby uzyskać godzinę w `COleDateTime` obiekcie jako `UDATE` strukturę danych.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parametry

*uDate*<br/>
Odwołanie do struktury, `UDATE` która ma otrzymać przekonwertowaną wartość daty/godziny z `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli powodzenie; FAŁSZ, jeśli konwersja nie powiedzie się lub jeśli `COleDateTime` obiekt ma wartość null lub jest nieprawidłowy.

### <a name="remarks"></a>Uwagi

`UDATE`Struktura reprezentuje datę unpackd.

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a> COleDateTime::GetCurrentTime

Wywołaj tę statyczną funkcję członkowską, aby zwrócić bieżącą wartość daty/godziny.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a> COleDateTime:: GetDay

Pobiera dzień miesiąca reprezentowanego przez tę wartość daty/godziny.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień miesiąca reprezentowanego przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać dnia.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 1 do 31.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a> COleDateTime::GetDayOfWeek

Pobiera dzień tygodnia reprezentowany przez tę wartość daty/godziny.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień tygodnia reprezentowany przez wartość tego `COleDateTime` obiektu lub jeśli nie można `COleDateTime::error` uzyskać dnia tygodnia.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 1 do 7, gdzie 1 = niedziela, 2 = poniedziałek itd.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a> COleDateTime::GetDayOfYear

Pobiera dzień roku reprezentowanego przez tę wartość daty/godziny.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień roku reprezentowanego przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` w przypadku, gdy nie można uzyskać dnia roku.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 1 do 366, gdzie 1 stycznia = 1.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a> COleDateTime:: GetHour

Pobiera godzinę reprezentowaną przez tę wartość daty/godziny.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Godzina reprezentowana przez wartość tego `COleDateTime` obiektu lub jeśli nie można `COleDateTime::error` uzyskać godziny.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 0 do 23.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a> COleDateTime:: GetMinute

Pobiera minutę reprezentowane przez tę wartość daty/godziny.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Minuta reprezentowana przez wartość tego `COleDateTime` obiektu lub jeśli nie można `COleDateTime::error` uzyskać minuty.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 0 do 59.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a> COleDateTime:: GetMonth

Pobiera miesiąc reprezentowany przez tę wartość daty/godziny.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Miesiąc reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` w przypadku, gdy nie można uzyskać miesiąca.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 1 do 12.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład dla [getDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a> COleDateTime:: GetSecond

Pobiera sekundę reprezentowane przez tę wartość daty/godziny.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Druga reprezentowana przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli druga nie można uzyskać.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 0 do 59.

> [!NOTE]
> `COleDateTime`Klasa nie obsługuje sekund przestępnych.

Aby uzyskać więcej informacji na temat implementacji programu `COleDateTime` , zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a> COleDateTime:: GetStatus

Pobiera stan (ważność) danego `COleDateTime` obiektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan tej `COleDateTime` wartości. Jeśli wywołasz `GetStatus` `COleDateTime` obiekt skonstruowany przy użyciu domyślnego, zostanie zwrócony prawidłowy. Jeśli wywołasz `GetStatus` `COleDateTime` obiekt zainicjowany z konstruktorem ustawionym na wartość null, `GetStatus` zwróci wartość null.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowana przez `DateTimeStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleDateTime` klasie.

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

- `COleDateTime::error` Wskazuje, że wystąpił błąd podczas próby uzyskania części wartości daty/godziny.

- `COleDateTime::valid` Wskazuje, że ten `COleDateTime` obiekt jest prawidłowy.

- `COleDateTime::invalid` Wskazuje, że ten `COleDateTime` obiekt jest nieprawidłowy; oznacza to, że jego wartość może być niepoprawna.

- `COleDateTime::null` Wskazuje, że ten `COleDateTime` obiekt ma wartość null, to oznacza, że nie podano wartości dla tego obiektu. (Jest to wartość "null" w sensie bazy danych "bez wartości", w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTime` obiektu jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość jest ustawiona z `VARIANT` lub `COleVariant` wartości, której nie można przekonwertować na wartość daty/godziny.

- Jeśli wartość jest ustawiona z `time_t` , `SYSTEMTIME` lub `FILETIME` wartość, która nie może zostać przekonwertowana na prawidłową wartość daty/godziny.

- Jeśli wartość jest ustawiona przez `SetDateTime` przy użyciu nieprawidłowych wartości parametrów.

- Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji przypisywania arytmetycznego, mianowicie `+=` lub `-=` .

- Jeśli nieprawidłowa wartość została przypisana do tego obiektu.

- Jeśli stan tego obiektu został jawnie ustawiony na nieprawidłowy przy użyciu `SetStatus` .

Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowe, zobacz następujące funkcje Członkowskie:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +,-](#operator_add_-)

- [operator + =,-=](#operator_add_eq_-_eq)

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a> COleDateTime:: GetYear

Pobiera rok reprezentowany przez tę wartość daty/godziny.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Rok reprezentowany przez wartość tego `COleDateTime` obiektu lub jeśli nie można `COleDateTime::error` uzyskać roku.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracane mieszczą się w zakresie od 100 do 9999, który obejmuje Century.

Aby uzyskać informacje na temat innych funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

Zobacz przykład dla [getDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a> COleDateTime:: m_dt

Bazowa `DATE` Struktura dla tego `COleDateTime` obiektu.

```
DATE m_dt;
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w obiekcie, `DATE` do którego uzyskuje dostęp wskaźnik zwracany przez tę funkcję, spowoduje zmianę wartości tego `COleDateTime` obiektu. Nie powoduje zmiany stanu tego `COleDateTime` obiektu.

Aby uzyskać więcej informacji na temat implementacji `DATE` obiektu, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a> COleDateTime:: m_status

Zawiera stan tego `COleDateTime` obiektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Uwagi

Typ tego elementu członkowskiego danych jest typem wyliczanym `DateTimeStatus` , który jest zdefiniowany w `COleDateTime` klasie. Aby uzyskać więcej informacji, zobacz [COleDateTime:: GetStatus](#getstatus).

> [!CAUTION]
> Ten element członkowski danych ma na celu zaawansowaną sytuację programistyczną. Należy użyć wbudowanej funkcji składowej [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz, `SetStatus` Aby uzyskać dalsze ostrzeżenie dotyczące jawnego ustawiania tego elementu członkowskiego danych.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a> COleDateTime:: operator =

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

Te przeciążone operatory przypisania kopiują źródłową wartość daty/godziny do tego `COleDateTime` obiektu. Poniżej znajduje się krótki opis każdego z następujących przeciążonych operatorów przypisania:

- **operator = (** `dateSrc` **)** wartość i stan operandu są kopiowane do tego `COleDateTime` obiektu.

- **operator = (** *varSrc* **)** Jeśli konwersja wartości [wariantu](/windows/win32/api/oaidl/ns-oaidl-variant) (lub obiektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na datę/godzinę (VT_DATE) powiedzie się, przekonwertowana wartość jest kopiowana do tego `COleDateTime` obiektu, a jego stan jest ustawiony na prawidłowy. Jeśli konwersja nie powiedzie się, wartość tego obiektu jest równa zero (30 grudnia 1899, północy) i jego stan jest nieprawidłowy.

- **operator = (** `dtSrc` **)** `DATE` wartość jest kopiowana do tego `COleDateTime` obiektu, a jego stan jest ustawiony na wartość prawidłowy.

- **operator = (** `timeSrc` **)** `time_t` wartość lub `__time64_t` jest konwertowana i kopiowana do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na wartość prawidłowy; Jeśli to się nie powiedzie, jest ono ustawione na nieprawidłowe.

- **operator = (** *systimeSrc* **)** Wartość [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) jest konwertowana i kopiowana do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na wartość prawidłowy; Jeśli to się nie powiedzie, jest ono ustawione na nieprawidłowe.

- **operator = (** `uDate` **)** `UDATE` wartość jest konwertowana i kopiowana do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na wartość prawidłowy; Jeśli to się nie powiedzie, jest ono ustawione na nieprawidłowe. `UDATE`Struktura reprezentuje datę unpackd. Aby uzyskać więcej informacji, zobacz Funkcja [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **operator = (** `filetimeSrc` **)** wartość [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) jest konwertowana i kopiowana do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na wartość prawidłowy; w przeciwnym razie jest ustawiony na nieprawidłowy. `FILETIME` używa uniwersalnego czasu koordynowanego (UTC), więc jeśli upłynie czas UTC w strukturze, wyniki zostaną przekonwertowane z czasu UTC na czas lokalny i będą przechowywane w postaci czasu wariantu. Takie zachowanie jest takie samo jak w Visual C++ 6,0 i Visual C++ .NET 2003 SP2. Aby uzyskać więcej informacji, zobacz [czasy plików](/windows/win32/SysInfo/file-times) w Windows SDK.

Aby uzyskać więcej informacji, zobacz wpis [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) w Windows SDK.

Aby uzyskać więcej informacji na temat `time_t` typu danych, zobacz [Time](../../c-runtime-library/reference/time-time32-time64.md) function in the *Run-Time Library Reference*.

Aby uzyskać więcej informacji, zobacz struktury [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) i [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) w Windows SDK.

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a> COleDateTime:: operator +,-

Dodawanie i odejmowanie `ColeDateTime` wartości.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Uwagi

`COleDateTime` obiekty reprezentują czasy bezwzględne. Obiekty [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) reprezentują względne czasy. Pierwsze dwa operatory umożliwiają dodawanie i odejmowanie `COleDateTimeSpan` wartości z `COleDateTime` wartości. Trzeci operator pozwala odjąć jedną `COleDateTime` wartość od drugiej do `COleDateTimeSpan` wartości.

Jeśli jeden z operandów ma wartość null, stan `COleDateTime` wartości wyników jest równy null.

Jeśli wartość wynikowa `COleDateTime` znajduje się poza granicami akceptowalnych wartości, stan tej `COleDateTime` wartości jest nieprawidłowy.

Jeśli jeden z operandów jest nieprawidłowy, a drugi nie ma wartości null, stan wartości uzyskanej `COleDateTime` jest nieprawidłowy.

**+** Operatory i **-** będą zatwierdzać, czy `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [Operatory relacyjne COleDateTime](#coledatetime_relational_operators) na przykład.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTime:: operator + =,-=

Dodaj i Odejmij `ColeDateTime` wartość z tego `COleDateTime` obiektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory umożliwiają dodawanie i odejmowanie `COleDateTimeSpan` wartości do i z tego typu `COleDateTime` . Jeśli jeden z operandów ma wartość null, stan `COleDateTime` wartości wyników jest równy null.

Jeśli wartość wynikowa `COleDateTime` znajduje się poza granicami akceptowalnych wartości, stan tej `COleDateTime` wartości jest ustawiony na nieprawidłowy.

Jeśli jeden z operandów jest nieprawidłowy i inne nie ma wartości null, stan `COleDateTime` wartości wyniki jest nieprawidłowy.

Aby uzyskać więcej informacji na temat prawidłowych i nieprawidłowych wartości stanu, zobacz zmienną członkowską [m_status](#m_status) .

**+=** Operatory i **-=** będą zatwierdzać, czy `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [Operatory relacyjne COleDateTime](#coledatetime_relational_operators) na przykład.

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a> COleDateTime:: operator — Data

Konwertuje `ColeDateTime` wartość na `DATE` .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca `DATE` obiekt, którego wartość jest kopiowana z tego `COleDateTime` obiektu. Aby uzyskać więcej informacji na temat implementacji `DATE` obiektu, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

Operator zostanie poproszony, `DATE` Jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [Operatory relacyjne COleDateTime](#coledatetime_relational_operators) na przykład.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a> COleDateTime::P arseDateTime

Analizuje ciąg w celu odczytania wartości daty/godziny.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*lpszDate*<br/>
Wskaźnik do ciągu zakończonego wartością null, który ma zostać przeanalizowany. Aby uzyskać szczegółowe informacje, zobacz uwagi.

*flagiDW*<br/>
Wskazuje flagi dla ustawień regionalnych i analizy. Co najmniej jedna z następujących flag:

- LOCALE_NOUSEROVERRIDE Użyj domyślnych ustawień regionalnych systemu zamiast niestandardowych ustawień użytkownika.

- VAR_TIMEVALUEONLY zignorować część daty podczas analizowania.

- VAR_DATEVALUEONLY zignorować części czasu podczas analizowania.

*lcid*<br/>
Wskazuje identyfikator ustawień regionalnych do użycia podczas konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ciąg został pomyślnie przekonwertowany na wartość daty/godziny, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli ciąg został pomyślnie przekonwertowany na wartość daty/godziny, wartość tego `COleDateTime` obiektu jest ustawiana na tę wartość, a jego stan jest prawidłowy.

> [!NOTE]
> Wartości roku muszą należeć do zakresu od 100 do 9999 włącznie.

Parametr *lpszDate* może przyjmować różne formaty. Na przykład następujące ciągi zawierają akceptowalne formaty daty i godziny:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

Identyfikator ustawień regionalnych ma także wpływ na to, czy format ciągu jest akceptowalny do konwersji na wartość daty/godziny.

W przypadku VAR_DATEVALUEONLY wartość czasu jest ustawiana na czas 0 lub północy. W przypadku VAR_TIMEVALUEONLY wartość daty jest równa dacie 0, co oznacza 30 grudnia 1899.

Jeśli nie można przekonwertować ciągu na wartość daty/godziny lub w przypadku przepełnienia liczbowego, stan tego `COleDateTime` obiektu jest nieprawidłowy.

Aby uzyskać więcej informacji na temat granic i implementacji `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a> COleDateTime:: SetDate

Ustawia datę tego `COleDateTime` obiektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nYear*\
Wskazuje rok, który ma zostać skopiowany do tego `COleDateTime` obiektu.

*nMonth*\
Wskazuje miesiąc, który ma zostać skopiowany do tego `COleDateTime` obiektu.

*Nbłędny dzień*\
Wskazuje dzień, który ma zostać skopiowany do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość tego `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie 1. Ta wartość zwracana jest oparta na `DateTimeStatus` typie wyliczeniowym. Aby uzyskać więcej informacji, zobacz Funkcja [SetStatus](#setstatus) elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Data jest ustawiona na określone wartości. Czas jest ustawiany na czas 0, północy.

Zapoznaj się z poniższą tabelą dotyczącą wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nYear*|100 – 9999|
|*nMonth*|1 - 12|
|*Nbłędny dzień*|0 - 31|

Jeśli dzień miesiąca przepełnił się, zostanie on przekonwertowany na poprawny dzień następnego miesiąca, a miesiąc i/lub rok są odpowiednio zwiększane. Wartość dnia zero wskazuje ostatni dzień poprzedniego miesiąca. Zachowanie jest takie samo jak w przypadku programu `SystemTimeToVariantTime` .

Jeśli wartość daty określona przez parametry jest nieprawidłowa, stan tego obiektu jest ustawiony na `COleDateTime::invalid` . Należy użyć [GetStatus](#getstatus) , aby sprawdzić poprawność `DATE` wartości i nie należy zakładać, że wartość [m_dt](#m_dt) pozostanie niezmodyfikowana.

Poniżej przedstawiono kilka przykładów wartości daty:

|*nYear*|*nMonth*|*Nbłędny dzień*|Wartość|
|-------------|--------------|------------|-----------|
|2000|2|29|29 lutego 2000|
|1776|7|4|4 lipca 1776|
|1925|4|35|35 kwietnia 1925 (nieprawidłowa data)|
|10 000|1|1|1 stycznia 10000 (nieprawidłowa data)|

Aby ustawić datę i godzinę, zobacz [COleDateTime:: SetDateTime](#setdatetime).

Aby uzyskać informacje na temat funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a> COleDateTime:: SetDateTime

Ustawia datę i godzinę tego `COleDateTime` obiektu.

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

*nYear*, *nMonth*, *nbłędny dzień*, *ngodzina*, *Nmin*, *NSEC*<br/>
Wskaż składniki daty i godziny, które mają być skopiowane do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość tego `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie 1. Ta wartość zwracana jest oparta na `DateTimeStatus` typie wyliczeniowym. Aby uzyskać więcej informacji, zobacz Funkcja [SetStatus](#setstatus) elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Zapoznaj się z poniższą tabelą dotyczącą wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nYear*|100 – 9999|
|*nMonth*|1 - 12|
|*Nbłędny dzień*|0 - 31|
|*Ngodzina*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Jeśli dzień miesiąca przepełnił się, zostanie on przekonwertowany na poprawny dzień następnego miesiąca, a miesiąc i/lub rok są odpowiednio zwiększane. Wartość dnia zero wskazuje ostatni dzień poprzedniego miesiąca. Zachowanie jest takie samo jak [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Jeśli wartość daty lub godziny określona przez parametry jest nieprawidłowa, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu nie jest zmieniana.

Oto kilka przykładów wartości czasu:

|*Ngodzina*|*nMin*|*nSec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Poniżej przedstawiono kilka przykładów wartości daty:

|*nYear*|*nMonth*|*Nbłędny dzień*|Wartość|
|-------------|--------------|------------|-----------|
|1995|4|15|15 kwietnia 1995|
|1789|7|14|17 lipca 1789|
|1925|2|30|Nieprawidłowy|
|10 000|1|1|Nieprawidłowy|

Aby ustawić tylko datę, zobacz [COleDateTime:: SetDate](#setdate). Aby ustawić tylko czas, zobacz [COleDateTime:: SetTime](#settime).

Aby uzyskać informacje na temat funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a> COleDateTime:: SetStatus

Ustawia stan tego `COleDateTime` obiektu.

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stany*<br/>
Nowa wartość stanu dla tego `COleDateTime` obiektu.

### <a name="remarks"></a>Uwagi

Wartość parametru *status* jest definiowana przez `DateTimeStatus` Typ wyliczeniowy, który jest zdefiniowany w `COleDateTime` klasie. Aby uzyskać szczegółowe informacje, zobacz [COleDateTime:: GetStatus](#getstatus) .

> [!CAUTION]
> Ta funkcja jest dla zaawansowanych sytuacji programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. Będzie najczęściej używany do ustawienia stanu na **wartość null** lub **nieprawidłowy**. Operator przypisania ([operator =](#operator_eq)) i [SetDateTime](#setdatetime) ustawia stan obiektu na podstawie wartości źródłowych.

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a> COleDateTime:: SetTime

Ustawia godzinę tego `COleDateTime` obiektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*ngodzina*, *Nmin*, *NSEC*<br/>
Wskaż składniki czasu, które mają być skopiowane do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość tego `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie 1. Ta wartość zwracana jest oparta na `DateTimeStatus` typie wyliczeniowym. Aby uzyskać więcej informacji, zobacz Funkcja [SetStatus](#setstatus) elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Czas jest ustawiany na określone wartości. Data jest ustawiona na datę 0, co oznacza 30 grudnia 1899.

Zapoznaj się z poniższą tabelą dotyczącą wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*Ngodzina*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Jeśli wartość czasu określona przez parametry jest nieprawidłowa, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu nie jest zmieniana.

Oto kilka przykładów wartości czasu:

|*Ngodzina*|*nMin*|*nSec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Aby ustawić datę i godzinę, zobacz [COleDateTime:: SetDateTime](#setdatetime).

Aby uzyskać informacje na temat funkcji Członkowskich, które wysyłają zapytania do wartości tego `COleDateTime` obiektu, zobacz następujące funkcje Członkowskie:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granic dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../date-and-time.md).

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [SetDate](#setdate).

## <a name="see-also"></a>Zobacz też

[Klasa COleVariant](../../mfc/reference/colevariant-class.md)<br/>
[Klasa CTime](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
