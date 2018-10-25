---
title: COleDateTime, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4490eef3427f66456ec79ae2f5429d309a82a54
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057404"
---
# <a name="coledatetime-class"></a>COleDateTime, klasa

Hermetyzuje `DATE` typu danych, który jest używany w automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleDateTime
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Konstruuje `COleDateTime` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::Format](#format)|Generuje reprezentację ciągu sformatowaną `COleDateTime` obiektu.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` obiektu jako `DBTIMESTAMP` strukturę danych.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` obiektu jako [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę danych.|
|[COleDateTime::GetAsUDATE](#getasudate)|Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` jako `UDATE` strukturę danych.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Tworzy `COleDateTime` obiekt, który reprezentuje bieżący czas (statyczny element członkowski funkcji).|
|[COleDateTime::GetDay](#getday)|Zwraca dzień to `COleDateTime` obiekt reprezentuje (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia, w tym `COleDateTime` obiekt reprezentuje (niedziela = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Zwraca dzień roku, to `COleDateTime` obiekt reprezentuje (1 stycznia = 1).|
|[COleDateTime::GetHour](#gethour)|Zwraca godzinę, to `COleDateTime` obiekt reprezentuje (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Zwraca minuty, to `COleDateTime` obiekt reprezentuje (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Zwraca miesiąc, to `COleDateTime` obiekt reprezentuje (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Zwraca sekundy, to `COleDateTime` obiekt reprezentuje (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Pobiera stan (ważność) to `COleDateTime` obiektu.|
|[COleDateTime::GetYear](#getyear)|Zwraca rok, to `COleDateTime` obiekt reprezentuje.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Odczytuje wartość daty/godziny z ciągu i ustawia wartość `COleDateTime`.|
|[COleDateTime::SetDate](#setdate)|Ustawia wartość to `COleDateTime` obiekt z podaną wartością w trybie tylko do daty.|
|[COleDateTime::SetDateTime](#setdatetime)|Ustawia wartość tego `COleDateTime` obiektu do wartości określonej daty/godziny.|
|[COleDateTime::SetStatus](#setstatus)|Ustawia stan (ważność) to `COleDateTime` obiektu.|
|[COleDateTime::SetTime](#settime)|Ustawia wartość to `COleDateTime` obiekt z podaną wartością w trybie tylko do czasu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::operator == COleDateTime::operator < itp.](#coledatetime_relational_operators)|Porównanie dwóch `COleDateTime` wartości.|
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|Dodawanie i odejmowanie `COleDateTime` wartości.|
|[COleDateTime::operator +=, COleDateTime::operator-=](#operator_add_eq_-_eq)|Dodawanie i odejmowanie `COleDateTime` wartości z tego `COleDateTime` obiektu.|
|[COleDateTime::operator =](#operator_eq)|Kopiuje `COleDateTime` wartość.|
|[COleDateTime::operator DATE, Date COleDateTime::operator *](#operator_date)|Konwertuje `COleDateTime` wartością do `DATE` lub `DATE*`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Zawiera podstawowe `DATE` tego `COleDateTime` obiektu.|
|[COleDateTime::m_status](#m_status)|Zawiera informacje o stanie tego `COleDateTime` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDateTime` nie ma klasy bazowej.

Jest jednym z możliwych typów dla [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) typ danych w automatyzacji OLE. A `COleDateTime` wartość reprezentuje bezwzględną wartość daty i godziny.

`DATE` Typ jest zaimplementowany jako wartość zmiennoprzecinkowa. Dni jest mierzony od 30 grudnia 1899 o północy. W poniższej tabeli przedstawiono niektóre dat i ich skojarzone wartości:

|Data|Wartość|
|----------|-----------|
|29 grudnia 1899 północy|-1.0|
|29 grudnia 1899, przedpołudnie 6|-1.25|
|30 grudnia 1899 północy|0.0|
|Do 31 grudnia 1899 północy|1.0|
|1 stycznia 1900, godziny 6: 00|2.25|

> [!CAUTION]
> Należy pamiętać, w powyższej tabeli, chociaż wartości dni ujemna wcześniejszą niż północ na 30 grudnia 1899 wartości pory dnia nie są. Na przykład 6:00 AM zawsze jest reprezentowany przez wartość ułamkowa 0,25 niezależnie od tego, czy liczbę całkowitą przedstawiającą dzień jest dodatnia (po 30 grudnia 1899) lub ujemna (przed 30 grudnia 1899). Oznacza to, że błędnie posortuj proste zmiennoprzecinkowy porównania punktu `COleDateTime` reprezentujący 6:00 AM 12/29/1899 **później** niż jeden reprezentujący 7:00:00 w dniu.

`COleDateTime` Klasa obsługuje daty od 1 stycznia 100 r. do 31 grudnia 9999 r. `COleDateTime` Klasa korzysta z kalendarza gregoriańskiego; nie obsługuje daty juliańskim. `COleDateTime` ignoruje czasu letniego. (Zobacz [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Możesz użyć `%y` formatu w celu pobrania dwucyfrowy rok tylko w przypadku daty od 1900. Jeśli używasz `%y` format na datę wcześniejszą 1900 kod generuje błąd ASERCJI.

Ten typ jest również używany do reprezentowania wartości daty lub godziny. Zgodnie z Konwencją Data 0 (30 grudnia 1899) jest używana dla wartości tylko do czasu i godziny 00:00 (północ) jest używana dla wartości daty.

Jeśli tworzysz `COleDateTime` obiektu za pomocą daty mniej niż 100 Data jest akceptowane, ale kolejne wywołania `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, i `GetSecond` zakończyć się niepowodzeniem i zwracają wartość -1. Wcześniej można użyć dwóch cyfr daty, ale daty muszą być 100 lub większej w MFC 4.2 lub nowszy.

Aby uniknąć problemów, należy określić datę czterech cyfr. Na przykład:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Podstawowe operacje arytmetyczne na `COleDateTime` wartości należy użyć klasy Pomocnika [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` wartości zdefiniować interwał czasu. Relacja między tymi klasami jest podobny do przedstawionego między [CTime](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Aby uzyskać więcej informacji na temat `COleDateTime` i `COleDateTimeSpan` klas, zapoznaj się z artykułem [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  COleDateTime, operatory relacyjne

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

*Data*<br/>
`COleDateTime` Obiekt do porównania.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  ATLASSERT wystąpi jedno z dwóch argumentów operacji jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Przykład

Operatory **>=**, **\< =**, **>**, i **<**, będzie potwierdzenia, jeśli `COleDateTime` obiekt jest ustawiony na wartość null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

Konstruuje `COleDateTime` obiektu.

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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```

### <a name="parameters"></a>Parametry

*dateSrc*<br/>
Istniejące `COleDateTime` obiektu do skopiowania w nowe `COleDateTime` obiektu.

*varSrc*<br/>
Istniejące `VARIANT` struktury danych (prawdopodobnie `COleVariant` obiektu) można przekonwertować na wartość daty/godziny (VT_DATE) i skopiowane do nowego `COleDateTime` obiektu.

*dtSrc*<br/>
Data/Godzina (`DATE`) wartość do skopiowania w nowe `COleDateTime` obiektu.

*timeSrc*<br/>
A `time_t` lub `__time64_t` wartość może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.

*systimeSrc*<br/>
A `SYSTEMTIME` struktura może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.

*filetimeSrc*<br/>
A `FILETIME` struktura może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu. Należy pamiętać, że `FILETIME` korzysta z uniwersalnego czasu koordynowanego (UTC), więc jeśli przekażesz czasu lokalnego w strukturze będą niepoprawne wyniki. Zobacz [czasy](/windows/desktop/SysInfo/file-times) w zestawie Windows SDK, aby uzyskać więcej informacji.

*nYear*, *nMonth*, *nbłędny dzień*, *Ngodzina*, *nMin*, *nSec*<br/>
Wskazuje wartości daty i godziny do skopiowania w nowe `COleDateTime` obiektu.

*wDosDate*, *wDosTime*<br/>
Wartości daty i godziny może zostać przekonwertowana na wartość daty/godziny i skopiowane do nowego systemu MS-DOS `COleDateTime` obiektu.

*znacznika dbts*<br/>
Odwołanie do [Odcisk czasowy](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury zawierającej bieżący czas lokalny.

### <a name="remarks"></a>Uwagi

Te konstruktory tworzenia nowych `COleDateTime` obiektów inicjowane z podaną wartością. W poniższej tabeli przedstawiono prawidłowe zakresy dla każdego składnika daty i godziny:

|Składnik daty/godziny|Prawidłowy zakres|
|--------------------------|-----------------|
|Rok|100 - 9999|
|Miesiąc|0 - 12|
|dzień|0 - 31|
|Godzina|0 - 23|
|Minuta|0 - 59|
|Sekundy|0 - 59|

Należy zauważyć, że różni się w rzeczywistych górną granicę składnik dnia na podstawie części miesiąca i roku. Aby uzyskać więcej informacji, zobacz `SetDate` lub `SetDateTime` funkcji elementów członkowskich.

Poniżej przedstawiono krótki opis każdego Konstruktor:

- `COleDateTime(` **)** Tworzy `COleDateTime` obiektu inicjowane na wartość 0 (o północy, 30 grudnia 1899).

- `COleDateTime(` `dateSrc` **)** Tworzy `COleDateTime` obiektu z istniejącego `COleDateTime` obiektu.

- `COleDateTime(` *varSrc* **)** tworzy `COleDateTime` obiektu. Stara się przekonwertować `VARIANT` struktury lub [COleVariant](../../mfc/reference/colevariant-class.md) obiekt do daty/godziny ( `VT_DATE`) wartość. Jeśli ta konwersja zakończy się pomyślnie, przekonwertowana wartości jest kopiowana do nowej `COleDateTime` obiektu. Jeśli nie, to wartość `COleDateTime` obiekt jest ustawiony na 0 (o północy, 30 grudnia 1899) i jej stanie się nieprawidłowy.

- `COleDateTime(` `dtSrc` **)** Tworzy `COleDateTime` obiektu z `DATE` wartości.

- `COleDateTime(` `timeSrc` **)** Tworzy `COleDateTime` obiektu z `time_t` wartości.

- `COleDateTime(` *systimeSrc* **)** tworzy `COleDateTime` obiektu z `SYSTEMTIME` wartości.

- `COleDateTime(` `filetimeSrc` **)** Tworzy `COleDateTime` obiektu z `FILETIME` wartości. . Należy pamiętać, że `FILETIME` korzysta z uniwersalnego czasu koordynowanego (UTC), więc jeśli przekażesz czasu lokalnego w strukturze będą niepoprawne wyniki. Zobacz [czasy](/windows/desktop/SysInfo/file-times) w zestawie Windows SDK, aby uzyskać więcej informacji.

- `COleDateTime(` `nYear``nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Tworzy `COleDateTime` obiektu z określonej wartości liczbowe.

- `COleDateTime(` `wDosDate``wDosTime` **)** Tworzy `COleDateTime` obiektu z określonej wartości daty i godziny systemu MS-DOS.

Aby uzyskać więcej informacji na temat `time_t` typ danych, zobacz [czasu](../../c-runtime-library/reference/time-time32-time64.md) działa w programach *odwołanie do biblioteki wykonawczej*.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) struktur w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Za pomocą konstruktora `DBTIMESTAMP` parametr jest dostępna tylko, gdy OLEDB.h jest dołączony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

Tworzy reprezentację sformatowaną wartość daty/godziny.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*Flagidw*<br/>
Wskazuje, jedną z następujących flag ustawień regionalnych:

- LOCALE_NOUSEROVERRIDE użyć systemu domyślne ustawienia regionalne, zamiast niestandardowych ustawień użytkownika.

- Ignoruj VAR_TIMEVALUEONLY część dotycząca daty podczas analizowania.

- Ignoruj VAR_DATEVALUEONLY część godzinowa podczas analizowania.

*lcid*<br/>
Określa identyfikator ustawień regionalnych na potrzeby konwersji. Aby uzyskać więcej informacji na temat identyfikatorów języka, zobacz [identyfikatorów języka](/windows/desktop/Intl/language-identifiers).

*lpszFormat*<br/>
Formatowanie ciągów podobne do `printf` ciąg formatowania. Każdy formatowanie kodu, poprzedzony procent ( `%`) Zaloguj się, jest zastępowany przez odpowiednie `COleDateTime` składnika. Inne znaki do ciągu formatowania są kopiowane bez zmian do zwracanego ciągu. Zobacz opis funkcji wykonawczej [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać więcej informacji. Wartość i znaczenie kody formatowania `Format` są:

- `%H` Godz. w bieżącym dniu

- `%M` Minuty w bieżącej godziny

- `%S` Liczba sekund w ciągu bieżącej minuty

- `%%` Znak procentu

*nFormatID*<br/>
Identyfikator zasobu ciąg formantu formatu.

### <a name="return-value"></a>Wartość zwracana

Element `CString` zawierający wartości daty/godziny sformatowane.

### <a name="remarks"></a>Uwagi

Jeśli stan to `COleDateTime` obiekt ma wartość null, wartość zwracana jest ciągiem pustym. Jeśli stan jest nieprawidłowa, zwracanego ciągu jest określany przez zasób ciągu ATL_IDS_DATETIME_INVALID.

Krótki opis trzy formy dla tej funkcji są następujące:

`Format`( *Flagidw*, *lcid*)<br/>
Ten formularz, formatuje wartość przy użyciu specyfikacji języka (identyfikatory ustawień regionalnych) dla daty i godziny. Przy użyciu parametrów domyślnych, ten formularz drukują datę i godzinę, o ile część godzinowa to 0 (północ), w którym to przypadku składała się tylko datę lub część dotycząca daty jest 0 (30 grudnia 1899), w takiej sytuacji zostanie wydrukowany tylko czas. Jeśli wartości daty/godziny to 0 (30 grudnia 1899, północy), ten formularz z parametrami domyślnymi będą drukowane północy.

`Format`( *lpszFormat*)<br/>
Ten formularz, formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest przekazywany jako parametr do funkcji. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w odwołaniu biblioteki wykonawczej.

`Format`( *nFormatID*)<br/>
Ten formularz, formatuje wartość przy użyciu ciągu formatu, który zawiera specjalne kody formatowania, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest zasobem. Identyfikator zasobu ciągu jest przekazywany jako parametr. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w *odwołanie do biblioteki wykonawczej*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` obiektu jako `DBTIMESTAMP` strukturę danych.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*znacznika dbts*<br/>
Odwołanie do [Odcisk czasowy](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zapisuje wynikowy czas w występujących w odwołaniu *znacznika dbts* struktury. `DBTIMESTAMP` Struktury danych, które inicjowane przez tę funkcję będzie miał jego `fraction` element członkowski należy ustawić na zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` obiektu jako `SYSTEMTIME` strukturę danych.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*systime —*<br/>
Odwołanie do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury, aby otrzymać wartość przekonwertowanego daty/godziny z `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli to się powiedzie; Wartość FALSE, jeśli konwersja nie powiedzie się lub jeśli `COleDateTime` obiektu ma wartość NULL lub nieprawidłowa.

### <a name="remarks"></a>Uwagi

`GetAsSystemTime` zapisuje wynikowy czas w występujących w odwołaniu *systime —* obiektu. `SYSTEMTIME` Struktury danych, które inicjowane przez tę funkcję będzie miał jego `wMilliseconds` element członkowski należy ustawić na zero.

Zobacz [GetStatus](#getstatus) dla więcej informacji na temat informacje o stanie przechowywanych w `COleDateTime` obiektu.

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

Wywołaj tę metodę w celu uzyskania czas w `COleDateTime` obiektu jako `UDATE` strukturę danych.

```
bool GetAsUDATE(UDATE& udate) const throw();
```

### <a name="parameters"></a>Parametry

*udate*<br/>
Odwołanie do `UDATE` struktury, aby otrzymać wartość przekonwertowanego daty/godziny z `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli to się powiedzie; Wartość FALSE, jeśli konwersja nie powiedzie się lub jeśli `COleDateTime` obiektu ma wartość NULL lub nieprawidłowa.

### <a name="remarks"></a>Uwagi

A `UDATE` struktury reprezentuje datę "nierozpakowane".

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

Wywołaj tę funkcję statycznego elementu członkowskiego w celu zwrócenia wartości bieżącej daty/godziny.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

Pobiera dzień miesiąca, reprezentowane przez tę wartość daty/godziny.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień miesiąca, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać dnia.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracanej zakres od 1 do 31.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

Pobiera dzień miesiąca, reprezentowane przez tę wartość daty/godziny.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień tygodnia, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać dzień tygodnia.

### <a name="remarks"></a>Uwagi

Nieprawidłowy zwracany wartości zakresu od 1 do 7, gdzie 1 = niedziela, 2 = poniedziałek i tak dalej.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

Pobiera dzień roku, reprezentowane przez tę wartość daty/godziny.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dzień roku, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać dzień roku.

### <a name="remarks"></a>Uwagi

Nieprawidłowy zwracany wartości z zakresu od 1 do 366, gdzie 1 stycznia = 1.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

Pobiera godzinę, reprezentowane przez tę wartość daty/godziny.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Godzina reprezentowana przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać pełnej godzinie.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracanej zakres od 0 do 23.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

Pobiera minutę, reprezentowane przez tę wartość daty/godziny.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Minuty reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać liczby minut.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracanej zakres od 0 do 59.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [GetHour](#gethour).

##  <a name="getmonth"></a>  COleDateTime::GetMonth

Pobiera miesiąca, reprezentowane przez tę wartość daty/godziny.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Miesiąc, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać miesiąca.

### <a name="remarks"></a>Uwagi

Nieprawidłowy zwracany wartości z zakresu od 1 do 12.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [GetDay](#getday).

##  <a name="getsecond"></a>  COleDateTime::GetSecond

Pobiera drugi, reprezentowane przez tę wartość daty/godziny.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Drugi reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli drugi jest niemożliwe.

### <a name="remarks"></a>Uwagi

Prawidłowe wartości zwracanej zakres od 0 do 59.

> [!NOTE]
>  `COleDateTime` Klasa nie obsługuje przestępnym sekund.

Aby uzyskać więcej informacji na temat wdrażania `COleDateTime`, zapoznaj się z artykułem [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Przykład

Zobacz przykład [GetHour](#gethour).

##  <a name="getstatus"></a>  COleDateTime::GetStatus

Pobiera stan (ważność) danego `COleDateTime` obiektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca stan to `COleDateTime` wartość. Jeśli wywołasz `GetStatus` na `COleDateTime` obiekt jest konstruowany przy użyciu domyślnego, to zostanie zwrócona nieprawidłowa. Jeśli wywołasz `GetStatus` na `COleDateTime` obiekt został zainicjowany z konstruktora o wartości null, `GetStatus` będzie zwracać wartość null. Zobacz **uwagi** Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Wartość zwracana jest definiowany przez `DateTimeStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleDateTime` klasy.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Aby uzyskać krótki opis tych wartości stanu przejrzyj następującą listę:

- `COleDateTime::error` Wskazuje, że wystąpił błąd podczas próby uzyskania część wartości daty/godziny.

- `COleDateTime::valid` Wskazuje, że `COleDateTime` obiekt jest prawidłowy.

- `COleDateTime::invalid` Wskazuje, że `COleDateTime` obiektu jest nieprawidłowy; oznacza to, że jego wartość może być nieprawidłowa.

- `COleDateTime::null` Wskazuje, że `COleDateTime` obiekt ma wartość null, oznacza to, że wartość nie została podana dla tego obiektu. (To jest "null" w sensie bazy danych o"Brak wartości" w przeciwieństwie do języka C++ o wartości NULL).

Stan `COleDateTime` obiekt jest nieprawidłowy w następujących przypadkach:

- Jeśli wartość zostanie ustawiona z `VARIANT` lub `COleVariant` wartość, która nie może być konwertowana na wartość daty/godziny.

- Jeśli wartość zostanie ustawiona z `time_t`, `SYSTEMTIME`, lub `FILETIME` wartość, która nie można przekonwertować na wartość prawidłowe daty/godziny.

- Jeśli wartość zostanie ustawiona `SetDateTime` przy użyciu wartości parametru.

- Ten obiekt ma spowodować przepełnienie lub niedopełnienie podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.

- Jeśli wartość jest nieprawidłowa został przypisany do tego obiektu.

- Jeśli stan tego obiektu jawnie ustawiono nieprawidłowy przy użyciu `SetStatus`.

Aby uzyskać więcej informacji na temat operacji, które mogą ustawić stan nieprawidłowy, zobacz następujące funkcje elementów członkowskich:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +, -](#operator_add_-)

- [operator +=-=](#operator_add_eq_-_eq)

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

Pobiera roku, reprezentowane przez tę wartość daty/godziny.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Rok, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli nie można uzyskać roku.

### <a name="remarks"></a>Uwagi

Nieprawidłowy zwracany wartości z zakresu od 100 do 9999 zawierającą wieku.

Instrukcje dotyczące innych funkcji Członkowskich, które tworzą zapytania dotyczące wartość tego `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [GetDay](#getday).

##  <a name="m_dt"></a>  COleDateTime::m_dt

Podstawowe `DATE` struktury, w tym `COleDateTime` obiektu.

```
DATE m_dt;
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
>  Zmiana wartości w `DATE` obiektu uzyskiwał dostęp do wskaźnika zwrócona przez tę funkcję zmieni wartość tego `COleDateTime` obiektu. Nie zmienia się jego stan to `COleDateTime` obiektu.

Aby uzyskać więcej informacji o implementacji `DATE` obiektu, zapoznaj się z artykułem [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="m_status"></a>  COleDateTime::m_status

Zawiera informacje o stanie tego `COleDateTime` obiektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Uwagi

Typ ten element członkowski danych jest Typ wyliczany `DateTimeStatus`, który jest zdefiniowany w obrębie `COleDateTime` klasy. Zobacz [COleDateTime::GetStatus](#getstatus) Aby uzyskać szczegółowe informacje.

> [!CAUTION]
>  Ten element członkowski danych dotyczy zaawansowane sytuacjach programistycznych. Skorzystaj z wbudowanych funkcji elementów członkowskich [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszych ostrzeżenia dotyczące jawne ustawienie ten element członkowski danych.

##  <a name="operator_eq"></a>  COleDateTime::operator =

Kopiuje `COleDateTime` wartość.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory przeciążone przypisania kopiowania wartości daty/godziny źródła do tego `COleDateTime` obiektu. Krótki opis każdego z tych przeciążone operatory przypisania w następujący sposób:

- **Operator = (** `dateSrc` **)** wartości i stanu operand są kopiowane do tego `COleDateTime` obiektu.

- **Operator = (** *varSrc* **)** Jeśli konwersja [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) wartość (lub [COleVariant](../../mfc/reference/colevariant-class.md) obiektu) do daty/godziny (VT_ Data) zakończy się pomyślnie, przekonwertowana wartości zostanie skopiowany do tego `COleDateTime` obiekt i jego stan jest ustawiony na prawidłowy. Jeśli konwersja się nie powiedzie, wartość tego obiektu jest równa zero (30 grudnia 1899, północ) i jej stanie się nieprawidłowy.

- **Operator = (** `dtSrc` **)** `DATE` jest kopiowana do to `COleDateTime` obiekt i jego stan jest ustawiony na prawidłowy.

- **Operator = (** `timeSrc` **)** `time_t` lub `__time64_t` wartość jest konwertowany i skopiowany do tego `COleDateTime` obiektu. Jeśli konwersja się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; Jeśli nie powiedzie, zostanie ustawiona na nieprawidłową.

- **Operator = (** *systimeSrc* **)** [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) wartość jest konwertowany i skopiowany do tego `COleDateTime` obiektu. Jeśli konwersja się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; Jeśli nie powiedzie, zostanie ustawiona na nieprawidłową.

- **Operator = (** `udate` **)** `UDATE` wartość jest konwertowany i skopiowany do tego `COleDateTime` obiektu. Jeśli konwersja się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; Jeśli nie powiedzie, zostanie ustawiona na nieprawidłową. A `UDATE` struktury reprezentuje datę "nierozpakowane". Zobacz opis funkcji [VarDateFromUdate](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate) Aby uzyskać więcej informacji.

- **Operator = (** `filetimeSrc` **)** [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) wartość jest konwertowany i skopiowany do tego `COleDateTime` obiektu. Jeśli konwersja się pomyślnie, stan tego obiektu jest ustawiony na prawidłowy; w przeciwnym razie jest ustawiona na nieprawidłową. `FILETIME` używa skoordynowany czas uniwersalny (UTC), jeśli przekażesz czasu UTC w strukturze wyniki zostanie przekonwertowana z czasu UTC na czas lokalny i będą przechowywane jako wariant czasu. To zachowanie jest takie same jak Visual C++ 6.0 i Visual C++ .NET 2003 z dodatkiem SP2. Zobacz [czasy](/windows/desktop/SysInfo/file-times) w zestawie Windows SDK, aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) wejścia w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat `time_t` typ danych, zobacz [czasu](../../c-runtime-library/reference/time-time32-time64.md) działa w programach *odwołanie do biblioteki wykonawczej*.

Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) struktur w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_add_-"></a>  COleDateTime::operator +, -

Dodawanie i odejmowanie `ColeDateTime` wartości.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Uwagi

`COleDateTime` obiekty reprezentują godziny bezwzględne. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) obiekty reprezentują godziny względne. Pierwsze dwa operatory pozwalają na dodawanie i odejmowanie `COleDateTimeSpan` wartość z `COleDateTime` wartości. Trzeci operator pozwala na potrzeby odejmowania jeden `COleDateTime` wartości z innej umożliwiające uzyskanie `COleDateTimeSpan` wartość.

Jeśli jeden z operandów jest null, stan wynikowy `COleDateTime` ma wartość null.

Jeśli wynikowe `COleDateTime` wartość znajduje się poza zakresem wartości dozwolonych, stan, który `COleDateTime` wartość jest nieprawidłowa.

Jeśli jeden z operandów jest nieprawidłowa, a druga nie ma wartość null, stan wynikowy `COleDateTime` wartość jest nieprawidłowa.

**+** i **-** operatory będzie potwierdzenia, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [operatory relacyjne COleDateTime](#coledatetime_relational_operators) przykład.

Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator +=-=

Dodawanie i odejmowanie `ColeDateTime` wartości z tego `COleDateTime` obiektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Uwagi

Te operatory pozwalają na dodawanie i odejmowanie `COleDateTimeSpan` wartości do i z tego `COleDateTime`. Jeśli jeden z operandów jest null, stan wynikowy `COleDateTime` ma wartość null.

Jeśli wynikowy `COleDateTime` wartość znajduje się poza zakresem wartości dozwolonych, stan tego `COleDateTime` wartość jest ustawiana na nieprawidłowy.

Jeśli jeden z operandów jest nieprawidłowa, a inne nie ma wartość null, stan wynikowy `COleDateTime` wartość jest nieprawidłowa.

Aby uzyskać więcej informacji na podstawie wartości w stan prawidłowy, nieprawidłowy i wartość null, zobacz [m_status](#m_status) zmiennej składowej.

**+=** i **-=** operatory będzie potwierdzenia, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [operatory relacyjne COleDateTime](#coledatetime_relational_operators) przykład.

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_date"></a>  COleDateTime::operator daty

Konwertuje `ColeDateTime` wartością do `DATE`.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Uwagi

Ten operator zwraca `DATE` obiektu, którego wartość jest kopiowany z tym `COleDateTime` obiektu. Aby uzyskać więcej informacji o implementacji `DATE` obiektu, zapoznaj się z artykułem [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

`DATE` Operator będzie potwierdzenia, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [operatory relacyjne COleDateTime](#coledatetime_relational_operators) przykład.

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

Analizuje ciąg, który ma zostać odczytana wartość daty/godziny.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*lpszDate*<br/>
Wskaźnik na ciąg zakończony znakiem null, które ma być analizowana. Aby uzyskać więcej informacji zobacz uwagi.

*Flagidw*<br/>
Określa flagi dla ustawień regionalnych i analizowanie. Co najmniej jedną z następujących flag:

- LOCALE_NOUSEROVERRIDE używane domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.

- Ignoruj VAR_TIMEVALUEONLY część dotycząca daty podczas analizowania.

- Ignoruj VAR_DATEVALUEONLY część godzinowa podczas analizowania.

*lcid*<br/>
Określa identyfikator ustawień regionalnych na potrzeby konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ciąg został pomyślnie przekonwertowany na wartość daty/godziny, w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli ten ciąg został pomyślnie przekonwertowany daty/godziny wartość, wartość to `COleDateTime` obiekt jest ustawiony na tę wartość i jego stan prawidłowy.

> [!NOTE]
>  Wartości roku musi znajdować się od 100 do 9999 (włącznie).

*LpszDate* parametr może przybierać różne formaty. Na przykład następujące ciągi zawierają formaty dopuszczalne daty/godziny:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

Pamiętaj, że identyfikator ustawień regionalnych wpłynie również na to, czy format ciągu jest możliwa do konwersji na wartość daty/godziny.

W przypadku VAR_DATEVALUEONLY wartość czasu jest równa czasu 0 lub północy. W przypadku VAR_TIMEVALUEONLY Data 0, co oznacza 30 grudnia 1899 ustawiono wartość daty.

Jeśli nie można przekonwertować ciągu na wartość daty/godziny lub, jeśli wystąpiło przepełnienie liczbowe, stan tego `COleDateTime` obiekt jest nieprawidłowy.

Aby uzyskać więcej informacji na temat granice i implementację `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="setdate"></a>  COleDateTime::SetDate

Ustawia datę to `COleDateTime` obiektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nYear*, *nMonth*, *nbłędny dzień*<br/>
Wskazać składniki daty, który ma być skopiowany do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość to `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie wartość 1. Ta wartość zwracana, opiera się na `DateTimeStatus` Typ wyliczany. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Data jest równa określonej wartości. Godzina jest ustawiana na czas 0, o północy.

Zobacz w tabeli poniżej granic o wprowadzenie wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nbłędny dzień*|0 - 31|

Jeśli zachodzi dzień miesiąca, jest konwertowany na poprawne dnia następnego miesiąca i miesiąca i/lub rok jest zwiększany, odpowiednio. Dzień wartość zero wskazuje ostatni dzień poprzedniego miesiąca. To zachowanie jest taka sama jak `SystemTimeToVariantTime`.

Jeśli wartość daty, określona przez parametry nie jest prawidłowy, stan tego obiektu jest ustawiony na `COleDateTime::invalid`. Należy używać [GetStatus](#getstatus) do sprawdzania poprawności `DATE` wartości i nie należy zakładać, że wartość [m_dt](#m_dt) nie zostaną zmodyfikowane.

Poniżej przedstawiono kilka przykładów wartości dat:

|*nYear*|*nMonth*|*nbłędny dzień*|Wartość|
|-------------|--------------|------------|-----------|
|2000|2|29|29 lutego 2000|
|1776|7|4|4 lipca 1776|
|1925|4|35|35 1925 kwietnia (Nieprawidłowa data)|
|10000|1|1|1 stycznia 10000 (Nieprawidłowa data)|

Aby ustawić daty i godziny, zobacz [COleDateTime::SetDateTime](#setdatetime).

Informacje na temat funkcji elementu członkowskiego, które wartość tego zapytania `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

Ustawia datę i godzinę, to `COleDateTime` obiektu.

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

*nYear*, *nMonth*, *nbłędny dzień*, *Ngodzina*, *nMin*, *nSec*<br/>
Wskazać składniki daty i godziny do skopiowania do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość to `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie wartość 1. Ta wartość zwracana, opiera się na `DateTimeStatus` Typ wyliczany. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Zobacz w tabeli poniżej granic o wprowadzenie wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nbłędny dzień*|0 - 31|
|*Ngodzina*|0 - 23|
|*Nmin.*|0 - 59|
|*rekordy nSec*|0 - 59|

Jeśli zachodzi dzień miesiąca, jest konwertowany na poprawne dnia następnego miesiąca i miesiąca i/lub rok jest zwiększany, odpowiednio. Dzień wartość zero wskazuje ostatni dzień poprzedniego miesiąca. To zachowanie jest taka sama jak [SystemTimeToVariantTime](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime).

Jeśli wartość daty lub godziny, określona przez parametry nie jest prawidłowy, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu jest zmieniany.

Poniżej przedstawiono kilka przykładów wartości czasu:

|*Ngodzina*|*Nmin.*|*rekordy nSec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Poniżej przedstawiono kilka przykładów wartości dat:

|*nYear*|*nMonth*|*nbłędny dzień*|Wartość|
|-------------|--------------|------------|-----------|
|1995|4|15|15 kwietnia 1995 r.|
|1789|7|14|17 lipca 1789|
|1925|2|30|Nieprawidłowy|
|10000|1|1|Nieprawidłowy|

Aby ustawić tylko data, zobacz [COleDateTime::SetDate](#setdate). Aby ustawić tylko raz, zobacz [COleDateTime::SetTime](#settime).

Informacje na temat funkcji elementu członkowskiego, które wartość tego zapytania `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [GetStatus](#getstatus).

##  <a name="setstatus"></a>  COleDateTime::SetStatus

Ustawia stan tego `COleDateTime` obiektu.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*status*<br/>
Nowa wartość stanu w tym `COleDateTime` obiektu.

### <a name="remarks"></a>Uwagi

*Stan* wartość parametru jest definiowana przez `DateTimeStatus` wyliczany typ, który jest zdefiniowany w obrębie `COleDateTime` klasy. Zobacz [COleDateTime::GetStatus](#getstatus) Aby uzyskać szczegółowe informacje.

> [!CAUTION]
>  Ta funkcja jest zaawansowane sytuacjach programistycznych. Ta funkcja nie zmienia danych w tym obiekcie. W większości przypadków posłuży do ustawiania stanu **null** lub **nieprawidłowy**. Należy pamiętać, że operator przypisania ( [operator =](#eq)) i [SetDateTime](#setdatetime) ustawić stan obiektu, w oparciu o wartości źródła.

### <a name="example"></a>Przykład

Zobacz przykład [GetStatus](#getstatus).

##  <a name="settime"></a>  COleDateTime::SetTime

Ustawia czas tego `COleDateTime` obiektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*Ngodzina*, *nMin*, *nSec*<br/>
Wskazać składniki czasu, który ma być skopiowany do tego `COleDateTime` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli wartość to `COleDateTime` obiektu została ustawiona pomyślnie; w przeciwnym razie wartość 1. Ta wartość zwracana, opiera się na `DateTimeStatus` Typ wyliczany. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Czas jest równa określonej wartości. Data jest ustawiona na Data 0, co oznacza 30 grudnia 1899.

Zobacz w tabeli poniżej granic o wprowadzenie wartości parametrów:

|Parametr|Granice|
|---------------|------------|
|*Ngodzina*|0 - 23|
|*Nmin.*|0 - 59|
|*rekordy nSec*|0 - 59|

Jeśli wartość określoną przez parametry nie jest prawidłowy, czas stanu tego obiektu jest równa invalid i wartość tego obiektu nie jest zmieniany.

Poniżej przedstawiono kilka przykładów wartości czasu:

|*Ngodzina*|*Nmin.*|*rekordy nSec*|Wartość|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Nieprawidłowy|
|9|60|0|Nieprawidłowy|

Aby ustawić daty i godziny, zobacz [COleDateTime::SetDateTime](#setdatetime).

Informacje na temat funkcji elementu członkowskiego, które wartość tego zapytania `COleDateTime` obiektu, zobacz następujące funkcje elementów członkowskich:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [Elementu GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Aby uzyskać więcej informacji na temat granice dla `COleDateTime` wartości, zobacz artykuł [Data i godzina: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Przykład

Zobacz przykład [SetDate](#setdate).

## <a name="see-also"></a>Zobacz też

[Klasa COleVariant](../../mfc/reference/colevariant-class.md)<br/>
[CTime, klasa](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan, klasa](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

