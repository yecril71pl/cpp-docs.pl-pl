---
title: Klasa CTokenPrivileges | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs: C++
helpviewer_keywords: CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b6a7d1c76b9ddb0aa555e8856f26da99611f553
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ctokenprivileges-class"></a>Klasa CTokenPrivileges
Ta klasa jest otoki dla **TOKEN_PRIVILEGES** struktury.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Konstruktor.|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|Dodaje co najmniej uprawnienia do `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::Delete](#delete)|Usuwa uprawnień z `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::DeleteAll](#deleteall)|Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetCount](#getcount)|Zwraca liczbę wpisów uprawnień w `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Pobiera wyświetlane nazwy uprawnienia zawarte w `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetLength](#getlength)|Zwraca rozmiar buforu w bajtach do przeprowadzenia **TOKEN_PRIVILEGES** struktura jest reprezentowana przez `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Pobiera lokalnie unikatowe identyfikatory (LUID) i flagi atrybutów z `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Pobiera nazwy uprawnień i flagi atrybutów z `CTokenPrivileges` obiektu.|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Zwraca wskaźnik do **TOKEN_PRIVILEGES** struktury.|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Pobiera atrybut skojarzony z nazwą danego uprawnienia.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Rzutuje wartość na wskaźnik do **TOKEN_PRIVILEGES** struktury.|  
|[CTokenPrivileges::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 [Token dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909) jest obiekt, który opisuje kontekst zabezpieczeń proces lub Wątek i jest przydzielana każdy użytkownik zalogowany do systemu Windows NT lub Windows 2000.  
  
 Token dostępu jest używany do opisania różnych zabezpieczeń przyznane następujące uprawnienia do poszczególnych użytkowników. Uprawnienie składa się z liczbą 64-bitowe o nazwie lokalnie unikatowy identyfikator ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) i ciągu deskryptora.  
  
 `CTokenPrivileges` Klasy jest otoki dla [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury i zawiera 0 lub więcej uprawnień. Można dodać uprawnienia, usunięte lub, którego dotyczy kwerenda przy użyciu metod klasy dostarczony.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="add"></a>CTokenPrivileges::Add  
 Dodaje co najmniej uprawnienia do `CTokenPrivileges` obiektu tokenu dostępu.  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Wskaźnik do zerem ciąg określający nazwę uprawnienia, zgodnie z definicją w WINNT. Plik nagłówka H.  
  
 `bEnable`  
 Jeśli PRAWDA, uprawnienie jest włączone. W przypadku wartości FAŁSZ uprawnienie jest wyłączone.  
  
 `rPrivileges`  
 Odwołanie do [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury. Uprawnienia i atrybuty zostaną skopiowane z tej struktury i dodane do `CTokenPrivileges` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy formularz ta metoda zwraca wartość true, jeśli uprawnienia zostały pomyślnie dodany, wartość false w przeciwnym razie wartość.  
  
##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges  
 Konstruktor.  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenPrivileges` Obiektu można przypisać do nowego obiektu.  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury można przypisać do nowego `CTokenPrivileges` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CTokenPrivileges` Można opcjonalnie można utworzyć obiektu przy użyciu **TOKEN_PRIVILEGES** struktury lub wcześniej zdefiniowanego `CTokenPrivileges` obiektu.  
  
##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges  
 Destruktor.  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="delete"></a>CTokenPrivileges::Delete  
 Usuwa uprawnień z `CTokenPrivileges` obiektu tokenu dostępu.  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Wskaźnik do zerem ciąg określający nazwę uprawnienia, zgodnie z definicją w WINNT. Plik nagłówka H. Na przykład ten parametr może określić stała SE_SECURITY_NAME lub jej odpowiedni ciąg "SeSecurityPrivilege."  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli uprawnienie zostało pomyślnie usunięte, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest przydatna jako narzędzie do tworzenia tokenów ograniczone przez system Windows 2000.  
  
##  <a name="deleteall"></a>CTokenPrivileges::DeleteAll  
 Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu tokenu dostępu.  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie uprawnienia zawarte w `CTokenPrivileges` obiektu tokenu dostępu.  
  
##  <a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames  
 Pobiera wyświetlane nazwy uprawnienia zawarte w `CTokenPrivileges` obiektu tokenu dostępu.  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisplayNames`  
 Wskaźnik do tablicy `CString` obiektów. **CNAME** jest zdefiniowany jako typedef: **CTokenPrivileges::CAtlArray\<cstring — >**.  
  
### <a name="remarks"></a>Uwagi  
 Parametr `pDisplayNames` wskaźnika do tablicy `CString` obiektów, które otrzymają nazwy wyświetlane odpowiadający uprawnienia zawarte w `CTokenPrivileges` obiektu. Ta metoda pobiera nazwy wyświetlane tylko w przypadku uprawnienia określone w sekcji uprawnienia zdefiniowane dla Windows NT. H.  
  
 Ta metoda pobiera nazwy wyświetlanej: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, jego nazwa jest "Wymuszanie zamknięcia systemu z systemu zdalnego". Aby uzyskać nazwę systemu, należy użyć [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).  
  
##  <a name="getcount"></a>CTokenPrivileges::GetCount  
 Zwraca liczbę wpisów uprawnień w `CTokenPrivileges` obiektu.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę uprawnienia zawarte w `CTokenPrivileges` obiektu.  
  
##  <a name="getlength"></a>CTokenPrivileges::GetLength  
 Zwraca długość `CTokenPrivileges` obiektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę bajtów wymaganą do przechowywania **TOKEN_PRIVILEGES** struktura jest reprezentowana przez `CTokenPrivileges` obiektu, w tym wszystkie wpisy uprawnień zawiera.  
  
##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes  
 Pobiera lokalnie unikatowe identyfikatory (LUID) i flagi atrybutów z `CTokenPrivileges` obiektu.  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pPrivileges`  
 Wskaźnik do tablicy [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) obiektów. **CLUIDArray** jako element typedef jest zdefiniowany jako **CAtlArray\<LUID > CLUIDArray**.  
  
 `pAttributes`  
 Wskaźnik do tablicy obiektów typu DWORD. Jeśli ten parametr jest pominięty, lub wartość NULL, atrybuty nie są pobierane. **CAttributes** jako element typedef jest zdefiniowany jako **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyliczenie wszystkich uprawnień zawarte w `CTokenPrivileges` uzyskać dostępu do obiektu tokenu i umieszczenie poszczególnych LUID i (opcjonalnie) flagi atrybutów w tablicy obiektów.  
  
##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes  
 Pobiera nazwę i atrybut flagi z `CTokenPrivileges` obiektu.  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pNames*  
 Wskaźnik do tablicy `CString` obiektów. **CNAME** jako element typedef jest zdefiniowany jako **CAtlArray \<cstring — > CNAME**.  
  
 `pAttributes`  
 Wskaźnik do tablicy obiektów typu DWORD. Jeśli ten parametr jest pominięty, lub wartość NULL, atrybuty nie są pobierane. **CAttributes** jako element typedef jest zdefiniowany jako **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyliczenie wszystkich uprawnień zawarte w `CTokenPrivileges` obiektu umieszczanie nazwy i (opcjonalnie) flagi atrybutów w tablicy obiektów.  
  
 Ta metoda pobiera nazwę atrybutu, a nie nazwy wyświetlanej: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, nazwa systemowa jest "SeRemoteShutdownPrivilege w odniesieniu." Aby uzyskać jego nazwa, należy użyć metody [CTokenPrivileges::GetDisplayNames](#getdisplaynames).  
  
##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 Zwraca wskaźnik do **TOKEN_PRIVILEGES** struktury.  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury.  
  
##  <a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege  
 Pobiera atrybut skojarzony z nazwą danego uprawnienia.  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Wskaźnik do zerem ciąg określający nazwę uprawnienia, zgodnie z definicją w WINNT. Plik nagłówka H. Na przykład ten parametr może określić stała SE_SECURITY_NAME lub jej odpowiedni ciąg "SeSecurityPrivilege."  
  
 `pdwAttributes`  
 Wskaźnik do zmiennej, która odbiera atrybutów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli atrybut pomyślnie pobrać, wartość false w przeciwnym razie wartość.  
  
##  <a name="operator_eq"></a>CTokenPrivileges::operator =  
 Operator przypisania.  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury można przypisać do `CTokenPrivileges` obiektu.  
  
 `rhs`  
 `CTokenPrivileges` Obiektu można przypisać do obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CTokenPrivileges` obiektu.  
  
##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 Rzutuje wartość na wskaźnik do **TOKEN_PRIVILEGES** struktury.  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>Uwagi  
 Rzutuje wartość na wskaźnik do [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [IDENTYFIKATOR LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
