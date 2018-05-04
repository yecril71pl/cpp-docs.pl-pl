---
title: Klasa CFileTimeSpan | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: facf4abc01ed55ec7c6d84755530a776c68e166d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cfiletimespan-class"></a>Klasa CFileTimeSpan
Ta klasa dostarcza metody do zarządzania względne wartości daty i godziny skojarzonych z plikiem.  
  
## <a name="syntax"></a>Składnia  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Wywołanie tej metody można pobrać przedział czasu z `CFileTimeSpan` obiektu.|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Wywołanie tej metody, aby ustawić zakres czasu `CFileTimeSpan` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|Dokonuje odejmowania `CFileTimeSpan` obiektu.|  
|[CFileTimeSpan::operator! =](#operator_neq)|Porównuje dwa `CFileTimeSpan` obiekty pod kątem nierówności.|  
|[CFileTimeSpan::operator +](#operator_add)|Dokonuje dodanie `CFileTimeSpan` obiektu.|  
|[CFileTimeSpan::operator +=](#operator_add_eq)|Dokonuje dodanie `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|  
|[CFileTimeSpan::operator &lt;](#operator_lt)|Porównuje dwa `CFileTimeSpan` określają mniejszy obiekty.|  
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Porównuje dwa `CFileTimeSpan` obiektów, aby ustalić równości lub mniejszy.|  
|[CFileTimeSpan::operator =](#operator_eq)|Operator przypisania.|  
|[CFileTimeSpan::operator-=](#operator_-_eq)|Dokonuje odejmowania `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|  
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Porównuje dwa `CFileTimeSpan` obiekty pod kątem równości.|  
|[CFileTimeSpan::operator &gt;](#operator_gt)|Porównuje dwa `CFileTimeSpan` obiektów, aby określić większy.|  
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Porównuje dwa `CFileTimeSpan` obiektów, aby ustalić równości lub większy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do zarządzania względną okresów czasu często napotkano podczas wykonywania operacji dotyczących, gdy został utworzony, ostatniego uzyskania dostępu do lub ostatniej modyfikacji pliku. Metody tej klasy są często używane w połączeniu z [klasy CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) obiektów.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltime.h  
  
##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan  
 Konstruktor.  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Istniejące `CFileTimeSpan` obiektu.  
  
 `nSpan`  
 Okres czasu w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 `CFileTimeSpan` Obiektu można tworzyć przy użyciu istniejącego `CFileTimeSpan` obiektu lub wyrażony jako wartość 64-bitowa. Domyślny konstruktor Ustawia zakres czasu na wartość 0.  
  
##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan  
 Wywołanie tej metody można pobrać przedział czasu z `CFileTimeSpan` obiektu.  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca przedział czasu w milisekundach.  
  
##  <a name="operator_-"></a>  CFileTimeSpan::operator-  
 Dokonuje odejmowania **CFileTimeSpan** obiektu.  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTimeSpan` obiekt reprezentujący wynik różnicę między dwoma okresów.  
  
##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =  
 Porównuje dwa `CFileTimeSpan` obiekty pod kątem nierówności.  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywane nie jest równa `CFileTimeSpan` obiektu; w przeciwnym razie **false**.  
  
##  <a name="operator_add"></a>  CFileTimeSpan::operator +  
 Dokonuje dodanie `CFileTimeSpan` obiektu.  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CFileTimeSpan` obiekt obejmuje zawierającą sumę dwóch czasu.  
  
##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=  
 Dokonuje dodanie `CFileTimeSpan` obiektów i przypisuje wynik do bieżącego obiektu.  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTimeSpan` obiekt obejmuje zawierającą sumę dwóch czasu.  
  
##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;  
 Porównuje dwa `CFileTimeSpan` określają mniejszy obiekty.  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy (to znaczy reprezentuje krótszy okres) od drugiego, w przeciwnym razie **false**.  
  
##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=  
 Porównuje dwa `CFileTimeSpan` obiektów, aby ustalić równości lub mniejszy.  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy od (to znaczy reprezentuje krótszy okres czasu) może być mniejszy niż do drugiego, w przeciwnym razie **false**.  
  
##  <a name="operator_eq"></a>  CFileTimeSpan::operator =  
 Operator przypisania.  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTimeSpan` obiektu.  
  
##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator-=  
 Dokonuje odejmowania `CFileTimeSpan` obiektów i przypisuje wynik do bieżącego obiektu.  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CFileTimeSpan` obiektu.  
  
##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==  
 Porównuje dwa `CFileTimeSpan` obiekty pod kątem równości.  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli obiekty są takie same, w przeciwnym razie **false**.  
  
##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;  
 Porównuje dwa `CFileTimeSpan` obiektów, aby określić większy.  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest większy niż (to znaczy reprezentuje dłuższy okres czasu) od drugiego, w przeciwnym razie **false**.  
  
##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=  
 Porównuje dwa `CFileTimeSpan` obiektów, aby ustalić równości lub większy.  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest większy niż (to znaczy reprezentuje dłuższy okres czasu) może być mniejszy niż do drugiego, w przeciwnym razie **false**.  
  
##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan  
 Wywołanie tej metody, aby ustawić zakres czasu `CFileTimeSpan` obiektu.  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nSpan`  
 Nowa wartość przedział czasu w milisekundach.  
  
## <a name="see-also"></a>Zobacz też  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [Klasa CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


