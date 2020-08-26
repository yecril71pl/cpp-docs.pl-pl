---
title: CSid, Klasa
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
ms.openlocfilehash: b6787c0e3f075935f19d51aa73bbd66da9cc0fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835600"
---
# <a name="csid-class"></a>CSid, Klasa

Ta klasa jest otoką dla `SID` struktury (identyfikator zabezpieczeń).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSid
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CSid:: CSidArray](#csidarray)|Tablica `CSid` obiektów.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSid:: CSid](#csid)|Konstruktor.|
|[CSid:: ~ CSid](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSid:: AccountName](#accountname)|Zwraca nazwę konta skojarzonego z `CSid` obiektem.|
|[CSid::D omain](#domain)|Zwraca nazwę domeny skojarzonej z `CSid` obiektem.|
|[CSid:: EqualPrefix](#equalprefix)|Sprawdzenia `SID` (identyfikator zabezpieczeń) prefiksy dla równości.|
|[CSid:: GetLength](#getlength)|Zwraca długość `CSid` obiektu.|
|[CSid:: GetPSID](#getpsid)|Zwraca wskaźnik do `SID` struktury.|
|[CSid:: GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.|
|[CSid:: GetSubAuthority](#getsubauthority)|Zwraca określony podurząd w `SID` strukturze.|
|[CSid:: GetSubAuthorityCount](#getsubauthoritycount)|Zwraca liczbę podurzędów.|
|[CSid:: IsValid](#isvalid)|Testuje `CSid` obiekt pod kątem ważności.|
|[CSid:: LoadAccount](#loadaccount)|Aktualizuje `CSid` obiekt z nazwą konta i domeną lub istniejącą `SID` strukturą.|
|[CSid:: SID](#sid)|Zwraca ciąg identyfikatora.|
|[CSid:: SidNameUse](#sidnameuse)|Zwraca opis stanu `CSid` obiektu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator =](#operator_eq)|Operator przypisania.|
|[Identyfikator SID const operatora *](#operator_const_sid__star)|Rzutuje `CSid` obiekt na wskaźnik do `SID` struktury.|

### <a name="global-operators"></a>Operatory globalne

|Nazwa|Opis|
|-|-|
|[operator = =](#operator_eq_eq)|Testuje dwa obiekty deskryptora zabezpieczeń pod kątem równości|
|[operator! =](#operator_neq)|Testuje dwa obiekty deskryptora zabezpieczeń pod kątem nierówności|
|[zakład \<](#operator_lt)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[>operatora ](#operator_gt)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[zakład \<=](#operator_lt__eq)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|
|[>operatora =](#operator_gt__eq)|Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.|

## <a name="remarks"></a>Uwagi

`SID`Struktura jest strukturą o zmiennej długości służącej do jednoznacznego identyfikowania użytkowników lub grup.

Aplikacje nie powinny bezpośrednio modyfikować `SID` struktury, ale zamiast tego używają metod dostarczonych w tej klasie otoki. Zobacz również [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)i [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/win32/SecAuthZ/access-control) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

## <a name="csidaccountname"></a><a name="accountname"></a> CSid:: AccountName

Zwraca nazwę konta skojarzonego z `CSid` obiektem.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca LPCTSTR wskazujący nazwę konta.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje znaleźć nazwę określonego `SID` (identyfikatora zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Jeśli nazwa konta nie `SID` może zostać znaleziona, `AccountName` zwraca pusty ciąg. Taka sytuacja może wystąpić, jeśli limit czasu sieci uniemożliwia tej metodzie znalezienie nazwy. Występuje również w przypadku identyfikatorów zabezpieczeń bez odpowiadającej nazwy konta, na przykład `SID` identyfikującej sesję logowania.

## <a name="csidcsid"></a><a name="csid"></a> CSid:: CSid

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
Istniejąca `CSid` Struktura obiektu lub `SID` (identyfikator zabezpieczeń).

*IdentifierAuthority*<br/>
Urząd.

*nSubAuthorityCount*<br/>
Liczba podurzędów.

*pszAccountName*<br/>
Nazwa konta.

*pszSystem*<br/>
Nazwa systemu. Ten ciąg może być nazwą komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast niego zostanie użyty system lokalny.

*Pusty PSID*<br/>
Wskaźnik do `SID` struktury.

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje `CSid` obiekt, ustawia wewnętrzny element członkowski danych na *SidTypeInvalid*lub kopiując ustawienia z istniejącego `CSid` , `SID` lub istniejącego konta.

Jeśli inicjalizacja nie powiedzie się, Konstruktor zgłosi [klasę CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a> CSid:: ~ CSid

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby uzyskane przez obiekt.

## <a name="csidcsidarray"></a><a name="csidarray"></a> CSid:: CSidArray

Tablica obiektów [CSid](../../atl/reference/csid-class.md) .

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef określa typ tablicy, za pomocą której można pobrać identyfikatory zabezpieczeń z listy ACL (lista kontroli dostępu). Zobacz [cacls:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a> CSid::D omain

Zwraca nazwę domeny skojarzonej z `CSid` obiektem.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `LPCTSTR` wskazanie wskazującego na domenę.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje znaleźć nazwę określonego `SID` (identyfikatora zabezpieczeń). Aby uzyskać szczegółowe informacje, zobacz [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Jeśli nazwa konta nie `SID` może zostać znaleziona, program `Domain` zwraca domenę jako pusty ciąg. Taka sytuacja może wystąpić, jeśli limit czasu sieci uniemożliwia tej metodzie znalezienie nazwy. Występuje również w przypadku identyfikatorów zabezpieczeń bez odpowiadającej nazwy konta, na przykład `SID` identyfikującej sesję logowania.

## <a name="csidequalprefix"></a><a name="equalprefix"></a> CSid:: EqualPrefix

Sprawdzenia `SID` (identyfikator zabezpieczeń) prefiksy dla równości.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SID`Struktura lub obiekt (identyfikator zabezpieczeń) `CSid` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) w Windows SDK.

## <a name="csidgetlength"></a><a name="getlength"></a> CSid:: GetLength

Zwraca długość `CSid` obiektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca długość w bajtach `CSid` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli `CSid` Struktura jest nieprawidłowa, wartość zwracana jest niezdefiniowana. Przed wywołaniem `GetLength` Użyj funkcji członkowskiej [CSid:: IsValid](#isvalid) , aby sprawdzić, czy `CSid` jest ona prawidłowa.

> [!NOTE]
> W obszarze kompilacje debugowania funkcja spowoduje wystąpienie potwierdzenia, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetpsid"></a><a name="getpsid"></a> CSid:: GetPSID

Zwraca wskaźnik do `SID` struktury (identyfikatora zabezpieczeń).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres `CSid` źródłowej `SID` struktury obiektu.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a> CSid:: GetPSID_IDENTIFIER_AUTHORITY

Zwraca wskaźnik do `SID_IDENTIFIER_AUTHORITY` struktury.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca adres `SID_IDENTIFIER_AUTHORITY` struktury. Jeśli to się nie powiedzie, wartość zwracana jest niezdefiniowana. Błąd może wystąpić, jeśli `CSid` obiekt jest nieprawidłowy. w takim przypadku Metoda [CSid:: IsValid](#isvalid) zwraca wartość false. Funkcja `GetLastError` może zostać wywołana dla rozszerzonych informacji o błędzie.

> [!NOTE]
> W obszarze kompilacje debugowania funkcja spowoduje wystąpienie potwierdzenia, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a> CSid:: GetSubAuthority

Zwraca określony podurząd w `SID` strukturze (identyfikator zabezpieczeń).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAuthority*<br/>
Podurząd.

### <a name="return-value"></a>Wartość zwracana

Zwraca podurząd, do którego odwołuje się *NSubAuthority.* Wartość subauthority jest identyfikatorem względnym (RID).

### <a name="remarks"></a>Uwagi

Parametr *NSubAuthority* określa wartość indeksu określającą element tablicy podurzędu, która zostanie zwrócona przez metodę. Metoda nie wykonuje testów weryfikacyjnych dla tej wartości. Aplikacja może wywołać metodę [CSid:: GetSubAuthorityCount](#getsubauthoritycount) , aby odnaleźć zakres dopuszczalnych wartości.

> [!NOTE]
> W obszarze kompilacje debugowania funkcja spowoduje wystąpienie potwierdzenia, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a> CSid:: GetSubAuthorityCount

Zwraca liczbę podurzędów.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartość zwracana jest liczbą podurzędów.

Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezdefiniowana. Metoda kończy się niepowodzeniem, jeśli `CSid` obiekt jest nieprawidłowy. Aby uzyskać rozszerzone informacje o błędzie, wywołaj polecenie `GetLastError` .

> [!NOTE]
> W obszarze kompilacje debugowania funkcja spowoduje wystąpienie potwierdzenia, jeśli `CSid` obiekt jest nieprawidłowy.

## <a name="csidisvalid"></a><a name="isvalid"></a> CSid:: IsValid

Testuje `CSid` obiekt pod kątem ważności.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE `CSid` , jeśli obiekt jest prawidłowy, FAŁSZ, jeśli nie. Nie ma rozszerzonych informacji o błędzie dla tej metody; Nie wywołuj `GetLastError` .

### <a name="remarks"></a>Uwagi

`IsValid`Metoda sprawdza poprawność `CSid` obiektu przez sprawdzenie, czy numer poprawki znajduje się w znanym zakresie i czy liczba podurzędów jest mniejsza niż wartość maksymalna.

## <a name="csidloadaccount"></a><a name="loadaccount"></a> CSid:: LoadAccount

Aktualizuje `CSid` obiekt z nazwą konta i domeną lub istniejącą strukturą SID (identyfikator zabezpieczeń).

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
Nazwa systemu. Ten ciąg może być nazwą komputera zdalnego. Jeśli ten ciąg ma wartość NULL, zamiast niego zostanie użyty system lokalny.

*Pusty PSID*<br/>
Wskaźnik do struktury [identyfikatora SID](/windows/win32/api/winnt/ns-winnt-sid) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu. Aby uzyskać rozszerzone informacje o błędzie, wywołaj polecenie `GetLastError` .

### <a name="remarks"></a>Uwagi

`LoadAccount` próbuje znaleźć identyfikator zabezpieczeń dla określonej nazwy. Aby uzyskać więcej informacji, zobacz [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) .

## <a name="csidoperator-"></a><a name="operator_eq"></a> CSid:: operator =

Operator przypisania.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` do przypisania do `CSid` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CSid` obiektu.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a> CSid:: operator = =

Testuje dwa obiekty deskryptora zabezpieczeń pod kątem równości.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora = =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora = =.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli deskryptory zabezpieczeń są równe, w przeciwnym razie FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a> CSid:: operator! =

Testuje dwa obiekty deskryptora zabezpieczeń pod kątem nierówności.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora! =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora! =.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli deskryptory zabezpieczeń nie są równe, w przeciwnym razie FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a> CSid:: operator &lt;

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora! =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora! =.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *LHS* jest mniejszy niż *RHS*, w przeciwnym razie false.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a> CSid:: operator &lt;=

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora! =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora! =.

### <a name="return-value"></a>Wartość zwracana

Prawda, jeśli wartość *LHS* jest mniejsza niż lub równa *RHS*, w przeciwnym razie false.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a> CSid:: operator &gt;

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora! =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora! =.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *LHS* jest większy niż *RHS*, w przeciwnym razie false.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a> CSid:: operator &gt;=

Porównuje względną wartość dwóch obiektów deskryptora zabezpieczeń.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po lewej stronie operatora! =.

*RHS*<br/>
`SID`(Identyfikator zabezpieczeń) lub `CSid` który pojawia się po prawej stronie operatora! =.

### <a name="return-value"></a>Wartość zwracana

Prawda, jeśli wartość *LHS* jest większa lub równa *RHS*, w przeciwnym razie false.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a> CSid:: operator const — SID \*

Rzutuje `CSid` obiekt na wskaźnik na `SID` strukturę (identyfikator zabezpieczeń).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Zwraca adres `SID` struktury.

## <a name="csidsid"></a><a name="sid"></a> CSid:: SID

Zwraca `SID` strukturę (identyfikator zabezpieczeń) jako ciąg.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `SID` strukturę jako ciąg w formacie odpowiednim do wyświetlania, przechowywania lub przesyłania. Równoważne [podczas operacji ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a> CSid:: SidNameUse

Zwraca opis stanu `CSid` obiektu.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość elementu członkowskiego danych, który przechowuje wartość opisującą stan `CSid` obiektu.

|Wartość|Opis|
|-----------|-----------------|
|SidTypeUser|Wskazuje użytkownika `SID` (identyfikator zabezpieczeń).|
|SidTypeGroup|Wskazuje grupę `SID` .|
|SidTypeDomain|Wskazuje domenę `SID` .|
|SidTypeAlias|Wskazuje alias `SID` .|
|SidTypeWellKnownGroup|Wskazuje `SID` dla dobrze znanej grupy.|
|SidTypeDeletedAccount|Wskazuje `SID` dla usuniętego konta.|
|SidTypeInvalid|Wskazuje nieprawidłowy `SID` .|
|SidTypeUnknown|Wskazuje nieznany `SID` Typ.|
|SidTypeComputer|Wskazuje `SID` dla komputera.|

### <a name="remarks"></a>Uwagi

Wywołaj metodę [CSid:: LoadAccount](#loadaccount) , aby zaktualizować `CSid` obiekt przed wywołaniem `SidNameUse` go w celu zwrócenia jego stanu. `SidNameUse` nie zmienia stanu obiektu (przez wywołanie do `LookupAccountName` lub `LookupAccountSid` ), ale tylko zwraca bieżący stan.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)<br/>
[Operatory](../../atl/reference/atl-operators.md)
