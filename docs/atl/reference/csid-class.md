---
title: Klasa CSid
ms.date: 03/27/2019
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
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: 4c8d05fd193254f2431bbec7692ff25420c1bf05
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565873"
---
# <a name="csid-class"></a>Klasa CSid

Ta klasa jest otoką `SID` struktury (identyfikator zabezpieczeń).

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CSid
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Tablica `CSid` obiektów.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSid::CSid](#csid)|Konstruktor.|
|[CSid::~CSid](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Zwraca nazwę na koncie skojarzonym z `CSid` obiektu.|
|[CSid::Domain](#domain)|Zwraca nazwę domeny skojarzonej z `CSid` obiektu.|
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` prefiksy (identyfikator zabezpieczeń) pod kątem równości.|
|[CSid::GetLength](#getlength)|Zwraca długość `CSid` obiektu.|
|[CSid::GetPSID](#getpsid)|Zwraca wskaźnik do `SID` struktury.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.|
|[CSid::GetSubAuthority](#getsubauthority)|Zwraca określony podrzędna w `SID` struktury.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Zwraca liczbę podrzędna.|
|[CSid::IsValid](#isvalid)|Testy `CSid` obiektu dla ważności.|
|[CSid::LoadAccount](#loadaccount)|Aktualizacje `CSid` podanej nazwy konta i domeny lub istniejący obiekt `SID` struktury.|
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
|[operator ==](#operator_eq_eq)|Testuje dwa obiekty deskryptora zabezpieczeń pod kątem równości|
|[operator! =](#operator_neq)|Testuje dwa obiekty deskryptora zabezpieczeń pod kątem nierówności|
|[Operator \<](#operator_lt)|Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.|
|[operator >](#operator_gt)|Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.|
|[Operator \<=](#operator_lt__eq)|Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.|
|[operator > =](#operator_gt__eq)|Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.|

## <a name="remarks"></a>Uwagi

`SID` Struktury jest strukturą danych o zmiennej długości, używany do jednoznacznego identyfikowania użytkowników lub grup.

Aplikacje nie należy modyfikować `SID` struktury tego zrobić bezpośrednio, ale zamiast tego należy użyć metod dostarczonych w tej klasy otoki. Zobacz też [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), i [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="accountname"></a>  CSid::AccountName

Zwraca nazwę na koncie skojarzonym z `CSid` obiektu.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazuje nazwę konta.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje odnaleźć nazwy dla określonego `SID` (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Jeśli brak nazwy konta dla `SID` można znaleźć `AccountName` zwraca pusty ciąg. Może to wystąpić, jeśli limit czasu sieci uniemożliwia znajdowanie nazwę tej metody. Wystąpi ona również identyfikatorów zabezpieczeń bez odpowiedniej nazwy konta, takie jak `SID` określający sesji logowania.

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

*RHS*<br/>
Istniejące `CSid` obiektu lub `SID` struktury (identyfikator zabezpieczeń).

*IdentifierAuthority*<br/>
Urząd.

*nSubAuthorityCount*<br/>
Liczba podrzędna.

*pszAccountName*<br/>
Nazwa konta.

*pszSystem*<br/>
Nazwa systemu. Ten ciąg może być nazwa komputera zdalnego. Jeśli ten ciąg ma wartość NULL, używany jest system lokalny.

*pSid*<br/>
Wskaźnik do `SID` struktury.

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje `CSid` obiektu, ustawiając element członkowski danych wewnętrznych na *SidTypeInvalid*, lub przez skopiowanie istniejącego ustawienia `CSid`, `SID`, lub istniejące konto.

Jeśli inicjowanie zakończy się niepowodzeniem, Konstruktor zgłosi [klasa CAtlException](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  CSid:: ~ CSid

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby, uzyskanych przez obiekt.

##  <a name="csidarray"></a>  CSid::CSidArray

Tablica [CSid](../../atl/reference/csid-class.md) obiektów.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef Określa typ tablicy, który może służyć do pobierania identyfikatorów zabezpieczeń z listy ACL (lista kontroli dostępu). Zobacz [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Zwraca nazwę domeny skojarzonej z `CSid` obiektu.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `LPCTSTR` wskazuje do domeny.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje odnaleźć nazwy dla określonego `SID` (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Jeśli brak nazwy konta dla `SID` można znaleźć `Domain` zwraca domeny w postaci pustego ciągu. Może to wystąpić, jeśli limit czasu sieci uniemożliwia znajdowanie nazwę tej metody. Wystąpi ona również identyfikatorów zabezpieczeń bez odpowiedniej nazwy konta, takie jak `SID` określający sesji logowania.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Testy `SID` prefiksy (identyfikator zabezpieczeń) pod kątem równości.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SID` Struktury (identyfikator zabezpieczeń) lub `CSid` obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zobacz [EqualPrefixSid](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) w zestawie Windows SDK, aby uzyskać więcej informacji.

##  <a name="getlength"></a>  CSid::GetLength

Zwraca długość `CSid` obiektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość w bajtach `CSid` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli `CSid` struktura jest nieprawidłowa, zwracana wartość jest niezdefiniowana. Przed wywołaniem `GetLength`, użyj [CSid::IsValid](#isvalid) funkcja elementu członkowskiego, aby sprawdzić, czy `CSid` jest prawidłowy.

> [!NOTE]
>  W obszarze kompilacji do debugowania funkcji spowoduje, że ASERCJA Jeśli `CSid` obiektu jest nieprawidłowy.

##  <a name="getpsid"></a>  CSid::GetPSID

Zwraca wskaźnik do `SID` struktury (identyfikator zabezpieczeń).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres `CSid` podstawowej obiektu `SID` struktury.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest adres `SID_IDENTIFIER_AUTHORITY` struktury. Jeśli nie powiedzie się, wartość zwracana jest niezdefiniowane. Błąd może wystąpić, jeśli `CSid` obiekt nie jest prawidłowa, w którym to przypadku [CSid::IsValid](#isvalid) metoda zwraca wartość FALSE. Funkcja `GetLastError` można wywoływać dla rozszerzonych informacji o błędzie.

> [!NOTE]
>  W obszarze kompilacji do debugowania funkcji spowoduje, że ASERCJA Jeśli `CSid` obiektu jest nieprawidłowy.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Zwraca określony podrzędna w `SID` struktury (identyfikator zabezpieczeń).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAuthority*<br/>
Podrzędna.

### <a name="return-value"></a>Wartość zwracana

Zwraca podrzędna odwołuje się *nSubAuthority.* Wartość podrzędna jest identyfikatora względnego (RID).

### <a name="remarks"></a>Uwagi

*NSubAuthority* parametr określa wartość indeksu, identyfikowanie podrzędna elementu tablicy, który zwróci metoda. Metoda wykonuje żadne testy weryfikacyjne na tę wartość. Aplikacja może wywołać [CSid::GetSubAuthorityCount](#getsubauthoritycount) do zakresu akceptowalnych odnajdywania.

> [!NOTE]
>  W obszarze kompilacji do debugowania funkcji spowoduje, że ASERCJA Jeśli `CSid` obiektu jest nieprawidłowy.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Zwraca liczbę podrzędna.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartość zwracana jest liczba podrzędna.

Jeśli metoda zakończy się niepowodzeniem, zwracana wartość jest niezdefiniowana. Metoda kończy się niepowodzeniem, jeśli `CSid` obiekt jest nieprawidłowy. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.

> [!NOTE]
>  W obszarze kompilacji do debugowania funkcji spowoduje, że ASERCJA Jeśli `CSid` obiektu jest nieprawidłowy.

##  <a name="isvalid"></a>  CSid::IsValid

Testy `CSid` obiektu dla ważności.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli `CSid` obiekt jest prawidłowy, FAŁSZ. Jeśli tak nie jest. Nie ma żadnych rozszerzone informacje o błędzie dla tej metody; Nie wywołuj `GetLastError`.

### <a name="remarks"></a>Uwagi

`IsValid` Metoda sprawdza `CSid` obiektu, sprawdzając, czy numer wersji znajduje się w zakresie znanych i że liczba subauthorities jest mniejsza niż wartość maksymalna.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Aktualizacje `CSid` obiekt na podstawie nazwy konta i domeny lub istniejącą strukturę SID (identyfikator zabezpieczeń).

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszAccountName*<br/>
Nazwa konta.

*pszSystem*<br/>
Nazwa systemu. Ten ciąg może być nazwa komputera zdalnego. Jeśli ten ciąg ma wartość NULL, używany jest system lokalny.

*pSid*<br/>
Wskaźnik do [SID](/windows/desktop/api/winnt/ns-winnt-_sid) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.

### <a name="remarks"></a>Uwagi

`LoadAccount` próbuje znaleźć identyfikator zabezpieczeń dla określonej nazwy. Zobacz [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) Aby uzyskać więcej informacji.

##  <a name="operator_eq"></a>  CSid::operator =

Operator przypisania.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` można przypisać do `CSid` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CSid` obiektu.

##  <a name="operator_eq_eq"></a>  CSid::operator ==

Testuje dwa obiekty deskryptora zabezpieczeń dla równości.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części == — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi == — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli deskryptorów zabezpieczeń są równe, w przeciwnym razie wartość FALSE.

##  <a name="operator_neq"></a>  CSid::operator! =

Testuje dwa obiekty deskryptora zabezpieczeń pod kątem nierówności.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części! = — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi! = — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli deskryptorów zabezpieczeń nie są równe, w przeciwnym razie wartość FALSE.

##  <a name="operator_lt"></a>  CSid::operator &lt;

Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części! = — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi! = — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *lhs* jest mniejsza niż *rhs*, w przeciwnym razie wartość FALSE.

##  <a name="operator_lt__eq"></a>  CSid::operator &lt;=

Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części! = — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi! = — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *lhs* jest mniejsza niż lub równa *rhs*, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt"></a>  CSid::operator &gt;

Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części! = — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi! = — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *lhs* jest większa niż *rhs*, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt__eq"></a>  CSid::operator &gt;=

Porównuje wartość względną dwa obiekty deskryptora zabezpieczeń.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` wyświetlany w lewej części! = — operator.

*RHS*<br/>
`SID` (Identyfikator zabezpieczeń) lub `CSid` widoczny na prawej krawędzi! = — operator.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *lhs* jest większa niż lub równa *rhs*, w przeciwnym razie wartość FALSE.

##  <a name="operator_const_sid__star"></a>  Identyfikator SID const CSid::operator \*

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

Zwraca `SID` struktury jako ciąg w formacie odpowiednim do wyświetlania, gromadzenia i przekazywania. Odpowiednikiem [ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Zwraca opis stanu `CSid` obiektu.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość elementu danych, który przechowuje wartości opisujące stan `CSid` obiektu.

|Wartość|Opis|
|-----------|-----------------|
|SidTypeUser|Wskazuje użytkownika `SID` (identyfikator zabezpieczeń).|
|SidTypeGroup|Wskazuje grupę `SID`.|
|SidTypeDomain|Określa domenę `SID`.|
|SidTypeAlias|Wskazuje alias `SID`.|
|SidTypeWellKnownGroup|Wskazuje `SID` dla dobrze znana grupa.|
|SidTypeDeletedAccount|Wskazuje `SID` dla usuniętego konta.|
|SidTypeInvalid|Wskazuje nieprawidłową `SID`.|
|SidTypeUnknown|Wskazuje nieznany `SID` typu.|
|SidTypeComputer|Wskazuje `SID` dla komputera.|

### <a name="remarks"></a>Uwagi

Wywołaj [CSid::LoadAccount](#loadaccount) można zaktualizować `CSid` obiekt przed wywołaniem `SidNameUse` do zwrócenia jej stan. `SidNameUse` nie zmienia się stan obiektu (za pośrednictwem wywołania do `LookupAccountName` lub `LookupAccountSid`), ale tylko zwraca bieżący stan.

## <a name="see-also"></a>Zobacz także

[Zabezpieczenia — przykład](../../visual-cpp-samples.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)<br/>
[Operatory](../../atl/reference/atl-operators.md)
