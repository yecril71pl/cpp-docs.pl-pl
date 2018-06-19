---
title: Klasa CTimeSpan | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd95d26dd2df41f16091379c892f67319c218cc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365321"
---
# <a name="ctimespan-class"></a>Klasa CTimeSpan
Ilość czasu, który wewnętrznie jest przechowywany jako liczbę sekund w przedziale czasu.  
  
## <a name="syntax"></a>Składnia  
  
```
class CTimeSpan
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTimeSpan::CTimeSpan](#ctimespan)|Konstruuje `CTimeSpan` obiektów na różne sposoby.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTimeSpan::Format](#format)|Konwertuje `CTimeSpan` na ciąg sformatowany.|  
|[CTimeSpan::GetDays](#getdays)|Zwraca wartość reprezentującą liczbę dni pełnej, w tym `CTimeSpan`.|  
|[CTimeSpan::GetHours](#gethours)|Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (-23 do 23).|  
|[CTimeSpan::GetMinutes](#getminutes)|Zwraca wartość reprezentującą liczbę minut w ciągu bieżącej godziny (-59 do 59).|  
|[CTimeSpan::GetSeconds](#getseconds)|Zwraca wartość reprezentującą liczbę sekund w ciągu bieżącej minuty (-59 do 59).|  
|[CTimeSpan::GetTimeSpan](#gettimespan)|Zwraca wartość `CTimeSpan` obiektu.|  
|[CTimeSpan::GetTotalHours](#gettotalhours)|Zwraca wartość, która reprezentuje łączną liczbę pełną godzin, w tym `CTimeSpan`.|  
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca wartość, która reprezentuje łączną liczbę pełną minut, w tym `CTimeSpan`.|  
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca wartość wskazującą całkowitą liczbę sekund pełną w tym `CTimeSpan`.|  
|[CTimeSpan::Serialize64](#serialize64)|Serializuje dane do lub z archiwum.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator + —](#operator_add_-)|Dodaje i odejmuje `CTimeSpan` obiektów.|  
|[+= — operator-=](#operator_add_eq_-_eq)|Dodaje i odejmuje `CTimeSpan` obiekt do i z tego `CTimeSpan`.|  
|[Operator == < itp.](#ctimespan_comparison_operators)|Porównuje dwie wartości względne czasu.|  
  
## <a name="remarks"></a>Uwagi  
 `CTimeSpan` nie ma klasy podstawowej.  
  
 `CTimeSpan` Funkcje konwersji sekund do różnych kombinacji dni, godziny, minuty i sekundy.  
  
 `CTimeSpan` Obiekt jest przechowywany w **__time64_t —** struktury, która jest 8 bajtów.  
  
 Klasa pomocnika, [ctime —](../../atl-mfc-shared/reference/ctime-class.md), reprezentuje bezwzględnego czasu.  
  
 `CTime` i `CTimeSpan` klasy nie są przeznaczone do wyprowadzenia. Ponieważ nie żadnych funkcji wirtualnych rozmiar obu `CTime` i `CTimeSpan` obiektów jest dokładnie 8 bajtów. Większość funkcji elementów członkowskich są wbudowane.  
  
 Aby uzyskać więcej informacji na temat używania `CTimeSpan`, zobacz artykuły [Data i godzina](../../atl-mfc-shared/date-and-time.md), i [zarządzanie czasem](../../c-runtime-library/time-management.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltime.h  
  
##  <a name="ctimespan_comparison_operators"></a>  Operatory porównania CTimeSpan  
 Operatory porównania.  
  
```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
  
 Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Te operatory porównania dwóch wartości względne czasu. Zwracają **true** Jeśli wynikiem warunku jest PRAWDA; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]  
  
##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan  
 Konstruuje `CTimeSpan` obiektów na różne sposoby.  
  
