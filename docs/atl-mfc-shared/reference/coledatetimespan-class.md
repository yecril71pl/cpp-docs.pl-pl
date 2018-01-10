---
title: Klasa COleDateTimeSpan | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
dev_langs: C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 173ae35f49379bcccf552a105b5615378e7a42cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledatetimespan-class"></a>Klasa COleDateTimeSpan
Reprezentuje względne czasu, przedział czasu.  
  
## <a name="syntax"></a>Składnia  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Konstruuje `COleDateTimeSpan` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|Generuje reprezentację ciągu sformatowaną `COleDateTimeSpan` obiektu.|  
|[COleDateTimeSpan::GetDays](#getdays)|Zwraca część dnia z zakresu, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetHours](#gethours)|Zwraca część godzin z zakresu, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|Zwraca część minut zakresu, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|Zwraca część drugiego zakresu, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetStatus](#getstatus)|Pobiera stan (ważności) to `COleDateTimeSpan` obiektu.|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Zwraca liczbę dni, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Zwraca liczbę godzin, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Zwraca liczbę minut, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Zwraca liczbę sekund, to `COleDateTimeSpan` reprezentuje obiekt.|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Ustawia wartość to `COleDateTimeSpan` obiektu.|  
|[COleDateTimeSpan::SetStatus](#setstatus)|Ustawia stan (ważności) to `COleDateTimeSpan` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|||  
|-|-|  
|[operator +, -](#operator_add_-)|Dodaj, odejmować, a następnie Zmień znak `COleDateTimeSpan` wartości.|  
|[operator +=-=](#operator_add_eq_-_eq)|Dodawanie i usuwanie `COleDateTimeSpan` wartości z tej `COleDateTimeSpan` wartości.|  
|[operator =](#operator_eq)|Kopie `COleDateTimeSpan` wartość.|  
|[operator ==, <, < =](#coledatetimespan_relational_operators)|Porównać dwa `COleDateTimeSpan` wartości.|  
|[double — operator](#operator_double)|Konwertuje to `COleDateTimeSpan` do wartości **podwójne**.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|Zawiera podstawową **podwójne** dla tego `COleDateTimeSpan` obiektu.|  
|[COleDateTimeSpan::m_status](#m_status)|Zawiera informacje o stanie tego `COleDateTimeSpan` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleDateTimeSpan`nie ma klasy podstawowej.  
  
 A `COleDateTimeSpan` zachowuje czasu w dni.  
  
 `COleDateTimeSpan`jest używana wraz ze swoją klasą Pomocnika [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`hermetyzuje **data** typu danych automatyzacji OLE. `COleDateTime`reprezentuje wartości bezwzględnego czasu. Wszystkie `COleDateTime` obejmują obliczenia `COleDateTimeSpan` wartości. Relacja między tych klas jest odpowiednikiem co między [ctime —](../../atl-mfc-shared/reference/ctime-class.md) i [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Aby uzyskać więcej informacji na temat `COleDateTime` i `COleDateTimeSpan` klas, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>Operatory relacyjne COleDateTimeSpan  
 Operatory porównania.  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dateSpan*  
 `COleDateTimeSpan` Do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tych operatorów porównywania dwóch wartości daty okres i zwracać **true** Jeśli wynikiem warunku jest PRAWDA; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  ATLASSERT wystąpi, jeśli którykolwiek argument operacji jest nieprawidłowy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
 Konstruuje `COleDateTimeSpan` obiektu.  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dblSpanSrc`  
 Liczba dni, które ma zostać skopiowany do nowego `COleDateTimeSpan` obiektu.  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Wskazuje dnia i godziny wartości ma zostać skopiowany do nowego `COleDateTimeSpan` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów tworzenia nowych `COleDateTimeSpan` obiektów zainicjowany z podaną wartością. Krótki opis każdego z tych konstruktorów następująco:  
  
- **(COleDateTimeSpan)** tworzy `COleDateTimeSpan` obiektu równe 0.  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)** tworzy `COleDateTimeSpan` obiektu z wartości zmiennoprzecinkowych.  
  
- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)**  Konstruuje `COleDateTimeSpan` obiekt został zainicjowany w określonej wartości liczbowe.  
  
 Stan nowego `COleDateTimeSpan` obiekt jest ustawiony na prawidłową.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTimeSpan` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 Generuje reprezentację ciągu sformatowaną `COleDateTimeSpan` obiektu.  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pFormat`  
 Formatowanie ciąg podobny do `printf` ciąg formatowania. Formatowanie kodów poprzedzone w procentach ( `%`) podpisania, są zastępowane przez odpowiednie `COleDateTimeSpan` składnika. Zwrócony ciąg jest kopiowana niezmienione innych znaków w ciągu formatowania. Wartość i znaczenie formatowania kody **Format** wymienionych poniżej:  
  
- **%H** godzin w bieżącym dniu  
  
- **%M** minut w ciągu bieżącej godziny  
  
- **%S** sekund w ciągu bieżącej minuty  
  
- **%%**Znak procentu  
  
 Cztery kodów formatu wymienione powyżej są tylko kody akceptujących Format.  
  
-  
  
 `nID`  
 Identyfikator zasobu ciągu formatu formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` zawierający sformatowana wartość Data okres.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływać te funkcje można utworzyć sformatowane reprezentację wartości przedział czasu. Jeśli stan to `COleDateTimeSpan` obiektu ma wartość null, zwracana wartość jest pustym ciągiem. Jeśli stan jest nieprawidłowy, zwracany ciąg jest określony przez zasób ciągu **IDS_INVALID_DATETIMESPAN**.  
  
 Krótki opis formularzy dla tej funkcji są następujące:  
  
 **Format (** `pFormat` **)**  
 Ten formularz formatuje wartość przy użyciu ciąg formatu, który zawiera specjalne formatowanie kody, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania zostanie przekazany jako parametr do funkcji.  
  
 **Format (** `nID` **)**  
 Ten formularz formatuje wartość przy użyciu ciąg formatu, który zawiera specjalne formatowanie kody, które są poprzedzone znakiem procentu (%), podobnie jak w `printf`. Ciąg formatowania jest zasobem. Identyfikator zasobu ciągu jest przekazywany jako parametr.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 Pobiera część dnia ta wartość daty okres.  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dzień część ta wartość daty okres.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany wartości z tej funkcji zakresie około - 3,615,000 i 3,615,000.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 Pobiera godzinę część ta wartość daty okres.  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba godzin korzystania z część ta wartość daty okres.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tego zakresu funkcji między - 23 i 23.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 Pobiera część minutowa ta wartość daty okres.  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Fragment minut ta wartość daty okres.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tej funkcji zakresu od - 59 do 59.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 Pobiera drugiej części ta wartość daty okres.  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Części sekundy ta wartość daty okres.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tej funkcji zakresu od - 59 do 59.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 Pobiera stan (ważności) to `COleDateTimeSpan` obiektu.  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan to `COleDateTimeSpan` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana jest definiowana za **DateTimeSpanStatus** wyliczany typ, który jest zdefiniowany w `COleDateTimeSpan` klasy.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- **COleDateTimeSpan::valid** wskazuje tego `COleDateTimeSpan` obiekt jest prawidłowy.  
  
- **COleDateTimeSpan::invalid** wskazuje tego `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleDateTimeSpan::null** wskazuje tego `COleDateTimeSpan` obiektu ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
 Stan `COleDateTimeSpan` obiektu jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.  
  
-   Jeśli wartość jest nieprawidłowa została przypisana do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłową przy użyciu `SetStatus`.  
  
 Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTimeSpan` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 Pobiera wartość ta data okres wyrażony w dniach.  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta wartość daty okres wyrażony w dniach. Mimo że ta funkcja jest prototypowana, aby zwrócić wartość o podwójnej precyzji, zawsze zwróci wartość całkowitą.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tego zakresu funkcji między około - 3.65e6 i 3.65e6.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 Pobiera wartość ta data okres wyrażony w godzinach.  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta wartość daty okres wyrażony w godzinach. Mimo że ta funkcja jest prototypowana, aby zwrócić wartość o podwójnej precyzji, zawsze zwróci wartość całkowitą.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tego zakresu funkcji między około - 8.77e7 i 8.77e7.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 Pobiera wartość ta data okres wyrażone w minutach.  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta wartość daty okres wyrażone w minutach. Mimo że ta funkcja jest prototypowana, aby zwrócić wartość o podwójnej precyzji, zawsze zwróci wartość całkowitą.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tego zakresu funkcji między około - 5.26e9 i 5.26e9.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 Pobiera wartość ta data okres wyrażony w sekundach.  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta wartość daty okres wyrażony w sekundach. Mimo że ta funkcja jest prototypowana, aby zwrócić wartość o podwójnej precyzji, zawsze zwróci wartość całkowitą.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracane z tej funkcji w zakresie między około — 3.16e11 do 3.16e11.  
  
 Do innych funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetTotalDays](#gettotaldays).  
  
##  <a name="m_span"></a>COleDateTimeSpan::m_span  
 Podstawowa **podwójne** wartość to `COleDateTime` obiektu.  
  
```
double m_span;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość określa Data /-przedział czasu w dni.  
  
> [!CAUTION]
>  Zmiana wartości w **podwójne** element członkowski danych zmieni wartość tego `COleDateTimeSpan` obiektu. Nie zmienia stanu to `COleDateTimeSpan` obiektu.  
  
##  <a name="m_status"></a>COleDateTimeSpan::m_status  
 Typ dla tego elementu członkowskiego danych jest typ wyliczeniowy **DateTimeSpanStatus**, który jest zdefiniowany w ramach `COleDateTimeSpan` klasy.  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>Uwagi  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- **COleDateTimeSpan::valid** wskazuje tego `COleDateTimeSpan` obiekt jest prawidłowy.  
  
- **COleDateTimeSpan::invalid** wskazuje tego `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleDateTimeSpan::null** wskazuje tego `COleDateTimeSpan` obiektu ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
 Stan `COleDateTimeSpan` obiektu jest nieprawidłowy w następujących przypadkach:  
  
-   Jeśli ten obiekt napotkał przepełnienie lub niedomiar podczas operacji arytmetycznych przypisania, a mianowicie `+=` lub `-=`.  
  
-   Jeśli wartość jest nieprawidłowa została przypisana do tego obiektu.  
  
-   Jeśli stan tego obiektu jawnie ustawiono nieprawidłową przy użyciu [SetStatus](#setstatus).  
  
 Aby uzyskać więcej informacji o operacjach, które mogą ustawić stan na nieprawidłowy, zobacz [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) i [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
> [!CAUTION]
>  Ten element członkowski danych jest zaawansowane sytuacjach programowania. Należy używać funkcji Członkowskich wbudowanego [GetStatus](#getstatus) i [SetStatus](#setstatus). Zobacz `SetStatus` dla dalszego ostrzeżenia dotyczące jawne ustawienie tego elementu członkowskiego danych.  
  
 Aby uzyskać więcej informacji na temat zakresem dla `COleDateTimeSpan` wartości, zobacz artykuł [daty i godziny: Obsługa automatyzacji](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 Kopie `COleDateTimeSpan` wartość.  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator przypisania przeciążone kopiuje wartość Data okres źródła do tego `COleDateTimeSpan` obiektu.  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +, -  
 Dodaj, odejmować, a następnie Zmień znak `COleDateTimeSpan` wartości.  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze dwa operatory umożliwiają dodawanie i odejmowanie wartości daty okres. Trzeci pozwala zmienić znak wartości daty okres.  
  
 Jeśli jest jeden z argumentów, null, stan wynikowy `COleDateTimeSpan` ma wartość null.  
  
 Jeśli jeden z argumentów jest nieprawidłowa i nie ma innych wartości null, stan wynikowy `COleDateTimeSpan` wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator +=-=  
 Dodawanie i usuwanie `COleDateTimeSpan` wartości z tej `COleDateTimeSpan` wartości.  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Operatory te umożliwiają dodawanie i odejmowanie wartości daty okres od tego `COleDateTimeSpan` obiektu. Jeśli jest jeden z argumentów, null, stan wynikowy `COleDateTimeSpan` ma wartość null.  
  
 Jeśli jeden z argumentów jest nieprawidłowa i nie ma innych wartości null, stan wynikowy `COleDateTimeSpan` wartość jest nieprawidłowa.  
  
 Aby uzyskać więcej informacji o wartościach stan prawidłowy, nieprawidłowy i wartości null, zobacz [m_status](#m_status) zmiennej członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>COleDateTimeSpan::operator podwójne  
 Konwertuje to `COleDateTimeSpan` do wartości **podwójne**.  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość tego `COleDateTimeSpan` wartość jako liczba zmiennoprzecinkowa dni.  
  
##  <a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 Ustawia wartość ta wartość daty okres.  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Wskazuje zakres dat i przedział czasu wartości ma zostać skopiowany do tego `COleDateTimeSpan` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Dla funkcji, które kwerendę dotyczącą wartości `COleDateTimeSpan` obiektów, zobacz następujące funkcje Członkowskie:  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 Ustawia stan (ważności) to `COleDateTimeSpan` obiektu.  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Stan*  
 Nowa wartość stanu dla tego `COleDateTimeSpan` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 *Stan* wartość parametru jest definiowana za pomocą **DateTimeSpanStatus** wyliczany typ, który jest zdefiniowany w `COleDateTimeSpan` klasy.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Krótki opis tych wartości stanu lista:  
  
- **COleDateTimeSpan::valid** wskazuje tego `COleDateTimeSpan` obiekt jest prawidłowy.  
  
- **COleDateTimeSpan::invalid** wskazuje tego `COleDateTimeSpan` obiektu jest nieprawidłowy; oznacza to, że jej wartość może być nieprawidłowa.  
  
- **COleDateTimeSpan::null** wskazuje tego `COleDateTimeSpan` obiektu ma wartość null, oznacza to, że podano żadnej wartości dla tego obiektu. (Jest to "null" w tym sensie bazy danych "o wartości,", w przeciwieństwie do języka C++ **NULL**.)  
  
    > [!CAUTION]
    >  Ta funkcja jest zaawansowane sytuacjach programowania. Ta funkcja nie ma wpływu na dane w tym obiekcie. W większości przypadków posłuży do ustawić stan na `null` lub **nieprawidłowy**. Należy pamiętać, że operator przypisania ( [operatora =](#eq)) i [SetDateTimeSpan](#setdatetimespan) ustawiania stanu obiektu, w oparciu o wartości źródła.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [Ctime — klasa](../../atl-mfc-shared/reference/ctime-class.md)   
 [Klasa CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


