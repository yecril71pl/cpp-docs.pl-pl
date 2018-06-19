---
title: Klasa CSid | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed55fd2286c3d6e37b59b16a06f43cc4efe55091
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366409"
---
# <a name="csid-class"></a>Klasa CSid
Ta klasa jest otoki dla `SID` struktury (identyfikator zabezpieczeń).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CSid
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|Tablica `CSid` obiektów.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSid::CSid](#csid)|Konstruktor.|  
|[CSid:: ~ CSid](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|Zwraca nazwę konta skojarzonego z `CSid` obiektu.|  
|[CSid::Domain](#domain)|Zwraca nazwę domeny skojarzone z `CSid` obiektu.|  
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` prefiksy (identyfikator zabezpieczeń) pod kątem równości.|  
|[CSid::GetLength](#getlength)|Zwraca długość `CSid` obiektu.|  
|[CSid::GetPSID](#getpsid)|Zwraca wskaźnik do `SID` struktury.|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Zwraca wskaźnik do **SID_IDENTIFIER_AUTHORITY** struktury.|  
|[CSid::GetSubAuthority](#getsubauthority)|Zwraca określony podrzędna w **SID** struktury.|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Zwraca liczbę podrzędna.|  
|[CSid::IsValid](#isvalid)|Testy `CSid` obiektu ważności.|  
|[CSid::LoadAccount](#loadaccount)|Aktualizacje `CSid` daną nazwę konta i domeny lub istniejący obiekt `SID` struktury.|  
|[CSid::Sid](#sid)|Zwraca ciąg Identyfikatora.|  
|[CSid::SidNameUse](#sidnameuse)|Zwraca opis stanu `CSid` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Operator przypisania.|  
|[Operator const SID *](#operator_const_sid__star)|Rzutowania `CSid` obiektu na wskaźnik do `SID` struktury.|  
  
### <a name="global-operators"></a>Operatorów globalnych  
  
|||  
|-|-|  
|[operator ==](#operator_eq_eq)|Dwa obiekty deskryptora zabezpieczeń dla równości testów|  
|[operator! =](#operator_neq)|Dwa obiekty deskryptora zabezpieczeń dla nierówności testów|  
|[Operator \<](#operator_lt_)|Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.|  
|[operator >](#operator_gt_)|Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.|  
|[Operator \<=](#operator_lt__eq)|Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.|  
|[operator > =](#operator_gt__eq)|Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.|  
  
## <a name="remarks"></a>Uwagi  
 `SID` Struktury jest strukturą danych o zmiennej długości, używany do jednoznacznego identyfikowania użytkowników lub grup.  
  
 Aplikacje nie należy modyfikować `SID` struktury bezpośrednio, ale zamiast tego użyj metody dostarczone w tej klasy otoki. Zobacz też [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), i [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="accountname"></a>  CSid::AccountName  
 Zwraca nazwę konta skojarzonego z `CSid` obiektu.  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `LPCTSTR` wskazuje nazwę konta.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda próbuje znaleźć nazwy dla określonego `SID` (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Jeśli nie nazwy konta dla `SID` można znaleźć `AccountName` zwraca pusty ciąg. Może to wystąpić, jeśli limit czasu sieci uniemożliwia znajdowanie nazwę tej metody. Występuje również w przypadku identyfikatorów zabezpieczeń bez odpowiedniej nazwy konta, takich jak logowanie `SID` identyfikującym sesji logowania.  
  
##  <a name="csid"></a>  CSid::CSid  
 Konstruktor.  
  
```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Istniejące `CSid` obiektu lub `SID` struktury (identyfikator zabezpieczeń).  
  
 *IdentifierAuthority*  
 Urząd.  
  
 *nSubAuthorityCount*  
 Liczba podrzędna.  
  
 `pszAccountName`  
 Nazwa konta.  
  
 `pszSystem`  
 Nazwa systemowa. Ten ciąg może być nazwa komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast tego użyć systemu lokalnego.  
  
 `pSid`  
 Wskaźnik do `SID` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor inicjuje `CSid` obiektu, ustawienie dla elementu członkowskiego danych wewnętrznych *SidTypeInvalid*, lub skopiować ustawienia z istniejącego `CSid`, `SID`, lub istniejącego konta.  
  
 Jeśli inicjowanie zakończy się niepowodzeniem, spowoduje zgłoszenie konstruktora [CAtlException klasy](../../atl/reference/catlexception-class.md).  
  
##  <a name="dtor"></a>  CSid:: ~ CSid  
 Destruktor.  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie zasoby uzyskaną przez obiekt.  
  
##  <a name="csidarray"></a>  CSid::CSidArray  
 Tablica [CSid](../../atl/reference/csid-class.md) obiektów.  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element typedef Określa typ tablicy, która może służyć do pobierania identyfikatorów zabezpieczeń z listy kontroli dostępu (listy kontroli dostępu). Zobacz [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).  
  
##  <a name="domain"></a>  CSid::Domain  
 Zwraca nazwę domeny skojarzone z `CSid` obiektu.  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `LPCTSTR` wskazanie do domeny.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda próbuje znaleźć nazwy dla określonego `SID` (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Jeśli nie nazwy konta dla `SID` można znaleźć **domeny** zwraca domeny w postaci pustego ciągu. Może to wystąpić, jeśli limit czasu sieci uniemożliwia znajdowanie nazwę tej metody. Występuje również w przypadku identyfikatorów zabezpieczeń bez odpowiedniej nazwy konta, takich jak logowanie `SID` identyfikującym sesji logowania.  
  
##  <a name="equalprefix"></a>  CSid::EqualPrefix  
 Testy `SID` prefiksy (identyfikator zabezpieczeń) pod kątem równości.  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `SID` Struktury (identyfikator zabezpieczeń) lub `CSid` obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia **false** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
##  <a name="getlength"></a>  CSid::GetLength  
 Zwraca długość `CSid` obiektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca długość w bajtach `CSid` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CSid` struktura jest nieprawidłowa, zwracana wartość jest niezdefiniowana. Przed wywołaniem `GetLength`, użyj [CSid::IsValid](#isvalid) funkcji członkowskiej, aby sprawdzić, czy `CSid` jest nieprawidłowy.  
  
> [!NOTE]
>  W kompilacjach debugowania funkcji spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.  
  
##  <a name="getpsid"></a>  CSid::GetPSID  
 Zwraca wskaźnik do `SID` struktury (identyfikator zabezpieczeń).  
  
```
const SID* GetPSID() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca adres `CSid` podstawowej obiektu `SID` struktury.  
  
##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY  
 Zwraca wskaźnik do **SID_IDENTIFIER_AUTHORITY** struktury.  
  
```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca adres **SID_IDENTIFIER_AUTHORITY** struktury. W przypadku niepowodzenia zwracane wartości są niezdefiniowane. Błąd może wystąpić, jeśli `CSid` obiekt nie jest prawidłowa, w którym to przypadku [CSid::IsValid](#isvalid) metoda zwraca **false**. Funkcja `GetLastError` można wywołać dla rozszerzonych informacji o błędzie.  
  
> [!NOTE]
>  W kompilacjach debugowania funkcji spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.  
  
##  <a name="getsubauthority"></a>  CSid::GetSubAuthority  
 Zwraca określony podrzędna w `SID` struktury (identyfikator zabezpieczeń).  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nSubAuthority*  
 Podrzędna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca podrzędna odwołuje się *nSubAuthority.* Wartość podrzędna jest identyfikatora względnego (RID).  
  
### <a name="remarks"></a>Uwagi  
 *NSubAuthority* parametr określa wartość indeksu identyfikowanie podrzędna elementu tablicy, który zwróci metoda. Metoda wykonuje żadne testy weryfikacyjne na tę wartość. Aplikacja może wywołać [CSid::GetSubAuthorityCount](#getsubauthoritycount) odnajdywania zakresu akceptowalnych właściwości.  
  
> [!NOTE]
>  W kompilacjach debugowania funkcji spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.  
  
##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount  
 Zwraca liczbę podrzędna.  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest liczba podrzędna.  
  
 Jeśli metoda nie powiedzie się, wartość zwracana jest niezdefiniowany. Metoda kończy się niepowodzeniem, jeśli `CSid` obiektu jest nieprawidłowy. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.  
  
> [!NOTE]
>  W kompilacjach debugowania funkcji spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.  
  
##  <a name="isvalid"></a>  CSid::IsValid  
 Testy `CSid` obiektu ważności.  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli `CSid` obiekt jest prawidłowy, **false** , jeśli nie. Nie ma żadnych informacji błąd rozszerzony dla tej metody; Nie wywołuj `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 `IsValid` Metoda sprawdza `CSid` obiektu upewniając się, że numer poprawki znajduje się w zakresie znane i liczba subauthorities jest mniejsza niż maksymalna.  
  
##  <a name="loadaccount"></a>  CSid::LoadAccount  
 Aktualizacje `CSid` obiektu daną nazwę konta i domeny lub istniejącej struktury identyfikatora SID (identyfikator zabezpieczeń).  
  
```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszAccountName`  
 Nazwa konta.  
  
 `pszSystem`  
 Nazwa systemowa. Ten ciąg może być nazwa komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast tego użyć systemu lokalnego.  
  
 `pSid`  
 Wskaźnik do [SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia **false** w przypadku awarii. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 `LoadAccount` próbuje znaleźć identyfikatora zabezpieczeń dla określonej nazwy. Zobacz [LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx) więcej szczegółów.  
  
##  <a name="operator_eq"></a>  CSid::operator =  
 Operator przypisania.  
  
```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` do przypisania do `CSid` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do zaktualizowanego `CSid` obiektu.  
  
##  <a name="operator_eq_eq"></a>  CSid::operator ==  
 Testy dwa obiekty deskryptora zabezpieczeń pod kątem równości.  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie == — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części == — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** deskryptorów zabezpieczeń są równe, w przeciwnym razie **false**.  
  
##  <a name="operator_neq"></a>  CSid::operator! =  
 Testy dwa obiekty deskryptora zabezpieczeń dla nierówności.  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie! = — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części! = — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** deskryptorów zabezpieczeń nie są równe, w przeciwnym razie **false**.  
  
##  <a name="operator_lt"></a>  CSid::operator &lt;  
 Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie! = — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części! = — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `lhs` jest mniejsza niż `rhs`, w przeciwnym razie **false**.  
  
##  <a name="operator_lt__eq"></a>  CSid::operator &lt;=  
 Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie! = — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części! = — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `lhs` jest mniejsza niż lub równa `rhs`, w przeciwnym razie **false**.  
  
##  <a name="operator_gt"></a>  CSid::operator &gt;  
 Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie! = — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części! = — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `lhs` jest większa niż `rhs`, w przeciwnym razie **false**.  
  
##  <a name="operator_gt__eq"></a>  CSid::operator &gt;=  
 Porównuje wartości względnej dwóch obiektów deskryptora zabezpieczeń.  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie! = — operator.  
  
 `rhs`  
 `SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w prawej części! = — operator.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `lhs` jest większa niż lub równa `rhs`, w przeciwnym razie **false**.  
  
##  <a name="operator_const_sid__star"></a>  CSid::operator const SID *  
 Rzutowania `CSid` obiektu na wskaźnik do `SID` struktury (identyfikator zabezpieczeń).  
  
```  
operator const SID *() const throw(...);
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca adres `SID` struktury.  
  
##  <a name="sid"></a>  CSid::Sid  
 Zwraca `SID` struktury (identyfikator zabezpieczeń) jako ciąg.  
  
```
LPCTSTR Sid() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `SID` struktury jako ciąg w formacie odpowiednie do wyświetlania, gromadzenia i przekazywania. Odpowiednikiem [ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399).  
  
##  <a name="sidnameuse"></a>  CSid::SidNameUse  
 Zwraca opis stanu `CSid` obiektu.  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość elementu członkowskiego danych przechowujący wartość opisującym `CSid` obiektu.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SidTypeUser|Wskazuje użytkownika `SID` (identyfikator zabezpieczeń).|  
|SidTypeGroup|Wskazuje grupę `SID`.|  
|SidTypeDomain|Wskazuje domeny `SID`.|  
|SidTypeAlias|Wskazuje alias `SID`.|  
|SidTypeWellKnownGroup|Wskazuje `SID` dla dobrze znana grupa.|  
|SidTypeDeletedAccount|Wskazuje `SID` dla usuniętego konta.|  
|SidTypeInvalid|Wskazuje nieprawidłową `SID`.|  
|SidTypeUnknown|Wskazuje nieznany `SID` typu.|  
|SidTypeComputer|Wskazuje `SID` dla komputera.|  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CSid::LoadAccount](#loadaccount) zaktualizować `CSid` obiekt przed wywołaniem `SidNameUse` do zwrócenia stanu. `SidNameUse` nie zmienia stanu obiektu (przez wywołanie do **LookupAccountName** lub **LookupAccountSid**), ale zwraca tylko bieżący stan.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)   
 [Operatory](../../atl/reference/atl-operators.md)
