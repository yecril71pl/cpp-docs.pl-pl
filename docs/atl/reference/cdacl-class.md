---
title: Klasa CDacl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2724eebd218cea2795d483351ef91b34c9f1bf39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cdacl-class"></a>Klasa CDacl
Ta klasa jest otoki dla struktury DACL (listy DACL kontroli dostępu).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|Konstruktor.|  
|[CDacl:: ~ CDacl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|Dodaje wpis ACE dozwolonych (wpisu kontroli dostępu) do `CDacl` obiektu.|  
|[CDacl::AddDeniedAce](#adddeniedace)|Dodaje odmowy ACE `CDacl` obiektu.|  
|[CDacl::GetAceCount](#getacecount)|Zwraca liczbę ACE (wpisy kontroli dostępu) w `CDacl` obiektu.|  
|[CDacl::RemoveAce](#removeace)|Usuwa określone ACE (wpis kontroli dostępu) `CDacl` obiektu.|  
|[CDacl::RemoveAllAces](#removeallaces)|Usuwa wszystkie wpisy kontroli dostępu zawarte w `CDacl` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt deskryptora zabezpieczeń może zawierać lista DACL dotycząca. Lista DACL dotycząca zawiera zero lub więcej ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Jeśli lista DACL dotycząca jest pusta (to znaczy nie zawiera zero ACE), bez dostępu ma jawnie przyznane uprawnienia, aby jawnie odmówiono dostępu. Jednak jeśli deskryptora zabezpieczeń obiektu nie ma listy DACL, obiekt nie jest chroniony i każdy ma pełny dostęp.  
  
 Aby uzyskać dostęp do POUFNEJ, możesz muszą być właściciela obiektu lub READ_CONTROL dostępu do tego obiektu. Aby zmienić POUFNEJ, musi mieć WRITE_DAC dostępu do tego obiektu.  
  
 Użycie metod klasy do tworzenia, dodawania, usuwania i Usuń wpisy kontroli dostępu z `CDacl` obiektu. Zobacz też [AtlGetDacl](security-global-functions.md#atlgetdacl) i [AtlSetDacl](security-global-functions.md#atlsetdacl).  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="addallowedace"></a>  CDacl::AddAllowedAce  
 Dodaje wpis ACE dozwolonych (wpisu kontroli dostępu) do `CDacl` obiektu.  
  
```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md) obiektu.  
  
 `AccessMask`  
 Określa maski praw dostępu mogą być dla określonego `CSid` obiektu.  
  
 `AceFlags`  
 Zestaw z bitowego flagi dziedziczenia ACE tego formantu.  
  
 `pObjectType`  
 Typ obiektu.  
  
 `pInheritedObjectType`  
 Typ obiektu dziedziczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli wpisu ACE jest dodawany do `CDacl` obiektu **false** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 A `CDacl` obiekt zawiera zero lub więcej ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Ta metoda dodaje wpisu kontroli dostępu, która umożliwia dostęp do `CDacl` obiektu.  
  
 Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) opis różnych flagi, które można ustawić w `AceFlags` parametru.  
  
##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce  
 Dodaje odmowy ACE (wpis kontroli dostępu) do `CDacl` obiektu.  
  
```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 A `CSid` obiektu.  
  
 `AccessMask`  
 Określa maskę odmawiania praw dostępu dla określonego `CSid` obiektu.  
  
 `AceFlags`  
 Zestaw z bitowego flagi dziedziczenia ACE tego formantu. Wartość domyślna to 0 z pierwszego formularza metody.  
  
 `pObjectType`  
 Typ obiektu.  
  
 `pInheritedObjectType`  
 Typ obiektu dziedziczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli wpisu ACE jest dodawany do `CDacl` obiektu **false** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 A `CDacl` obiekt zawiera zero lub więcej ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Ta metoda dodaje wpisu kontroli dostępu, która odmawia dostępu `CDacl` obiektu.  
  
 Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) opis różnych flagi, które można ustawić w `AceFlags` parametru.  
  
##  <a name="cdacl"></a>  CDacl::CDacl  
 Konstruktor.  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Istniejące **ACL** struktury (lista kontroli dostępu).  
  
### <a name="remarks"></a>Uwagi  
 `CDacl` Obiektu można opcjonalnie utworzyć przy użyciu istniejącego **ACL** struktury. Należy pamiętać, aby tylko DACL (listy DACL kontroli dostępu), a nie listę kontroli dostępu (listy kontroli dostępu system), powinien zostać przekazany jako parametr. W kompilacjach do debugowania przekazywanie SACL spowoduje potwierdzenia. W kompilacjach wydania przekazywanie SACL spowoduje, że wpisy kontroli dostępu (wpisy kontroli dostępu) na liście ACL mają być ignorowane, a błąd nie nastąpi.  
  
##  <a name="dtor"></a>  CDacl:: ~ CDacl  
 Destruktor.  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie zasoby uzyskaną przez obiekt, w tym wszystkie wpisy kontroli dostępu (wpisy kontroli dostępu) przy użyciu [CDacl::RemoveAllAces](#removeallaces).  
  
##  <a name="getacecount"></a>  CDacl::GetAceCount  
 Zwraca liczbę ACE (wpisy kontroli dostępu) w `CDacl` obiektu.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę ACE zawarte w `CDacl` obiektu.  
  
##  <a name="operator_eq"></a>  CDacl::operator =  
 Operator przypisania.  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Listy kontroli dostępu (listy kontroli dostępu) można przypisać do istniejącego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do zaktualizowanego `CDacl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, tylko przekazać DACL (listy DACL kontroli dostępu) do tej funkcji. Przekazywanie SACL (systemowa lista kontroli dostępu) do tej funkcji spowoduje, że ASSERT w kompilacjach debugowania, ale spowoduje, że żaden błąd w kompilacjach wydania.  
  
##  <a name="removeace"></a>  CDacl::RemoveAce  
 Usuwa określone ACE (wpis kontroli dostępu) `CDacl` obiektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wpisu ACE do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest określana na podstawie [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>  CDacl::RemoveAllAces  
 Usuwa wszystkie wpisy kontroli dostępu (wpisy kontroli dostępu) zawartych w `CDacl` obiektu.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa co **ACE** (wpisu kontroli dostępu) struktury (jeśli istnieją) w `CDacl` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [Klasa CAcl](../../atl/reference/cacl-class.md)   
 [Listy kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
