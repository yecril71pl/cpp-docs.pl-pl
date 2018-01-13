---
title: Klasa CTokenGroups | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
dev_langs: C++
helpviewer_keywords: CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6f0e8e2f63d5765e0e888c7a98cea77c862e241
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctokengroups-class"></a>Klasa CTokenGroups
Ta klasa jest otoki dla **TOKEN_GROUPS** struktury.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CTokenGroups
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor.|  
|[CTokenGroups:: ~ CTokenGroups](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenGroups::Add](#add)|Dodaje `CSid` lub istniejące **TOKEN_GROUPS** struktury do `CTokenGroups` obiektu.|  
|[CTokenGroups::Delete](#delete)|Usuwa `CSid` i jego atrybuty skojarzone z `CTokenGroups` obiektu.|  
|[CTokenGroups::DeleteAll](#deleteall)|Usuwa wszystkie `CSid` obiektów i ich atrybuty skojarzone z `CTokenGroups` obiektu.|  
|[CTokenGroups::GetCount](#getcount)|Zwraca liczbę `CSid` obiektów i skojarzonych z nimi atrybutów, zawarte w **CTokenGroups** obiektu.|  
|[CTokenGroups::GetLength](#getlength)|Zwraca rozmiar `CTokenGroups` obiektu.|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Pobiera wskaźnik do **TOKEN_GROUPS** struktury.|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Pobiera `CSid` obiektów i atrybutów należących do `CTokenGroups` obiektu.|  
|[CTokenGroups::LookupSid](#lookupsid)|Pobiera atrybuty skojarzone z `CSid` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Rzutowania `CTokenGroups` obiektu na wskaźnik do **TOKEN_GROUPS** struktury.|  
|[CTokenGroups::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 [Token dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909) jest obiekt, który opisuje kontekst zabezpieczeń proces lub Wątek i jest przydzielana każdy użytkownik zalogowany do systemu Windows NT lub Windows 2000.  
  
 **CTokenGroups** klasy jest otoki dla [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury, zawierający informacje o grupie identyfikatory zabezpieczeń (SID) w tokenie dostępu.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="add"></a>CTokenGroups::Add  
 Dodaje `CSid` lub istniejące **TOKEN_GROUPS** struktury do `CTokenGroups` obiektu.  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md) obiektu.  
  
 `dwAttributes`  
 Atrybuty do skojarzenia z `CSid` obiektu.  
  
 *rTokenGroups*  
 A [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Te metody Dodaj jeden lub kilka `CSid` obiektów i ich skojarzonych z nimi atrybutów do `CTokenGroups` obiektu.  
  
##  <a name="ctokengroups"></a>CTokenGroups::CTokenGroups  
 Konstruktor.  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenGroups` Obiektu lub [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) strukturę, z którą chcesz utworzyć `CTokenGroups` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CTokenGroups` Można opcjonalnie można utworzyć obiektu przy użyciu **TOKEN_GROUPS** struktury lub wcześniej zdefiniowanego `CTokenGroups` obiektu.  
  
##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups  
 Destruktor.  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="delete"></a>CTokenGroups::Delete  
 Usuwa `CSid` i jego atrybuty skojarzone z `CTokenGroups` obiektu.  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md) obiektu, dla którego identyfikator zabezpieczeń (SID) i atrybuty powinna zostać usunięta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli `CSid` zostanie usunięty, wartość false w przeciwnym razie wartość.  
  
##  <a name="deleteall"></a>CTokenGroups::DeleteAll  
 Usuwa wszystkie `CSid` obiektów i ich atrybuty skojarzone z `CTokenGroups` obiektu.  
  
```
void DeleteAll() throw();
```  
  
##  <a name="getcount"></a>CTokenGroups::GetCount  
 Zwraca liczbę `CSid` obiektów zawartych w `CTokenGroups`.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę [CSid](../../atl/reference/csid-class.md) obiektów i ich skojarzonych z nimi atrybutów, zawarte w `CTokenGroups` obiektu.  
  
##  <a name="getlength"></a>CTokenGroups::GetLength  
 Zwraca rozmiar **CTokenGroup** obiektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca rozmiar całkowitą **CTokenGroup** obiektu w bajtach.  
  
##  <a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS  
 Pobiera wskaźnik do **TOKEN_GROUPS** struktury.  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobiera wskaźnik do [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) należących do struktury `CTokenGroups` obiektu tokenu dostępu.  
  
##  <a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes  
 Pobiera `CSid` obiektów i (opcjonalnie) atrybuty należące do `CTokenGroups` obiektu.  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSids`  
 Wskaźnik do tablicy [CSid](../../atl/reference/csid-class.md) obiektów.  
  
 `pAttributes`  
 Wskaźnik do dane DWORD tablicy. Jeśli ten parametr jest pominięty, lub wartość NULL, atrybuty nie są pobierane.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyliczenie wszystkich `CSid` obiektów zawartych w `CTokenGroups` obiektu i umieść je i (opcjonalnie) flagi atrybutów w tablicy obiektów.  
  
##  <a name="lookupsid"></a>CTokenGroups::LookupSid  
 Pobiera atrybuty skojarzone z `CSid` obiektu.  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md) obiektu.  
  
 `pdwAttributes`  
 Wskaźnik do typu DWORD, która będzie akceptować `CSid` atrybutu obiektu. Jeśli pominięte lub wartość NULL, nie można pobrać atrybutu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli `CSid` zostanie znaleziony, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienie `pdwAttributes` do wartości NULL zapewnia możliwość rozporządza `CSid` bez uzyskiwania dostępu do atrybutu. Należy pamiętać, że ta metoda powinna nie używany do sprawdzania praw dostępu jako niepoprawne wyniki może wystąpić w systemie Windows 2000. Zamiast tego należy użyć aplikacji [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) metody.  
  
##  <a name="operator_eq"></a>CTokenGroups::operator =  
 Operator przypisania.  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenGroups` Obiektu lub [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury można przypisać do `CTokenGroups` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CTokenGroups` obiektu.  
  
##  <a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *  
 Rzutuje wartość na wskaźnik do **TOKEN_GROUPS** struktury.  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>Uwagi  
 Rzutuje wartość na wskaźnik do [TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [Klasa CSid](../../atl/reference/csid-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
