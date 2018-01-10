---
title: Klasa CAcl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
dev_langs: C++
helpviewer_keywords: CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd3b17c3cf74e87b709353a8dd2cd00c5355c7fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cacl-class"></a>Klasa CAcl
Ta klasa jest otoki dla `ACL` struktury (lista kontroli dostępu).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAcl
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Tablica `ACCESS_MASK`s.|  
|[CAcl::CAceFlagArray](#caceflagarray)|Tablica `BYTE`s.|  
|[CAcl::CAceTypeArray](#cacetypearray)|Tablica `BYTE`s.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAcl::CAcl](#cacl)|Konstruktor.|  
|[CAcl:: ~ CAcl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAcl::GetAceCount](#getacecount)|Zwraca liczbę kontroli dostępu do obiektów wpisu.|  
|[CAcl::GetAclEntries](#getaclentries)|Pobiera wpisów kontroli dostępu listę kontroli dostępu (ACL) z `CAcl` obiektu.|  
|[CAcl::GetAclEntry](#getaclentry)|Pobiera wszystkie informacje o wpis w `CAcl` obiektu.|  
|[CAcl::GetLength](#getlength)|Zwraca długość listy kontroli dostępu.|  
|[CAcl::GetPACL](#getpacl)|Zwraca PACL (wskaźnik do listy ACL).|  
|[CAcl::IsEmpty](#isempty)|Testy `CAcl` obiektu wpisy.|  
|[CAcl::IsNull](#isnull)|Zwraca stan `CAcl` obiektu.|  
|[CAcl::RemoveAce](#removeace)|Usuwa określone ACE (wpis kontroli dostępu) `CAcl` obiektu.|  
|[CAcl::RemoveAces](#removeaces)|Usuwa wszystkie wpisy kontroli dostępu (wpisy kontroli dostępu) `CAcl` przeznaczonych do danej `CSid`.|  
|[CAcl::SetEmpty](#setempty)|Znaczniki `CAcl` obiekt jako pusta.|  
|[CAcl::SetNull](#setnull)|Znaczniki `CAcl` obiekt jako `NULL`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAcl::operator const ACL *](#operator_const_acl__star)|Rzutowania `CAcl` do obiektu `ACL` struktury.|  
|[CAcl::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 **ACL** struktura jest nagłówka listy kontroli dostępu (listy kontroli dostępu). Listy ACL zawiera listę sekwencyjnych zero lub więcej [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868) (wpisy kontroli dostępu). Poszczególne wpisy kontroli dostępu na liście ACL są ponumerowane od 0 do *n-1*, gdzie  *n*  jest liczba wpisów na liście ACL. Podczas edytowania listy ACL, aplikacja odwołuje się do wpisu kontroli dostępu (ACE) w obrębie listy ACL według indeksu.  
  
 Istnieją dwa typy listy ACL:  
  
-   DACL  
  
-   System  
  
 LISTY DACL jest kontrolowana przez właściciela obiektu lub wszystkich przyznane **WRITE_DAC** dostępu do tego obiektu. Określa dostęp do określonych użytkowników i grup, które mogą mieć do obiektu. Na przykład właściciela pliku można użyć listy DACL do formantu, którzy użytkownicy i grupy mogą i nie może mieć dostęp do pliku.  
  
 Obiekt może być również zabezpieczenia na poziomie systemu informacje skojarzone z nią w formularzu systemu ACL kontrolowane przez administratora systemu. Listy ACL systemu umożliwia administratorowi systemu inspekcji, wszelkie próby uzyskania dostępu do obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) dyskusji w zestawie Windows SDK.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray  
 Tablica obiektów ACCESS_MASK.  
  
```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element typedef Określa typ tablicy, która może służyć do przechowywania praw dostępu używany w wpisów kontroli dostępu (ACE).  
  
##  <a name="caceflagarray"></a>CAcl::CAceFlagArray  
 Tablica bajtów.  
  
```
typedef CAtlArray<BYTE> CAceFlagArray;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element typedef Określa typ tablicy używane do definiowania flagi kontrolne określonego typu wpisu kontroli dostępu. Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definicji Pełna lista możliwości flagi.  
  
##  <a name="cacetypearray"></a>CAcl::CAceTypeArray  
 Tablica bajtów.  
  
```
typedef CAtlArray<BYTE> CAceTypeArray;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element typedef Określa używany do definiowania rodzaj obiektów wpisu kontroli dostępu, takich jak ACCESS_ALLOWED_ACE_TYPE lub ACCESS_DENIED_ACE_TYPE typu tablicy. Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) definicji, aby uzyskać pełną listę możliwych typów.  
  
##  <a name="cacl"></a>CAcl::CAcl  
 Konstruktor.  
  
```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Istniejące `CAcl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CAcl` Obiektu można opcjonalnie utworzyć przy użyciu istniejącego `CAcl` obiektu.  
  
##  <a name="dtor"></a>CAcl:: ~ CAcl  
 Destruktor.  
  
```
virtual ~CAcl() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie zasoby uzyskaną przez obiekt.  
  
##  <a name="getacecount"></a>CAcl::GetAceCount  
 Zwraca liczbę kontroli dostępu do obiektów wpisu.  
  
```
virtual UINT GetAceCount() const throw() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wpisów ACE w `CAcl` obiektu.  
  
##  <a name="getaclentries"></a>CAcl::GetAclEntries  
 Pobiera wpisów kontroli dostępu listę kontroli dostępu (ACL) z `CAcl` obiektu.  
  
```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSids`  
 Wskaźnik do tablicy [CSid](../../atl/reference/csid-class.md) obiektów.  
  
 *pAccessMasks*  
 Maski dostępu.  
  
 *pAceTypes*  
 Wpisu kontroli dostępu ( **ACE**) typów.  
  
 *pAceFlags*  
 **ACE** flagi.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wypełnia tablicy parametrów szczegółowe informacje o każdym **ACE** obiektów zawartych w `CAcl` obiektu. Użyj wartości NULL, gdy szczegóły dla tego konkretnego tablicy nie są wymagane.  
  
 Zawartość każdej macierzy zgodne ze sobą, oznacza to, pierwszy element `CAccessMaskArray` odpowiada pierwszy element w tablicy `CSidArray` tablicy i tak dalej.  
  
 Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) szczegółowe na typach ACE i flagi.  
  
##  <a name="getaclentry"></a>CAcl::GetAclEntry  
 Pobiera wszystkie informacje o wpis na liście kontroli dostępu (ACL).  
  
```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wpisu listy kontroli dostępu do pobrania.  
  
 `pSid`  
 [CSid](../../atl/reference/csid-class.md) obiekt, którego dotyczy wpisu na liście ACL.  
  
 *pMask*  
 Maska określanie uprawnień, aby udzielić lub odmówić dostępu.  
  
 `pType`  
 Typ wpisu kontroli dostępu.  
  
 `pFlags`  
 Flagi ACE.  
  
 `pObjectType`  
 Typ obiektu. Spowoduje to ustawienie do GUID_NULL czy typ obiektu nie została określona w asa, czy wpisu kontroli dostępu nie jest ACE obiektu.  
  
 `pInheritedObjectType`  
 Typ obiektu dziedziczone. Spowoduje to ustawienie do GUID_NULL czy typ dziedziczony obiektu nie została określona w asa, czy wpisu kontroli dostępu nie jest ACE obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera wszystkie informacje o poszczególnych ACE informacjami więcej niż [CAcl::GetAclEntries](#getaclentries) samodzielnie udostępnia.  
  
 Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) szczegółowe na typach ACE i flagi.  
  
##  <a name="getlength"></a>CAcl::GetLength  
 Zwraca długość listy kontroli dostępu (ACL).  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wymaganą długość w bajtach niezbędne do przechowywania **ACL** struktury.  
  
##  <a name="getpacl"></a>CAcl::GetPACL  
 Zwraca wskaźnik do listy kontroli dostępu (ACL).  
  
```
const ACL* GetPACL() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do **ACL** struktury.  
  
##  <a name="isempty"></a>CAcl::IsEmpty  
 Testy `CAcl` obiektu wpisy.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** Jeśli `CAcl` obiekt nie ma wartości NULL i nie ma żadnych członków. Zwraca **false** Jeśli `CAcl` obiektu ma wartość NULL lub zawiera co najmniej jeden wpis.  
  
##  <a name="isnull"></a>CAcl::IsNull  
 Zwraca stan `CAcl` obiektu.  
  
```
bool IsNull() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli `CAcl` obiektu ma wartość NULL, **false** inaczej.  
  
##  <a name="operator_const_acl__star"></a>CAcl::operator const ACL *  
 Rzutowania `CAcl` do obiektu **ACL** struktury (lista kontroli dostępu).  
  
```  
operator const ACL *() const throw(...);
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca adres **ACL** struktury.  
  
##  <a name="operator_eq"></a>CAcl::operator =  
 Operator przypisania.  
  
```
CAcl& operator= (const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CAcl` Można przypisać do istniejącego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do zaktualizowanego `CAcl` obiektu.  
  
##  <a name="removeace"></a>CAcl::RemoveAce  
 Usuwa określone ACE (wpis kontroli dostępu) **CAcl** obiektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wpisu ACE do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest określana na podstawie [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeaces"></a>CAcl::RemoveAces  
 Usuwa wszystkim ACE (wpisy kontroli dostępu) `CAcl` przeznaczonych do danej `CSid`.  
  
```
bool RemoveAces(const CSid& rSid) throw(...)
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 Odwołanie do `CSid` obiektu.  
  
##  <a name="setempty"></a>CAcl::SetEmpty  
 Znaczniki `CAcl` obiekt jako pusta.  
  
```
void SetEmpty() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 `CAcl` Można ustawić pustą lub null: dwa stany są unikatowe.  
  
##  <a name="setnull"></a>CAcl::SetNull  
 Znaczniki `CAcl` obiektu jako wartość NULL.  
  
```
void SetNull() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 `CAcl` Można ustawić pustą lub null: dwa stany są unikatowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