```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(  
 LONG lDays,
 int nHours,
 int nMins,
 int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *timeSpanSrc*  
 A `CTimeSpan` obiektu, który już istnieje.  
  
 `time`  
 A **__time64_t —** wartość czasu, która jest to liczba sekund w przedziale czasu.  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Dni, godziny minuty i sekundy, odpowiednio.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów Utwórz nową `CTimeSpan` obiektu zainicjowane z określonego czasu względną. Poniżej opisano każdy konstruktora:  
  
- **CTimeSpan ();**  Tworzy niezainicjowany `CTimeSpan` obiektu.  
  
- **CTimeSpan (const CTimeSpan &);**  Tworzy `CTimeSpan` obiektu z innego `CTimeSpan` wartość.  
  
- **CTimeSpan (__time64_t —);**  Tworzy `CTimeSpan` obiekt z **__time64_t —** typu.  
  
- **CTimeSpan (DŁUGI**, **int, int, int);** Konstruuje `CTimeSpan` obiektu ze składników z każdego składnika ograniczone do następujących zakresów:  
  
    |Składnik|Zakres|  
    |---------------|-----------|  
    |`lDays`|25 000 0 (około)|  
    |`nHours`|0-23|  
    |`nMins`|0-59|  
    |`nSecs`|0-59|  
  
 Należy pamiętać, że wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń, jeśli jeden lub większa liczba instalowanych składników godzinach jest poza zakresem. Jest obowiązek Waliduj argumenty przed wywołaniem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]  
  
##  <a name="format"></a>  CTimeSpan::Format  
 Generuje ciąg formatowania, który odpowiada to `CTimeSpan`.  
  
```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pFormat`, `pszFormat`  
 Formatowanie ciąg podobny do `printf` ciąg formatowania. Formatowanie kodów poprzedzone w procentach ( `%`) podpisania, są zastępowane przez odpowiednie `CTimeSpan` składnika. Zwrócony ciąg jest kopiowana niezmienione innych znaków w ciągu formatowania. Wartość i znaczenie formatowania kody **Format** wymienionych poniżej:  
  
- **%D** łączna liczba dni, w tym `CTimeSpan`  
  
- **%H** godzin w bieżącym dniu  
  
- **%M** minut w ciągu bieżącej godziny  
  
- **%S** sekund w ciągu bieżącej minuty  
  
- **%%** Znak procentu  
  
 `nID`  
 Identyfikator ciągu, która identyfikuje ten format.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który zawiera czas sformatowany.  
  
### <a name="remarks"></a>Uwagi  
 Wersja do debugowania biblioteki sprawdza kody formatowania i potwierdza, czy kod nie jest na liście powyżej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]  
  
##  <a name="getdays"></a>  CTimeSpan::GetDays  
 Zwraca wartość reprezentującą liczbę dni pełnej, w tym `CTimeSpan`.  
  
```
LONGLONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę dni, 24-godzinnym pełną w przedziale czasu. Ta wartość może być ujemna, jeśli przedział czasu jest ujemna.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że może spowodować czasu letniego `GetDays` do zwrócenia wyniku potencjalnie zaskakująco. Na przykład gdy czasu letniego jest aktywna, **GetDays** zgłasza liczbę dni między 1 kwietnia i 1 maja jako 29 nie 30, ponieważ jeden dzień w kwietniu jest obcinana przez godzinę i dlatego nie liczy się jako pełny dzień.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]  
  
##  <a name="gethours"></a>  CTimeSpan::GetHours  
 Zwraca wartość reprezentującą liczbę godzin w bieżącym dniu (-23 do 23).  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę godzin w bieżącym dniu. Zakres jest -23 do 23.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]  
  
##  <a name="getminutes"></a>  CTimeSpan::GetMinutes  
 Zwraca wartość reprezentującą liczbę minut w ciągu bieżącej godziny (-59 do 59).  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę minut, w ciągu bieżącej godziny. Zakres jest -59 do 59.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHours](#gethours).  
  
##  <a name="getseconds"></a>  CTimeSpan::GetSeconds  
 Zwraca wartość reprezentującą liczbę sekund w ciągu bieżącej minuty (-59 do 59).  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę sekund w ciągu bieżącej minuty. Zakres jest -59 do 59.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetHours](#gethours).  
  
##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan  
 Zwraca wartość `CTimeSpan` obiektu.  
  
```
__ time64_t GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą wartość `CTimeSpan` obiektu.  
  
##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours  
 Zwraca wartość, która reprezentuje łączną liczbę pełną godzin, w tym `CTimeSpan`.  
  
```
LONGLONG GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca łączną liczbę godzin pełną w tym `CTimeSpan`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]  
  
##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes  
 Zwraca wartość, która reprezentuje łączną liczbę pełną minut, w tym `CTimeSpan`.  
  
```
LONGLONG GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca łączną liczbę minut pełną w tym `CTimeSpan`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetTotalHours](#gettotalhours).  
  
##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds  
 Zwraca wartość wskazującą całkowitą liczbę sekund pełną w tym `CTimeSpan`.  
  
```
LONGLONG GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sumę sekund pełną w tym `CTimeSpan`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetTotalHours](#gettotalhours).  
  
##  <a name="operator_add_-"></a>  CTimeSpan::operator +, -  
 Dodaje i odejmuje `CTimeSpan` obiektów.  
  
```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Wartość do dodania do `CTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CTimeSpan` obiekt reprezentujący wynik operacji.  
  
### <a name="remarks"></a>Uwagi  
 Te dwa operatory pozwala na dodawanie i usuwanie `CTimeSpan` obiektów do i od siebie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator +=-=  
 Dodaje i odejmuje `CTimeSpan` obiekt do i z tego `CTimeSpan`.  
  
```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Wartość do dodania do `CTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowany interfejs `CTimeSpan` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Operatory te umożliwiają dodawanie i odejmowanie `CTimeSpan` obiekt do i z tego `CTimeSpan`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]  
  
##  <a name="serialize64"></a>  CTimeSpan::Serialize64  
  
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
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


