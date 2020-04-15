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
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330921"
---
# <a name="csid-class"></a>Klasa CSid

Ta klasa jest otoką `SID` dla struktury (identyfikator zabezpieczeń).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSid
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

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
|[CSid::Nazwa konta](#accountname)|Zwraca nazwę konta skojarzonego z `CSid` obiektem.|
|[CSid::Domain](#domain)|Zwraca nazwę domeny skojarzonej z `CSid` obiektem.|
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` (identyfikator zabezpieczeń) prefiksy równości.|
|[CSid::GetLength](#getlength)|Zwraca długość `CSid` obiektu.|
|[CSid::GetPSID](#getpsid)|Zwraca wskaźnik do `SID` struktury.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.|
|[CSid::GetSubAuthority](#getsubauthority)|Zwraca określony podautory w `SID` strukturze.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Zwraca liczbę podrzędnych.|
|[CSid::IsValid](#isvalid)|Testuje `CSid` obiekt pod kątem ważności.|
|[CSid::LoadAccount](#loadaccount)|Aktualizuje `CSid` obiekt, podany nazwie konta `SID` i domeny lub istniejącej strukturze.|
|[CSid::Sid](#sid)|Zwraca ciąg identyfikatora.|
|[CSid::SidNameUżywko](#sidnameuse)|Zwraca opis stanu `CSid` obiektu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Operator przypisania.|
|[operator const SID *](#operator_const_sid__star)|Rzutuje `CSid` obiekt na wskaźnik `SID` do struktury.|

### <a name="global-operators"></a>Operatorzy globalni

|||
|-|-|
|[operator ==](#operator_eq_eq)|Testy dwóch obiektów deskryptora zabezpieczeń pod kątem równości|
|[operator !=](#operator_neq)|Testy dwóch obiektów deskryptora zabezpieczeń pod kątem nierówności|
|[Operator\<](#operator_lt)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[>operatora](#operator_gt)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[Operator\<=](#operator_lt__eq)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[>operatora =](#operator_gt__eq)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|

## <a name="remarks"></a>Uwagi

Struktura `SID` jest strukturą o zmiennej długości, używaną do jednoznacznej identyfikacji użytkowników lub grup.

Aplikacje nie `SID` należy modyfikować struktury bezpośrednio, ale zamiast tego należy użyć metod podanych w tej klasie otoki. Zobacz [też: AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), oraz [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::Nazwa konta

Zwraca nazwę konta skojarzonego z `CSid` obiektem.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazując nazwę konta.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje znaleźć nazwę `SID` dla określonego (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Jeśli nie `SID` można znaleźć nazwy `AccountName` konta dla, zwraca pusty ciąg. Taka możliwość może wystąpić, jeśli limit czasu sieci uniemożliwia tej metody znalezienie nazwy. Występuje również dla identyfikatorów zabezpieczeń bez odpowiedniej nazwy `SID` konta, takich jak identyfikujące sesji logowania.

## <a name="csidcsid"></a><a name="csid"></a>CSid::CSid

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

*Rhs*<br/>
Istniejący `CSid` obiekt `SID` lub (identyfikator zabezpieczeń) struktura.

*IdentyfikatorAutorytet*<br/>
Władza.

*nSubAuthorityCount*<br/>
Liczba podautorysów.

*pszAccountName*<br/>
Nazwa konta.

*pszSystem*<br/>
Nazwa systemu. Ten ciąg może być nazwą komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast tego jest używany system lokalny.

*pSid*<br/>
Wskaźnik do `SID` struktury.

### <a name="remarks"></a>Uwagi

Konstruktor `CSid` inicjuje obiekt, ustawia wewnętrzny element członkowski danych na *SidTypeInvalid*lub kopiując ustawienia z istniejącego `CSid`lub `SID`istniejącego konta.

Jeśli inicjowanie nie powiedzie się, konstruktor zrzuci [klasę CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a>CSid::~CSid

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszelkie zasoby nabyte przez obiekt.

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray

Tablica obiektów [CSid.](../../atl/reference/csid-class.md)

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Uwagi

Ta typedef określa typ tablicy, który może służyć do pobierania identyfikatorów zabezpieczeń z listy ACL (listy kontroli dostępu). Zobacz [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a>CSid::Domain

Zwraca nazwę domeny skojarzonej z `CSid` obiektem.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `LPCTSTR` wskazywanie do domeny.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje znaleźć nazwę `SID` dla określonego (identyfikator zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Jeśli nie `SID` można znaleźć nazwy `Domain` konta dla, zwraca domenę jako pusty ciąg. Taka możliwość może wystąpić, jeśli limit czasu sieci uniemożliwia tej metody znalezienie nazwy. Występuje również dla identyfikatorów zabezpieczeń bez odpowiedniej nazwy `SID` konta, takich jak identyfikujące sesji logowania.

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix

Testy `SID` (identyfikator zabezpieczeń) prefiksy równości.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
`SID` Struktura (identyfikator zabezpieczeń) `CSid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) w programie Windows SDK.

## <a name="csidgetlength"></a><a name="getlength"></a>CSid::GetLength

Zwraca długość `CSid` obiektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość w bajtach `CSid` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli `CSid` struktura jest nieprawidłowa, zwracana wartość jest niezdefiniowana. Przed `GetLength`wywołaniem użyj funkcji [CSid::IsValid,](#isvalid) aby sprawdzić, czy `CSid` jest prawidłowa.

> [!NOTE]
> W debugowanie tworzy funkcję spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID

Zwraca wskaźnik do `SID` struktury (identyfikator zabezpieczeń).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres podstawowej `CSid` `SID` struktury obiektu.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca `SID_IDENTIFIER_AUTHORITY` adres struktury. Jeśli nie powiedzie się, zwracana wartość jest niezdefiniowana. Błąd może wystąpić, `CSid` jeśli obiekt jest nieprawidłowy, w którym to przypadku [CSid::IsValid](#isvalid) metoda zwraca FAŁSZ. Funkcję `GetLastError` można wywołać w przypadku rozszerzonych informacji o błędzie.

> [!NOTE]
> W debugowanie tworzy funkcję spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority

Zwraca określony podautory w `SID` strukturze (identyfikator zabezpieczeń).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAuthority*<br/>
Podautory.

### <a name="return-value"></a>Wartość zwracana

Zwraca podautorystyki, do których odwołuje się *nSubAuthority.* Wartość podrzędności jest identyfikatorem względnym (RID).

### <a name="remarks"></a>Uwagi

Parametr *nSubAuthority* określa wartość indeksu identyfikującą element tablicy podrzędnej, który zostanie zwracany przez metodę. Metoda wykonuje żadnych testów sprawdzania poprawności dla tej wartości. Aplikacja może wywołać [CSid::GetSubAuthorityCount,](#getsubauthoritycount) aby odkryć zakres dopuszczalnych wartości.

> [!NOTE]
> W debugowanie tworzy funkcję spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount

Zwraca liczbę podrzędnych.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest liczbą podrzędnych.

Jeśli metoda nie powiedzie się, zwracana wartość jest niezdefiniowana. Metoda kończy się `CSid` niepowodzeniem, jeśli obiekt jest nieprawidłowy. Aby uzyskać rozszerzone informacje `GetLastError`o błędzie, zadzwoń do pliku .

> [!NOTE]
> W debugowanie tworzy funkcję spowoduje ASSERT, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid::IsValid

Testuje `CSid` obiekt pod kątem ważności.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CSid` PRAWDA, jeśli obiekt jest prawidłowy, WARTOŚĆ FAŁSZ, jeśli nie. Nie ma żadnych rozszerzonych informacji o błędzie dla tej metody; nie dzwonić `GetLastError`.

### <a name="remarks"></a>Uwagi

Metoda `IsValid` sprawdza poprawność `CSid` obiektu, sprawdzając, czy numer poprawki mieści się w znanym zakresie i czy liczba podautorów jest mniejsza niż maksymalna.

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::LoadAccount

Aktualizuje `CSid` obiekt, podany nazwie konta i domenie lub istniejącej strukturze identyfikatora SID (identyfikatora zabezpieczeń).

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
Nazwa systemu. Ten ciąg może być nazwą komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast tego jest używany system lokalny.

*pSid*<br/>
Wskaźnik do struktury [SID.](/windows/win32/api/winnt/ns-winnt-sid)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie. Aby uzyskać rozszerzone informacje `GetLastError`o błędzie, zadzwoń do pliku .

### <a name="remarks"></a>Uwagi

`LoadAccount`próbuje znaleźć identyfikator zabezpieczeń dla określonej nazwy. Aby uzyskać więcej informacji, zobacz [WyszukiwanieKonsyduj.](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::operator =

Operator przypisania.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` przypisać do `CSid` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CSid` zaktualizowanego obiektu.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::operator ==

Testy dwóch obiektów deskryptora zabezpieczeń pod kątem równości.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora == .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora == .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli deskryptory zabezpieczeń są równe, w przeciwnym razie FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::operator !=

Testuje dwa obiekty deskryptora zabezpieczeń pod kątem nierówności.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora != .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora != .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli deskryptory zabezpieczeń nie są równe, w przeciwnym razie FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::operator&lt;

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora != .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora != .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *lhs* jest mniejsza niż *rhs*, w przeciwnym razie FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::operator&lt;=

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora != .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora != .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *lhs* jest mniejsza lub równa *rhs*, w przeciwnym razie FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::operator&gt;

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora != .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora != .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *lhs* jest większa niż *rhs*, w przeciwnym razie FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::operator&gt;=

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora != .

*Rhs*<br/>
(identyfikator `SID` zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora != .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *lhs* jest większa lub równa *rhs*, w przeciwnym razie FALSE.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::operator const SID\*

Rzutuje `CSid` obiekt na wskaźnik `SID` do struktury (identyfikator zabezpieczeń).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Zwraca adres `SID` struktury.

## <a name="csidsid"></a><a name="sid"></a>CSid::Sid

Zwraca `SID` strukturę (identyfikator zabezpieczeń) jako ciąg.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `SID` strukturę jako ciąg w formacie odpowiednim do wyświetlania, przechowywania lub transmisji. Odpowiednik [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUżywko

Zwraca opis stanu `CSid` obiektu.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość elementu członkowskiego danych, który przechowuje wartość `CSid` opisującą stan obiektu.

|Wartość|Opis|
|-----------|-----------------|
|SidTypeUżydnik|Wskazuje użytkownika `SID` (identyfikator zabezpieczeń).|
|Grupa SidTypeGroup|Wskazuje grupę `SID`.|
|Domena SidType|Wskazuje domenę `SID`.|
|Identyfikator SidTypeAlias|Wskazuje alias `SID`.|
|Grupa SidTypeWellKnown|Wskazuje a `SID` dla dobrze znanej grupy.|
|Konto SidTypeDeletedAccount|Wskazuje `SID` dla usuniętego konta.|
|Identyfikator SidTypeInvalid|Wskazuje nieprawidłowy `SID`.|
|SidTypeUnknown (SidTypeUnknown)|Wskazuje nieznany `SID` typ.|
|Sypialnykomputer|Wskazuje a `SID` dla komputera.|

### <a name="remarks"></a>Uwagi

Wywołanie [CSid::LoadAccount,](#loadaccount) aby zaktualizować `CSid` obiekt przed wywołaniem, `SidNameUse` aby przywrócić jego stan. `SidNameUse`nie zmienia stanu obiektu (przez `LookupAccountName` wywołanie `LookupAccountSid`lub ), ale zwraca tylko bieżący stan.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)<br/>
[Operatory](../../atl/reference/atl-operators.md)
