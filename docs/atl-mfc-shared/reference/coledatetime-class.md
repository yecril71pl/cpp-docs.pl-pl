---
title: Klasa COleDateTime | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbe0e831a644dfc09c6b4afb3c54f23b220850d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledatetime-class"></a>Klasa COleDateTime
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
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Wywołanie tej metody można uzyskać czasu w `COleDateTime` obiekt jako **odcisk CZASOWY** struktury danych.|  
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Wywołanie tej metody można uzyskać czasu w `COleDateTime` obiekt jako [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury danych.|  
|[COleDateTime::GetAsUDATE](#getasudate)|Wywołanie tej metody można uzyskać czasu w `COleDateTime` jako **UDATE** struktury danych.|  
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Tworzy `COleDateTime` obiekt, który reprezentuje bieżący czas (statycznej funkcji członkowskiej).|  
|[COleDateTime::GetDay](#getday)|Zwraca dzień to `COleDateTime` obiekt reprezentuje (1-31).|  
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Zwraca dzień tygodnia, to `COleDateTime` obiekt reprezentuje (niedziela = 1).|  
|[COleDateTime::GetDayOfYear](#getdayofyear)|Zwraca dzień roku, to `COleDateTime` obiekt reprezentuje (1 stycznia = 1).|  
|[COleDateTime::GetHour](#gethour)|Zwraca godzinę, to `COleDateTime` obiekt reprezentuje (0 - 23).|  
|[COleDateTime::GetMinute](#getminute)|Zwraca minutę, to `COleDateTime` obiekt reprezentuje (0 - 59).|  
|[COleDateTime::GetMonth](#getmonth)|Zwraca miesiąc, to `COleDateTime` obiekt reprezentuje (1-12).|  
|[COleDateTime::GetSecond](#getsecond)|Zwraca sekundę to `COleDateTime` obiekt reprezentuje (0 - 59).|  
|[COleDateTime::GetStatus](#getstatus)|Pobiera stan (ważności) to `COleDateTime` obiektu.|  
|[COleDateTime::GetYear](#getyear)|Zwraca rok, to `COleDateTime` reprezentuje obiekt.|  
|[COleDateTime::ParseDateTime](#parsedatetime)|Odczytuje wartości daty/godziny z ciągu i ustawia wartość `COleDateTime`.|  
|[COleDateTime::SetDate](#setdate)|Ustawia wartość to `COleDateTime` obiekt z podaną wartością tylko do daty.|  
|[COleDateTime::SetDateTime](#setdatetime)|Ustawia wartość to `COleDateTime` obiektu do wartości określonej daty/godziny.|  
|[COleDateTime::SetStatus](#setstatus)|Ustawia stan (ważności) to `COleDateTime` obiektu.|  
|[COleDateTime::SetTime](#settime)|Ustawia wartość to `COleDateTime` obiekt z podaną wartością tylko od czasu.|  
  
### <a name="public-operators"></a>Operatory publiczne  

|Nazwa|Opis|  
|----------|-----------------|  
|[COleDateTime::operator == COleDateTime::operator < itp.](#coledatetime_relational_operators)|Porównać dwa `COleDateTime` wartości.|  
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|Dodawanie i usuwanie `COleDateTime` wartości.|  
|[+= COleDateTime::operator, COleDateTime::operator-=](#operator_add_eq_-_eq)|Dodawanie i usuwanie `COleDateTime` wartości z tej `COleDateTime` obiektu.|  
|[COleDateTime::operator =](#operator_eq)|Kopie `COleDateTime` wartość.|  
|[Data, COleDateTime::operator COleDateTime::operator Data *](#operator_date)|Konwertuje `COleDateTime` wartości do `DATE` lub `DATE*`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDateTime::m_dt](#m_dt)|Zawiera podstawową **data** dla tego `COleDateTime` obiektu.|  
|[COleDateTime::m_status](#m_status)|Zawiera informacje o stanie tego `COleDateTime` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDateTime`nie ma klasy podstawowej.  
  
 Jest to jeden z typów możliwych do [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) typu danych automatyzacji OLE. A `COleDateTime` reprezentuje wartość bezwzględna wartość daty i godziny.  
  
 `DATE` Typu jest zaimplementowany jako wartość zmiennoprzecinkową. Liczba dni są mierzone od 30 grudnia 1899 o północy. W poniższej tabeli przedstawiono niektóre daty oraz powiązanych wartości:  
  
|Data|Wartość|  
|----------|-----------|  
|29 grudnia 1899 północy|-1.0|  
|29 grudnia 1899, przedpołudnie 6|-1.25|  
|30 grudnia 1899 północy|0.0|  
|31 grudnia 1899 północy|1.0|  
|1 stycznia 1900, godziny 6: 00|2.25|  
  
> [!CAUTION]
>  W powyższej tabeli Pamiętaj, że chociaż ujemna wartości dni przed północy 30 grudnia 1899 wartości czasu dnia nie. Na przykład 6:00:00 zawsze jest reprezentowany przez wartość ułamkową 0,25 niezależnie od tego, czy liczbę całkowitą przedstawiającą dzień (po 30 grudnia 1899) dodatnią lub ujemną (przed 30 grudnia 1899). Oznacza to, że błędnie posortuj proste przestawne porównanie punktu `COleDateTime` reprezentujący 6:00 AM 12/29/1899 **później** niż jeden reprezentujący 7:00:00 w dniu.  
  
 `COleDateTime` Klasa obsługuje dat od 1 stycznia 100 r. do 31 grudnia 9999 r. `COleDateTime` Klasa korzysta z kalendarza gregoriańskiego; nie obsługuje dat juliański. `COleDateTime`ignoruje czasu letniego. (Zobacz [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).)  
  
> [!NOTE]
>  Można użyć `%y` format można pobrać dwucyfrowe tylko dla dat, zaczynając od 1900 roku. Jeśli używasz `%y` format dnia przed 1900 kod generuje błąd potwierdzenia.  
  
 Ten typ jest również używana do reprezentowania wartości daty lub tylko od czasu. Konwencja Data 0 (30 grudnia 1899) jest używany dla wartości tylko od czasu i godziny 00:00 (północ) jest używany dla wartości daty.  
  
 W przypadku utworzenia `COleDateTime` obiektu za pomocą datę mniej niż 100 Data jest akceptowane, ale kolejne wywołania `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, i `GetSecond` zakończyć się niepowodzeniem i zwróć -1. Wcześniej można użyć dwóch cyfr daty, ale daty muszą być 100 lub większym w MFC 4.2 lub nowszy.  
  
 Aby uniknąć problemów, należy określić datę czterech cyfr. Na przykład:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]  
  
 Podstawowe operacje arytmetyczne na `COleDateTime` wartości należy użyć klasy Pomocnika [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`wartości definiują przedział czasu. Relacja między tych klas jest podobny do przedstawionego między [ctime —](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Aby uzyskać więcej informacji na temat `COleDateTime` i `COleDateTimeSpan` klas, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ATLComTime.h  
  
##  <a name="coledatetime_relational_operators"></a>Operatory relacyjne COleDateTime  
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
 `date`  
 **COleDateTime** obiekt do porównania.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  ATLASSERT wystąpi, jeśli jeden z dwóch argumentów operacji jest nieprawidłowy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]  
  
### <a name="example"></a>Przykład  
 Operatory  **>=** ,  **\< =** ,  **>** , i  **<** , zostanie assert, jeśli `COleDateTime` obiekt jest ustawiony na wartość null.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]  
  
##  <a name="coledatetime"></a>COleDateTime::COleDateTime  
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
 `dateSrc`  
 Istniejące `COleDateTime` obiekt ma zostać skopiowany do nowego `COleDateTime` obiektu.  
  
 *varSrc*  
 Istniejące **VARIANT** struktury danych (prawdopodobnie `COleVariant` obiektu) są konwertowane na wartość daty/godziny ( `VT_DATE`) i skopiowane do nowego `COleDateTime` obiektu.  
  
 `dtSrc`  
 Data/Godzina ( **data**) wartość ma zostać skopiowany do nowego `COleDateTime` obiektu.  
  
 `timeSrc`  
 A `time_t` lub **__time64_t —** wartość przekonwertowana na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.  
  
 *systimeSrc*  
 A `SYSTEMTIME` struktury można przekonwertować na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu.  
  
 `filetimeSrc`  
 A `FILETIME` struktury można przekonwertować na wartość daty/godziny i skopiowane do nowego `COleDateTime` obiektu. Należy pamiętać, że `FILETIME` używany uniwersalny czas koordynowany (UTC), więc jeśli przekazujesz czasu lokalnego w strukturze będą niepoprawne wyniki. Zobacz [czasy plików](http://msdn.microsoft.com/library/windows/desktop/ms724290) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Wskazuje datę i godzinę wartości ma zostać skopiowany do nowego `COleDateTime` obiektu.  
  
 `wDosDate`, `wDosTime`  
 Wartości daty i godziny można przekonwertować na wartość daty/godziny i skopiowane do nowego systemu MS-DOS `COleDateTime` obiektu.  
  
 `dbts`  
 Odwołanie do [Odcisk czasowy](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury zawierającej bieżącym czasem lokalnym.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów tworzenia nowych `COleDateTime` obiektów zainicjowany z podaną wartością. W poniższej tabeli przedstawiono prawidłowych zakresów dla poszczególnych składników daty i godziny:  
  
|Składnik daty/godziny|Prawidłowy zakres|  
|--------------------------|-----------------|  
|Roku|100 - 9999|  
|Miesiąc|0 - 12|  
|dzień|0 - 31|  
|Godzina|0 - 23|  
|Minuta|0 - 59|  
|Drugie|0 - 59|  
  
 Należy pamiętać, że zmienia się rzeczywista górna granica składnika dzień oparte na składnikach miesiącu i roku. Aby uzyskać więcej informacji, zobacz **SetDate** lub `SetDateTime` funkcji elementów członkowskich.  
  
 Poniżej znajduje się krótki opis każdego konstruktora:  
  
- `COleDateTime(`**)** Tworzy `COleDateTime` obiektu równe 0 (30 grudnia 1899 północ).  
  
- `COleDateTime(``dateSrc` **)** Tworzy `COleDateTime` obiektu z istniejącego `COleDateTime` obiektu.  
  
- `COleDateTime(`*varSrc* **)** tworzy `COleDateTime` obiektu. Próbuje przekonwertować `VARIANT` struktury lub [COleVariant](../../mfc/reference/colevariant-class.md) obiekt do daty/godziny ( `VT_DATE`) wartość. Jeśli ta konwersja zakończy się pomyślnie, skonwertowana wartość jest kopiowana do nowej `COleDateTime` obiektu. Jeśli nie, to wartość `COleDateTime` obiektu ma wartość 0 (30 grudnia 1899 północ) i jego stan na nieprawidłowy.  
  
- `COleDateTime(``dtSrc` **)** Tworzy `COleDateTime` obiekt z **data** wartość.  
  
- `COleDateTime(``timeSrc` **)** Tworzy `COleDateTime` obiekt z `time_t` wartości.  
  
- `COleDateTime(`*systimeSrc* **)** tworzy `COleDateTime` obiekt z `SYSTEMTIME` wartości.  
  
- `COleDateTime(``filetimeSrc` **)** Tworzy `COleDateTime` obiekt z `FILETIME` wartości. . Należy pamiętać, że `FILETIME` używany uniwersalny czas koordynowany (UTC), więc jeśli przekazujesz czasu lokalnego w strukturze będą niepoprawne wyniki. Zobacz [czasy plików](http://msdn.microsoft.com/library/windows/desktop/ms724290) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
- `COleDateTime(``nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Tworzy `COleDateTime` obiektu z określonej wartości liczbowe.  
  
- `COleDateTime(``wDosDate`, `wDosTime` **)** Tworzy `COleDateTime` obiektu z określonej wartości daty i godziny systemu MS-DOS.  
  
 Aby uzyskać więcej informacji na temat `time_t` typ danych, zobacz [czasu](../../c-runtime-library/reference/time-time32-time64.md) działać w *odwołanie do biblioteki wykonawczej*.  
  
 Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
> [!NOTE]
>  Za pomocą konstruktora **odcisk CZASOWY** parametru jest dostępna tylko, gdy OLEDB.h jest dołączony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]  
  
##  <a name="format"></a>COleDateTime::Format  
 Tworzy reprezentację sformatowane wartości daty/godziny.  
  
```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Wskazuje jedną z następujących flag ustawień regionalnych:  
  
- `LOCALE_NOUSEROVERRIDE`Użyj systemu domyślne ustawienia regionalne, zamiast niestandardowych ustawień użytkownika.  
  
- `VAR_TIMEVALUEONLY`Ignoruj część daty podczas analizy.  
  
- `VAR_DATEVALUEONLY`Ignoruj części czasu podczas analizy.  
  
 `lcid`  
 Wskazuje identyfikator ustawień regionalnych na potrzeby konwersji. Aby uzyskać więcej informacji na temat identyfikatorów języka, zobacz [identyfikatorów języka](http://msdn.microsoft.com/library/windows/desktop/dd318691).  
  
 `lpszFormat`  
 Formatowanie ciąg podobny do `printf` ciąg formatowania. Każdy formatowania kodu poprzedzone procent ( `%`) Zaloguj się, zostanie zastąpiony przez odpowiednie `COleDateTime` składnika. Zwrócony ciąg jest kopiowana niezmienione innych znaków w ciągu formatowania. Zobacz opis funkcji środowiska wykonawczego [strftime —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać więcej informacji. Wartość i znaczenie formatowania kody `Format` są:  
  
- `%H`Godziny w bieżącym dniu  
  
- `%M`Minut w ciągu bieżącej godziny  
  
- `%S`Sekund w ciągu bieżącej minuty  
  
- `%%`Znak procentu  
  
 `nFormatID`  
 Identyfikator zasobu ciągu formatu formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawierający wartości daty/godziny sformatowane.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli stan to `COleDateTime` obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, zwracany ciąg jest określony przez zasób ciągu `ATL_IDS_DATETIME_INVALID`.  
  
 Krótki opis trzy formularzy dla tej funkcji są następujące:  
  
 `Format`( `dwFlags`, `lcid`)  
 Ten formularz formatuje wartość daty i godziny w przy użyciu specyfikacji języka (identyfikatory ustawień regionalnych). Przy użyciu parametrów domyślnych, ten formularz będzie drukować datę i godzinę, chyba że część czasu jest 0 (północ), w takim przypadku będzie drukować tylko datę lub część daty jest 0 (30 grudnia 1899), w takim przypadku go będzie drukować tylko czasu. Jeśli wartości daty/godziny to 0 (30 grudnia 1899, północ), ten formularz z parametrów domyślnych będzie drukować północy.  
  
 `Format`( `lpszFormat`)  
 Ten formularz formatuje wartość przy użyciu ciągu formatu, który zawiera kody specjalne formatowanie, poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania zostanie przekazany jako parametr do funkcji. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime —, wcsftime —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w odwołaniu biblioteki czasu wykonywania.  
  
 `Format`( `nFormatID`)  
 Ten formularz formatuje wartość przy użyciu ciągu formatu, który zawiera kody specjalne formatowanie, poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest zasobem. Identyfikator zasobu ciągu jest przekazywany jako parametr. Aby uzyskać więcej informacji na temat kodów formatowania, zobacz [strftime —, wcsftime —](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) w *odwołanie do biblioteki wykonawczej*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]  
  
##  <a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP  
 Wywołanie tej metody można uzyskać czasu w `COleDateTime` obiekt jako **odcisk CZASOWY** struktury danych.  
  
```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dbts`  
 Odwołanie do [Odcisk czasowy](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przechowuje wynikowy czas w przywoływana `dbts` struktury. **Odcisk CZASOWY** zainicjowane przez tę funkcję struktura danych będzie mieć jego **ułamek** zestaw elementów członkowskich na zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]  
  
##  <a name="getassystemtime"></a>COleDateTime::GetAsSystemTime  
 Wywołanie tej metody można uzyskać czasu w `COleDateTime` obiekt jako `SYSTEMTIME` struktury danych.  
  
```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *sysTime*  
 Odwołanie do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury wartość przekonwertowanego daty/godziny z `COleDateTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia; **false** czy konwersji nie powiedzie się, czy `COleDateTime` obiekt jest **NULL** lub jest on nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 `GetAsSystemTime`przechowuje wynikowy czas w przywoływana *sysTime* obiektu. `SYSTEMTIME` Zainicjowane przez tę funkcję struktura danych będzie mieć jego **wMilliseconds** zestaw elementów członkowskich na zero.  
  
 Zobacz [GetStatus](#getstatus) dla więcej informacji na temat informacje o stanie przechowywać w formacie `COleDateTime` obiektu.  
  
##  <a name="getasudate"></a>COleDateTime::GetAsUDATE  
 Wywołanie tej metody można uzyskać czasu w `COleDateTime` obiekt jako **UDATE** struktury danych.  
  
```
bool GetAsUDATE(UDATE& udate) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `udate`  
 Odwołanie do **UDATE** struktury wartość przekonwertowanego daty/godziny z `COleDateTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia; **false** czy konwersji nie powiedzie się, czy `COleDateTime` obiekt jest **NULL** lub jest on nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 A **UDATE** struktury reprezentuje datę "rozpakowanego".  
  
##  <a name="getcurrenttime"></a>COleDateTime::GetCurrentTime  
 Wywołanie tej funkcji statyczny element członkowski ma zostać zwrócona wartość bieżącej daty/godziny.  
  
```
static COleDateTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]  
  
##  <a name="getday"></a>COleDateTime::GetDay  
 Pobiera dzień miesiąca reprezentowany przez ten wartości daty/godziny.  
  
```
int GetDay() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dzień miesiąca reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać dnia.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe wartości zwracane zakresu od 1 do 31.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]  
  
##  <a name="getdayofweek"></a>COleDateTime::GetDayOfWeek  
 Pobiera dzień miesiąca reprezentowany przez ten wartości daty/godziny.  
  
```
int GetDayOfWeek() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dzień tygodnia reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać dzień tygodnia.  
  
### <a name="remarks"></a>Uwagi  
 Nieprawidłowy zwracany wartości zakresu od 1 do 7, gdzie 1 = niedziela, 2 = poniedziałek i tak dalej.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]  
  
##  <a name="getdayofyear"></a>COleDateTime::GetDayOfYear  
 Pobiera dzień roku, reprezentowany przez ten wartości daty/godziny.  
  
```
int GetDayOfYear() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dzień roku, reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać dzień roku.  
  
### <a name="remarks"></a>Uwagi  
 Nieprawidłowy zwracany wartości z zakresu od 1 do 366, gdzie 1 stycznia = 1.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]  
  
##  <a name="gethour"></a>COleDateTime::GetHour  
 Pobiera godzinę reprezentowany przez ten wartości daty/godziny.  
  
```
int GetHour() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Godzina reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać godzinę.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe wartości zwracane zakresu od 0 do 23.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]  
  
##  <a name="getminute"></a>COleDateTime::GetMinute  
 Pobiera minutę reprezentowany przez ten wartości daty/godziny.  
  
```
int GetMinute() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minuta reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać minutę.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe wartości zwracane zakresu od 0 do 59.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHour](#gethour).  
  
##  <a name="getmonth"></a>COleDateTime::GetMonth  
 Pobiera miesiąca reprezentowany przez ten wartości daty/godziny.  
  
```
int GetMonth() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Miesiąc reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać miesiąca.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe wartości zwracane zakresu od 1 do 12.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetDay](#getday).  
  
##  <a name="getsecond"></a>COleDateTime::GetSecond  
 Pobiera sekundę reprezentowany przez ten wartości daty/godziny.  
  
```
int GetSecond() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Drugi reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` Jeśli drugi jest niemożliwe.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe wartości zwracane zakresu od 0 do 59.  
  
> [!NOTE]
>  `COleDateTime` Klasa nie obsługuje sekund przestępnym.  
  
 Aby uzyskać więcej informacji na temat wdrażania `COleDateTime`, zapoznaj się z artykułem [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHour](#gethour).  
  
##  <a name="getstatus"></a>COleDateTime::GetStatus  
 Pobiera stan (ważności) danego `COleDateTime` obiektu.  
  
```
DateTimeStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca informacje o stanie tego `COleDateTime` wartość. Jeśli należy wywołać **GetStatus** na `COleDateTime` obiekt skonstruowany przy użyciu domyślnego, będzie zwracać prawidłowy. Jeśli należy wywołać **GetStatus** na `COleDateTime` obiektu zainicjowany z konstruktora ustawioną na wartość null, **GetStatus** zwróci wartość null. Zobacz **uwagi** Aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest definiowana za **DateTimeStatus** wyliczany typ, który jest zdefiniowany w `COleDateTime` klasy.  
  
```  
enum DateTimeStatus  
{  
   error = -1,  
   valid = 0,  
   invalid = 1,    // Invalid date (out of range, etc.)  
   null = 2,       // Literally has no value  
};  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- `COleDateTime::error`Wskazuje, że wystąpił błąd podczas próby uzyskania część wartości daty/godziny.  
  
- **COleDateTime::valid** wskazuje tego `COleDateTime` obiekt jest prawidłowy.  
  
- **COleDateTime::invalid** wskazuje tego `COleDateTime` obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleDateTime::null** wskazuje tego `COleDateTime` obiektu ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
 Stan `COleDateTime` obiektu jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli wartość jest ustawiona z **VARIANT** lub `COleVariant` wartość, która nie można przekonwertować na wartość daty/godziny.  
  
-   Jeśli wartość jest ustawiona z `time_t`, `SYSTEMTIME`, lub `FILETIME` wartość, która nie można przekonwertować na wartość prawidłowe daty/godziny.  
  
-   Jeśli jego wartość jest ustawiana przez `SetDateTime` wartościami nieprawidłowy parametr.  
  
-   Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.  
  
-   Jeśli wartość jest nieprawidłowa została przypisana do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłową przy użyciu `SetStatus`.  
  
 Aby uzyskać więcej informacji na temat operacji, które może ustawić stanu nieprawidłowego, zobacz następujące funkcje Członkowskie:  
  
- [COleDateTime](#coledatetime)  
  
- [SetDateTime](#setdatetime)  
  
- [operator +, -](#operator_add_-)  
  
- [operator +=-=](#operator_add_eq_-_eq)  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]  
  
##  <a name="getyear"></a>COleDateTime::GetYear  
 Pobiera roku reprezentowany przez ten wartości daty/godziny.  
  
```
int GetYear() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rok reprezentowany przez wartość tego `COleDateTime` obiektu lub `COleDateTime::error` , jeśli nie można uzyskać roku.  
  
### <a name="remarks"></a>Uwagi  
 Zakres prawidłowy zwracanych wartości od 100 do 9999, w tym wieku.  
  
 Aby uzyskać informacje o innych funkcji elementów członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetDay](#getday).  
  
##  <a name="m_dt"></a>COleDateTime::m_dt  
 Podstawowa **data** to struktura `COleDateTime` obiektu.  
  
```
DATE m_dt;
```  
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Zmiana wartości w **data** obiekt wskaźnika zwracane przez tę funkcję z niego zmieni wartość tego `COleDateTime` obiektu. Nie zmienia stanu to `COleDateTime` obiektu.  
  
 Aby uzyskać więcej informacji o implementacji **data** obiektów, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="m_status"></a>COleDateTime::m_status  
 Zawiera informacje o stanie tego `COleDateTime` obiektu.  
  
```
DateTimeStatus m_status;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ elementu członkowskiego danych jest typ wyliczeniowy **DateTimeStatus**, który jest zdefiniowany w ramach `COleDateTime` klasy. Zobacz [COleDateTime::GetStatus](#getstatus) szczegółowe informacje.  
  
> [!CAUTION]
>  Ten element członkowski danych jest zaawansowane sytuacjach programowania. Należy używać funkcji Członkowskich wbudowanego [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszego ostrzeżenia dotyczące jawne ustawienie tego elementu członkowskiego danych.  
  
##  <a name="operator_eq"></a>COleDateTime::operator =  
 Kopie `COleDateTime` wartość.  
  
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
  
- **Operator = (** `dateSrc` **)** wartość i stan operandu są kopiowane do tego `COleDateTime` obiektu.  
  
- **Operator = (** *varSrc* **)** Jeśli konwersji [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) wartości (lub [COleVariant](../../mfc/reference/colevariant-class.md) obiektu) do (Data/Godzina `VT_DATE`) to się powiedzie, skonwertowana wartość jest kopiowany do tego `COleDateTime` obiekt i jego stan jest ustawiony na prawidłową. Jeśli konwersja zakończy się niepowodzeniem, ten obiekt jest wartość zero (30 grudnia 1899, północ) i jej stanie się nieprawidłowy.  
  
- **Operator = (** `dtSrc` **)** **data** jest kopiowana do to `COleDateTime` obiekt i jego stan jest ustawiony na prawidłową.  
  
- **Operator = (** `timeSrc` **)** `time_t` lub **__time64_t —** wartość jest konwertowana i skopiowane do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłową; Jeśli nie powiodło się, zostanie ustawiona na nieprawidłowy.  
  
- **Operator = (** *systimeSrc* **)** [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) wartość jest konwertowana i skopiowane do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłową; Jeśli nie powiodło się, zostanie ustawiona na nieprawidłowy.  
  
- **Operator = (** `udate` **)** **UDATE** wartość jest konwertowana i skopiowane do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłową; Jeśli nie powiodło się, zostanie ustawiona na nieprawidłowy. A **UDATE** struktury reprezentuje datę "rozpakowanego". Zobacz opis funkcji [VarDateFromUdate](http://msdn.microsoft.com/en-us/1c924ac5-b896-49e1-9ccf-825ac7a030c8) więcej szczegółów.  
  
- **Operator = (** `filetimeSrc` **)** [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) wartość jest konwertowana i skopiowane do tego `COleDateTime` obiektu. Jeśli konwersja zakończy się pomyślnie, stan tego obiektu jest ustawiony na prawidłową; w przeciwnym razie jest ustawiona na nieprawidłowy. `FILETIME`używa uniwersalnego czasu koordynowanego (UTC), więc jeśli przekazujesz czasu UTC w strukturze wyniki zostanie przekonwertowany od czasu UTC na czas lokalny i będą przechowywane jako wariant czasu. To zachowanie jest takie same jak Visual C++ 6.0 i Visual C++ .NET 2003 z dodatkiem SP2. Zobacz [czasy plików](http://msdn.microsoft.com/library/windows/desktop/ms724290) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) wejścia w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat `time_t` typ danych, zobacz [czasu](../../c-runtime-library/reference/time-time32-time64.md) działać w *odwołanie do biblioteki wykonawczej*.  
  
 Aby uzyskać więcej informacji, zobacz [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) i [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_add_-"></a>COleDateTime::operator +, -  
 Dodawanie i usuwanie **ColeDateTime** wartości.  
  
```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 `COleDateTime`obiekty reprezentują bezwzględną razy. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) obiekty reprezentują czas względny. Pierwsze dwa operatory pozwala na dodawanie i usuwanie `COleDateTimeSpan` wartość z `COleDateTime` wartości. Trzeci operator służy do odejmowania jedną `COleDateTime` wartości z innej umożliwiające uzyskanie `COleDateTimeSpan` wartość.  
  
 Jeśli jest jeden z argumentów, null, stan wynikowy `COleDateTime` ma wartość null.  
  
 Jeśli powstałe w ten sposób `COleDateTime` wartość znajduje się poza zakresem wartości dozwolonych, stan, który `COleDateTime` wartość jest nieprawidłowa.  
  
 Jeśli jeden z argumentów jest nieprawidłowa i nie ma innych wartości null, stan wynikowy `COleDateTime` wartość jest nieprawidłowa.  
  
  **+**  i  **-**  operatory będzie assert, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [COleDateTime — operatory relacyjne](#coledatetime_relational_operators) przykład.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTime::operator +=-=  
 Dodawanie i usuwanie **ColeDateTime** wartości z tej `COleDateTime` obiektu.  
  
```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Operatory te umożliwiają dodawanie i odejmowanie `COleDateTimeSpan` wartość do i z tego `COleDateTime`. Jeśli jest jeden z argumentów, null, stan wynikowy `COleDateTime` ma wartość null.  
  
 Jeśli powstałe w ten sposób `COleDateTime` wartość znajduje się poza zakresem wartości dozwolonych, stan to `COleDateTime` wartość jest ustawiona na nieprawidłowy.  
  
 Jeśli jeden z argumentów jest nieprawidłowa i nie ma innych wartości null, stan wynikowy `COleDateTime` wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
  **+=**  i  **-=**  operatory będzie assert, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [COleDateTime — operatory relacyjne](#coledatetime_relational_operators) przykład.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_date"></a>COleDateTime::operator daty  
 Konwertuje **ColeDateTime** wartości do **data**.  
  
```
operator DATE() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca **data** obiektu, którego wartość jest kopiowana z to `COleDateTime` obiektu. Aby uzyskać więcej informacji o implementacji **data** obiektów, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 **Data** operatora zostanie assert, jeśli `COleDateTime` obiekt jest ustawiony na wartość null. Zobacz [COleDateTime — operatory relacyjne](#coledatetime_relational_operators) przykład.  
  
##  <a name="parsedatetime"></a>COleDateTime::ParseDateTime  
 Analizuje ciąg można odczytać wartości daty/godziny.  
  
```
bool ParseDateTime(  
 LPCTSTR lpszDate,
 DWORD dwFlags = 0,
 LCID lcid = LANG_USER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDate`  
 Wskaźnik do zerem ciągu, który ma zostać przeanalizowany. Aby uzyskać więcej informacji zobacz uwagi.  
  
 `dwFlags`  
 Wskazuje flagi dla ustawień regionalnych i analizowania. Co najmniej jeden z następujących flag:  
  
- **LOCALE_NOUSEROVERRIDE** domyślne ustawienia regionalne systemu, a nie niestandardowych ustawień użytkownika.  
  
- **VAR_TIMEVALUEONLY** zignorować część daty podczas analizy.  
  
- **VAR_DATEVALUEONLY** zignorować część czasu podczas analizy.  
  
 `lcid`  
 Wskazuje identyfikator ustawień regionalnych na potrzeby konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli ciąg został pomyślnie przekonwertowany na wartość daty/godziny, w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ten ciąg został pomyślnie przekonwertowany na daty/godziny wartości, wartość to `COleDateTime` obiektu ma ustawioną tę wartość i jego stan prawidłowy.  
  
> [!NOTE]
>  Rok musi znajdować się od 100 do 9999, włącznie.  
  
 `lpszDate` Parametr można wykonywać różne formaty. Na przykład następujące ciągi zawierać formaty dopuszczalne daty/godziny:  
  
 `"25 January 1996"`  
  
 `"8:30:00"`  
  
 `"20:30:00"`  
  
 `"January 25, 1996 8:30:00"`  
  
 `"8:30:00 Jan. 25, 1996"`  
  
 `"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`  
  
 Należy pamiętać, że identyfikator ustawień regionalnych ma wpływ na czy format ciągu jest możliwa do konwersji wartości daty/godziny.  
  
 W przypadku liczby **VAR_DATEVALUEONLY**, czas jest ustawiona wartość czasu 0 lub północy. W przypadku liczby **VAR_TIMEVALUEONLY**, data ma wartość Data 0, co oznacza 30 grudnia 1899.  
  
 Jeśli nie można przekonwertować ciągu na wartość daty/godziny lub wystąpiło przepełnienie liczbowe, stan to `COleDateTime` obiektu jest nieprawidłowy.  
  
 Aby uzyskać więcej informacji o granice i implementację `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="setdate"></a>COleDateTime::SetDate  
 Ustawia datę to `COleDateTime` obiektu.  
  
```
int SetDate(  
 int nYear,
 int nMonth,
 int nDay) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nYear`, `nMonth`, `nDay`  
 Wskazuje składniki daty, który ma zostać skopiowany do tego `COleDateTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli wartość to `COleDateTime` obiekt został ustawiony pomyślnie; w przeciwnym razie wartość 1. Zwrócona wartość opiera się na **DateTimeStatus** typ wyliczeniowy. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Data jest równa określonej wartości. Czas ma ustawioną czasu 0, północy.  
  
 Zobacz poniższą tabelę dla zakresu wartości parametrów:  
  
|Parametr|Granice|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
  
 Jeśli zachodzi dnia miesiąca, zostanie przekonwertowane na poprawną dzień następnego miesiąca i miesiąca i/lub rok jest zwiększany odpowiednio. Dzień wartość zerowa wskazuje ostatni dzień minionego miesiąca. Zachowanie jest taka sama jak `SystemTimeToVariantTime`.  
  
 Jeśli wartość data określona przez parametry nie jest prawidłowy, stan tego obiektu jest ustawiony na **COleDateTime::invalid**. Należy używać [GetStatus](#getstatus) do sprawdzania poprawności **data** wartości i nie należy zakładać, że wartość [m_dt](#m_dt) nie zostaną zmodyfikowane.  
  
 Poniżej przedstawiono przykładowe wartości daty:  
  
|`nYear`|`nMonth`|`nDay`|Wartość|  
|-------------|--------------|------------|-----------|  
|2000|2|29|29 lutego 2000|  
|1776|7|4|4 1776 lipca|  
|1925|4|35|35 1925 kwietnia (Nieprawidłowa data)|  
|10000|1|1|1 stycznia 10000 (Nieprawidłowa data)|  
  
 Aby ustawić daty i czasu, zobacz [COleDateTime::SetDateTime](#setdatetime).  
  
 Aby uzyskać informacje na temat funkcji Członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]  
  
##  <a name="setdatetime"></a>COleDateTime::SetDateTime  
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
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Wskazuje datę i godzinę składniki do skopiowania do tego `COleDateTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli wartość to `COleDateTime` obiekt został ustawiony pomyślnie; w przeciwnym razie wartość 1. Zwrócona wartość opiera się na **DateTimeStatus** typ wyliczeniowy. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz poniższą tabelę dla zakresu wartości parametrów:  
  
|Parametr|Granice|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Jeśli zachodzi dnia miesiąca, zostanie przekonwertowane na poprawną dzień następnego miesiąca i miesiąca i/lub rok jest zwiększany odpowiednio. Dzień wartość zerowa wskazuje ostatni dzień minionego miesiąca. Zachowanie jest taka sama jak [SystemTimeToVariantTime](http://msdn.microsoft.com/en-us/d9d69521-9b33-4fc5-8a1c-929f216db450).  
  
 Jeśli wartości daty i godziny określoną przez parametry nie jest prawidłowy, stan tego obiektu jest ustawiony na nieprawidłowy i wartość tego obiektu nie ulega zmianie.  
  
 Poniżej przedstawiono przykładowe wartości czasu:  
  
|`nHour`|`nMin`|`nSec`|Wartość|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Nieprawidłowy|  
|9|60|0|Nieprawidłowy|  
  
 Poniżej przedstawiono przykładowe wartości daty:  
  
|`nYear`|`nMonth`|`nDay`|Wartość|  
|-------------|--------------|------------|-----------|  
|1995|4|15|15 kwietnia 1995 r.|  
|1789|7|14|17 1789 lipca|  
|1925|2|30|Nieprawidłowy|  
|10000|1|1|Nieprawidłowy|  
  
 Aby ustawić tylko data, zobacz [COleDateTime::SetDate](#setdate). Aby ustawić tylko raz, zobacz [COleDateTime::SetTime](#settime).  
  
 Aby uzyskać informacje na temat funkcji Członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetStatus](#getstatus).  
  
##  <a name="setstatus"></a>COleDateTime::SetStatus  
 Ustawia stan tego `COleDateTime` obiektu.  
  
```
void SetStatus(DateTimeStatus status) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Stan*  
 Nowa wartość stanu dla tego `COleDateTime` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 *Stan* wartość parametru jest definiowana za pomocą **DateTimeStatus** wyliczany typ, który jest zdefiniowany w `COleDateTime` klasy. Zobacz [COleDateTime::GetStatus](#getstatus) szczegółowe informacje.  
  
> [!CAUTION]
>  Ta funkcja jest zaawansowane sytuacjach programowania. Ta funkcja nie ma wpływu na dane w tym obiekcie. W większości przypadków posłuży do ustawić stan na `null` lub **nieprawidłowy**. Należy pamiętać, że operator przypisania ( [operatora =](#eq)) i [SetDateTime](#setdatetime) ustawiania stanu obiektu, w oparciu o wartości źródła.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetStatus](#getstatus).  
  
##  <a name="settime"></a>COleDateTime::SetTime  
 Ustawia czas tego `COleDateTime` obiektu.  
  
```
int SetTime(  
 int nHour,
 int nMin,
 int nSec) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nHour`, `nMin`, `nSec`  
 Wskazuje składniki czasu, który ma zostać skopiowany do tego `COleDateTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli wartość to `COleDateTime` obiekt został ustawiony pomyślnie; w przeciwnym razie wartość 1. Zwrócona wartość opiera się na **DateTimeStatus** typ wyliczeniowy. Aby uzyskać więcej informacji, zobacz [SetStatus](#setstatus) funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Czas jest równa określonej wartości. Data jest ustawiona data 0, co oznacza 30 grudnia 1899.  
  
 Zobacz poniższą tabelę dla zakresu wartości parametrów:  
  
|Parametr|Granice|  
|---------------|------------|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Jeśli wartość określoną przez parametry jest nieprawidłowa, czas stanu tego obiektu ustawiono nieprawidłowy i wartość tego obiektu nie ulega zmianie.  
  
 Poniżej przedstawiono przykładowe wartości czasu:  
  
|`nHour`|`nMin`|`nSec`|Wartość|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Nieprawidłowy|  
|9|60|0|Nieprawidłowy|  
  
 Aby ustawić daty i czasu, zobacz [COleDateTime::SetDateTime](#setdatetime).  
  
 Aby uzyskać informacje na temat funkcji Członkowskich, które wartość tego zapytania `COleDateTime` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDay](#getday)  
  
- [GetMonth](#getmonth)  
  
- [GetYear](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Elementu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTime` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [SetDate](#setdate).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleVariant](../../mfc/reference/colevariant-class.md)   
 [Ctime — klasa](../../atl-mfc-shared/reference/ctime-class.md)   
 [Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)



