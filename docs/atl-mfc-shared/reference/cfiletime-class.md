---
title: Klasa CFileTime | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d48e899bb058ed27559a4ef699a3a53267064f98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cfiletime-class"></a>Klasa CFileTime
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
|[CFileTime::GetCurrentTime](#getcurrenttime)|Wywołanie tej funkcji statycznych można pobrać `CFileTime` obiekt, który reprezentuje bieżącej systemowej daty i godziny.|  
|[CFileTime::GetTime](#gettime)|Wywołaj tę metodę, aby pobrać razem z `CFileTime` obiektu.|  
|[CFileTime::LocalToUTC](#localtoutc)|Wywołanie tej metody do konwertowania czasu pliku lokalnego do czasu pliku na podstawie na uniwersalny czas koordynowany (UTC).|  
|[CFileTime::SetTime](#settime)|Wywołanie tej metody można ustawić daty i godziny przechowywane przez `CFileTime` obiektu.|  
|[CFileTime::UTCToLocal](#utctolocal)|Wywołanie tej metody można przekonwertować czasu oparte na uniwersalny czas koordynowany (UTC) na czas lokalny plik.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileTime::operator-](#operator_-)|Ten operator jest używana do wykonywania odejmowania na `CFileTime` lub `CFileTimeSpan` obiektu.|  
|[CFileTime::operator! =](#operator_neq)|Ten operator porównuje dwa `CFileTime` obiekty pod kątem nierówności.|  
|[CFileTime::operator +](#operator_add)|Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu.|  
|[CFileTime::operator +=](#operator_add_eq)|Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|  
|[CFileTime::operator&lt;](#operator_lt)|Ten operator porównuje dwa `CFileTime` określają mniejszy obiekty.|  
|[CFileTime::operator&lt;=](#operator_lt_eq)|Ten operator porównuje dwa `CFileTime` obiektów, aby ustalić równości lub mniejszy.|  
|[CFileTime::operator =](#operator_eq)|Operator przypisania.|  
|[CFileTime::operator-=](#operator_-_eq)|Ten operator jest używana do wykonywania odejmowania na `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|  
|[CFileTime::operator ==](#operator_eq_eq)|Ten operator porównuje dwa `CFileTime` obiekty pod kątem równości.|  
|[CFileTime::operator&gt;](#operator_gt)|Ten operator porównuje dwa `CFileTime` obiektów, aby określić większy.|  
|[CFileTime::operator&gt;=](#operator_gt_eq)|Ten operator porównuje dwa `CFileTime` obiektów, aby ustalić równości lub większy.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileTime::Day](#day)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które tworzą jeden dzień.|  
|[CFileTime::Hour](#hour)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które składają się na godzinę.|  
|[CFileTime::Millisecond](#millisecond)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, wchodzące w skład jednej milisekundy.|  
|[CFileTime::Minute](#minute)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które składają się na minutę.|  
|[CFileTime::Second](#second)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, wchodzące w skład jednej sekundzie.|  
|[CFileTime::Week](#week)|Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które tworzą jeden tydzień.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do zarządzania wartości daty i godziny skojarzone z tworzenia, dostępu i modyfikacji plików. Metody i danych z tej klasy są często używane w połączeniu z `CFileTimeSpan` obiektów, które postępowania w przypadku wartości względne czasu.  
  
 Wartość daty i godziny jest przechowywana jako 64-bitowych wartość odpowiadającą liczbie 100-nanosekundowych interwałów od 1 stycznia 1601. Ten format jest używany uniwersalny czas koordynowany (UTC).  
  
 Dostępne są następujące statycznych const zmienne Członkowskie do uproszczenia obliczeń:  
  
|Zmiennej członkowskiej|Liczba 100-nanosekundowych interwałów|  
|---------------------|-----------------------------------------|  
|Milisekundy|10 000|  
|Sekunda|Milisekundy * 1000|  
|Minuta|Drugi * 60|  
|Godzina|Minuta * 60|  
|Dzień|Godzina * 24|  
|Tydzień|Dzień * 7|  
  
 **Uwaga** nie wszystkie systemy plików mogą być rejestrowane tworzenia i czas ostatniego dostępu i nie wszystkie systemy plików zarejestruj je w taki sam sposób. Na przykład w systemie plików FAT systemu Windows NT, utworzyć czasu ma rozdzielczość 10 MS, czas zapisu ma rozdzielczość 2 sekundy, i czas dostępu ma rozdzielczość 1 dzień (data access). W systemie plików NTFS czas dostępu ma rozdzielczość 1 godzina. Ponadto FAT rejestruje czas na dysku w czasie lokalnym, ale NTFS rejestruje czas na dysku w formacie UTC. Aby uzyskać więcej informacji, zobacz [czasy plików](http://msdn.microsoft.com/library/windows/desktop/ms724290).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `FILETIME`  
  
 `CFileTime`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltime.h  
  
##  <a name="cfiletime"></a>CFileTime::CFileTime  
 Konstruktor.  
  
```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 A [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury.  
  
 `nTime`  
 Data i godzina, wyrażony jako wartość 64-bitowa.  
  
### <a name="remarks"></a>Uwagi  
 `CFileTime` Obiektu można tworzyć przy użyciu istniejących datę i godzinę z `FILETIME` struktury lub wyrażony jako 64-bitową wartość (w lokalnej lub formaty czasu uniwersalnego czasu koordynowanego (UTC)). Domyślny konstruktor ustawia czas na 0.  
  
##  <a name="day"></a>CFileTime::Day  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które tworzą jeden dzień.  
  
```
static const ULONGLONG Day = Hour* 24;
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](#millisecond).  
  
##  <a name="getcurrenttime"></a>CFileTime::GetCurrentTime  
 Wywołanie tej funkcji statycznych można pobrać `CFileTime` obiekt, który reprezentuje bieżącej systemowej daty i godziny.  
  
```
static CFileTime GetCurrentTime() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącej systemowej daty i godziny w formacie uniwersalnego czasu koordynowanego (UTC).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]  
  
##  <a name="gettime"></a>CFileTime::GetTime  
 Wywołaj tę metodę, aby pobrać razem z `CFileTime` obiektu.  
  
```
ULONGLONG GetTime() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca datę i godzinę jako liczbę 64-bitowe, które może być w formacie uniwersalnego czasu koordynowanego (UTC) albo lokalne.  
  
##  <a name="hour"></a>CFileTime::Hour  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które składają się na godzinę.  
  
```
static const ULONGLONG Hour = Minute* 60;
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](#millisecond).  
  
##  <a name="localtoutc"></a>CFileTime::LocalToUTC  
 Wywołanie tej metody do konwertowania czasu pliku lokalnego do czasu pliku na podstawie na uniwersalny czas koordynowany (UTC).  
  
```
CFileTime LocalToUTC() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTime` obiekt zawierający godzinę w formacie UTC.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::UTCToLocal](#utctolocal).  
  
##  <a name="millisecond"></a>CFileTime::Millisecond  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, wchodzące w skład jednej milisekundy.  
  
```
static const ULONGLONG Millisecond = 10000;
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]  
  
##  <a name="minute"></a>CFileTime::Minute  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które składają się na minutę.  
  
```
static const ULONGLONG Minute = Second* 60;
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](#millisecond).  
  
##  <a name="operator_-"></a>CFileTime::operator-  
 Ten operator jest używana do wykonywania odejmowania na `CFileTime` lub `CFileTimeSpan` obiektu.  
  
```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
 `ft`  
 A `CFileTime` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTime` obiektu lub `CFileTimeSpan` obiekt reprezentujący wynik odstęp czasu między tymi dwoma obiektami.  
  
##  <a name="operator_neq"></a>CFileTime::operator! =  
 Ten operator porównuje dwa `CFileTime` obiekty pod kątem nierówności.  
  
```
bool operator!=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywane nie jest równa `CFileTime` obiektu, w przeciwnym razie **false**.  
  
##  <a name="operator_add"></a>CFileTime::operator +  
 Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu.  
  
```
CFileTime operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTime` obiekt reprezentujący wynik oryginalnego czas oraz względne czasu.  
  
##  <a name="operator_add_eq"></a>CFileTime::operator +=  
 Ten operator jest używany podczas dodawania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.  
  
```
CFileTime& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTime` obiekt reprezentujący wynik oryginalnego czas oraz względne czasu.  
  
##  <a name="operator_lt"></a>CFileTime::operator&lt;  
 Ten operator porównuje dwa `CFileTime` określają mniejszy obiekty.  
  
```
bool operator<(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy (wcześniej w czasie) od drugiej, **false** inaczej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]  
  
##  <a name="operator_lt_eq"></a>CFileTime::operator&lt;=  
 Ten operator porównuje dwa `CFileTime` obiektów, aby ustalić równości lub mniejszy.  
  
```
bool operator<=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy niż (wcześniej w czasie) lub równe drugiemu, w przeciwnym razie **false**.  
  
##  <a name="operator_eq"></a>CFileTime::operator =  
 Operator przypisania.  
  
```
CFileTime& operator=(const FILETIME& ft) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 A `CFileTime` obiekt zawierający nową godzinę i datę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTime` obiektu.  
  
##  <a name="operator_-_eq"></a>CFileTime::operator-=  
 Ten operator jest używana do wykonywania odejmowania na `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.  
  
```
CFileTime& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiekt zawierający względne czasu do odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTime` obiektu.  
  
##  <a name="operator_eq_eq"></a>CFileTime::operator ==  
 Ten operator porównuje dwa `CFileTime` obiekty pod kątem równości.  
  
```
bool operator==(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli obiekty są takie same, w przeciwnym razie **false**.  
  
##  <a name="operator_gt"></a>CFileTime::operator&gt;  
 Ten operator porównuje dwa `CFileTime` obiektów, aby określić większy.  
  
```
bool operator>(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli (później w czasie) jest większa niż pierwszy obiekt od drugiego, w przeciwnym razie **false**.  
  
##  <a name="operator_gt_eq"></a>CFileTime::operator&gt;=  
 Ten operator porównuje dwa `CFileTime` obiektów, aby ustalić równości lub większy.  
  
```
bool operator>=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest większy niż (później w czasie) lub równe drugiemu, w przeciwnym razie **false**.  
  
##  <a name="second"></a>CFileTime::Second  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które tworzą jeden dzień.  
  
```
static const ULONGLONG Second = Millisecond* 1000;
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](#millisecond).  
  
##  <a name="settime"></a>CFileTime::SetTime  
 Wywołanie tej metody można ustawić daty i godziny przechowywane przez `CFileTime` obiektu.  
  
```
void SetTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nTime`  
 Wartość 64-bitowa reprezentująca datę i godzinę w lokalnej lub w formacie uniwersalnego czasu koordynowanego (UTC).  
  
##  <a name="utctolocal"></a>CFileTime::UTCToLocal  
 Wywołanie tej metody można przekonwertować czasu oparte na uniwersalny czas koordynowany (UTC) na czas lokalny plik.  
  
```
CFileTime UTCToLocal() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTime` obiekt zawierający godzinę w formacie czasu lokalnego pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]  
  
##  <a name="week"></a>CFileTime::Week  
 Element członkowski danych statycznych przechowywania Liczba 100-nanosekundowych interwałów, które tworzą jeden tydzień.  
  
```
static const ULONGLONG Week = Day* 7;
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](#millisecond).  
  
## <a name="see-also"></a>Zobacz też  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [Klasa CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


