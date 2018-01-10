---
title: Klasa CSacl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs: C++
helpviewer_keywords: CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 104c189b1f368b42ef1d93496629b4e142e1c938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csacl-class"></a>Klasa CSacl
Ta klasa jest otoki dla struktury SACL (systemowa lista kontroli dostępu).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|Konstruktor.|  
|[CSacl:: ~ CSacl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|Dodaje wpis inspekcji kontroli dostępu (ACE) do `CSacl` obiektu.|  
|[CSacl::GetAceCount](#getacecount)|Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiektu.|  
|[CSacl::RemoveAce](#removeace)|Usuwa określone ACE (wpis kontroli dostępu) **CSacl** obiektu.|  
|[CSacl::RemoveAllAces](#removeallaces)|Usuwa wszystkie wpisy kontroli dostępu zawarte w `CSacl` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 Lista SACL zawiera wpisy kontroli dostępu (ACE), określających typy prób dostępu, które generują rekordów inspekcji w dzienniku zdarzeń zabezpieczeń kontrolera domeny. Należy pamiętać, że Lista SACL generuje wpisy dziennika tylko na kontrolerze domeny, na których nastąpiła próba uzyskania dostępu, a nie na każdym kontrolerze domeny, zawierający repliki obiektu.  
  
 Aby ustawić lub pobrać SACL w deskryptora zabezpieczeń obiektu, uprawnień SE_SECURITY_NAME musi być włączony w wątku żądania tokenu dostępu. Grupa Administratorzy ma to uprawnienie przyznane przez domyślne i może zostać przydzielony do innych użytkowników lub grup. Posiadające uprawnienia przyznane nie jest wymagane jest: Aby można było wykonać operację, zdefiniowane przez uprawnienia, uprawnienie musi być włączony w token dostępu obowiązuje. Model pozwala uprawnienia do można włączyć tylko dla określonego systemu operacji, a następnie wyłączone, gdy nie są już potrzebne. Zobacz [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl) przykłady włączenie SE_SECURITY_NAME.  
  
 Użycie metod klasy do dodawania, usuwania, tworzenie i usuwanie ACE z **SACL** obiektu. Zobacz też [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl).  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="addauditace"></a>CSacl::AddAuditAce  
 Dodaje wpis inspekcji kontroli dostępu (ACE) do `CSacl` obiektu.  
  
```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md) obiektu.  
  
 `AccessMask`  
 Określa maski praw dostępu, które mają podlegać inspekcji dla określonego `CSid` obiektu.  
  
 `bSuccess`  
 Określa, czy przeprowadzać inspekcję prób dozwolonych dostępu. Ustawienia tej flagi na wartość PRAWDA, aby włączyć inspekcję; w przeciwnym wypadku ustaw ją na wartość false.  
  
 *bFailure*  
 Określa, czy przeprowadzać inspekcję prób odmówiono dostępu. Ustawienia tej flagi na wartość PRAWDA, aby włączyć inspekcję; w przeciwnym wypadku ustaw ją na wartość false.  
  
 `AceFlags`  
 Zestaw z bitowego flagi dziedziczenia ACE tego formantu.  
  
 `pObjectType`  
 Typ obiektu.  
  
 `pInheritedObjectType`  
 Typ obiektu dziedziczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli wpisu ACE jest dodawany do `CSacl` obiektu **false** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 A `CSacl` obiekt zawiera wpisy kontroli dostępu (ACE), określających typy prób dostępu, które generują rekordów inspekcji w dzienniku zdarzeń zabezpieczeń. Ta metoda dodaje ACE, aby `CSacl` obiektu. Drugiej formy `AddAuditAce` jest tylko dostępne w systemie Windows 2000 lub nowszej.  
  
 Zobacz [ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919) opis różnych flagi, które można ustawić w `AceFlags` parametru.  
  
##  <a name="csacl"></a>CSacl::CSacl  
 Konstruktor.  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Istniejące **ACL** struktury (lista kontroli dostępu).  
  
### <a name="remarks"></a>Uwagi  
 `CSacl` Obiektu można opcjonalnie utworzyć przy użyciu istniejącego **ACL** struktury. Upewnij się, że ten parametr jest systemowa lista kontroli dostępu (SACL), a nie listy DACL kontroli dostępu (DACL). W kompilacjach debugowania, jeśli podano listy DACL nastąpi potwierdzenia. W kompilacjach wydania wszystkie pozycje z listy DACL są ignorowane.  
  
##  <a name="dtor"></a>CSacl:: ~ CSacl  
 Destruktor.  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie zasoby uzyskaną przez obiekt, w tym wszystkie wpisy kontroli dostępu (ACE).  
  
##  <a name="getacecount"></a>CSacl::GetAceCount  
 Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiektu.  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę ACE zawarte w `CSacl` obiektu.  
  
##  <a name="operator_eq"></a>CSacl::operator =  
 Operator przypisania.  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 **ACL** (lista kontroli dostępu) można przypisać do istniejącego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do zaktualizowanego `CSacl` obiektu. Upewnij się, że **ACL** parametr jest rzeczywiście systemu lista kontroli dostępu (SACL), a nie listy DACL kontroli dostępu (DACL). W kompilacjach debugowania nastąpi potwierdzenia, a w kompilacjach wydania **ACL** parametr zostanie zignorowany.  
  
##  <a name="removeace"></a>CSacl::RemoveAce  
 Usuwa określone ACE (wpis kontroli dostępu) **CSacl** obiektu.  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wpisu ACE do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest określana na podstawie [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).  
  
##  <a name="removeallaces"></a>CSacl::RemoveAllAces  
 Usuwa wszystkie wpisy kontroli dostępu (ACE) zawartych w `CSacl` obiektu.  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa co **ACE** struktury (jeśli istnieją) w `CSacl` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAcl](../../atl/reference/cacl-class.md)   
 [Listy kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
