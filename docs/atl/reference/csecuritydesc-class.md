---
title: Klasa CSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: a9e0eb01608edf29f99209dffc932630ad08807a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915708"
---
# <a name="csecuritydesc-class"></a>Klasa CSecurityDesc

Ta klasa jest otoką dla `SECURITY_DESCRIPTOR` struktury.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSecurityDesc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor.|
|[CSecurityDesc::~CSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Konwertuje deskryptor zabezpieczeń w formacie ciągu na prawidłowy, funkcjonalny deskryptor zabezpieczeń.|
|[CSecurityDesc::GetControl](#getcontrol)|Pobiera informacje o kontrolkach z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetDacl](#getdacl)|Pobiera z deskryptora zabezpieczeń informacje o poufnej liście kontroli dostępu (DACL).|
|[CSecurityDesc::GetGroup](#getgroup)|Pobiera informacje o grupie podstawowej z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetOwner](#getowner)|Pobiera właściciela informacji z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::GetSacl](#getsacl)|Pobiera informacje o systemowej liście kontroli dostępu (SACL) z deskryptora zabezpieczeń.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Określa, czy lista DACL jest skonfigurowana do obsługi automatycznego propagacji.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną LISTą DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Określa, czy deskryptor zabezpieczeń zawiera listę DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Określa, czy lista DACL jest skonfigurowana do zapobiegania modyfikacji.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Określa, czy identyfikator zabezpieczeń grupy (SID) deskryptora zabezpieczeń został ustawiony domyślnie.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Określa, czy identyfikator SID właściciela deskryptora zabezpieczeń został ustawiony domyślnie.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Określa, czy lista SACL jest skonfigurowana do obsługi automatycznego propagacji.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną SACL.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Określa, czy deskryptor zabezpieczeń zawiera listę SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Określa, czy lista SACL jest skonfigurowana do zapobiegania modyfikacji.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Określa, czy deskryptor zabezpieczeń jest w formacie autorelacyjnym.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Wywołaj tę metodę, aby przekonwertować deskryptor zabezpieczeń na format bezwzględny.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Wywołaj tę metodę, aby skonwertować deskryptor zabezpieczeń do formatu samoobsługowego.|
|[CSecurityDesc::SetControl](#setcontrol)|Ustawia bity kontrolne deskryptora zabezpieczeń.|
|[CSecurityDesc::SetDacl](#setdacl)|Ustawia informacje w DACL. Jeśli lista DACL jest już obecna w deskryptorze zabezpieczeń, zostanie zastąpiona.|
|[CSecurityDesc::SetGroup](#setgroup)|Ustawia informacje o grupie podstawowej deskryptora zabezpieczeń w formacie bezwzględnym, zastępując wszystkie już obecne informacje o grupie podstawowej.|
|[CSecurityDesc::SetOwner](#setowner)|Ustawia informacje o właścicielu bezwzględnego deskryptora zabezpieczeń, zastępując wszystkie informacje o właścicielu, które już istnieją.|
|[CSecurityDesc::SetSacl](#setsacl)|Ustawia informacje w SACL. Jeśli lista SACL jest już obecna w deskryptorze zabezpieczeń, zostanie zastąpiona.|
|[CSecurityDesc:: ToString](#tostring)|Konwertuje deskryptor zabezpieczeń na format ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc:: operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

`SECURITY_DESCRIPTOR` Struktura zawiera informacje o zabezpieczeniach skojarzone z obiektem. Aplikacje używają tej struktury do ustawiania stanu zabezpieczeń obiektu i wykonywania względem nich zapytań. Zobacz również [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikacje nie powinny bezpośrednio modyfikować `SECURITY_DESCRIPTOR` struktury, a zamiast tego powinny używać dostarczonych metod klasy.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/desktop/SecAuthZ/access-control) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Konstruktor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Obiekt lub `SECURITY_DESCRIPTOR` struktura, która ma zostać przypisana `CSecurityDesc` do nowego obiektu. `CSecurityDesc`

### <a name="remarks"></a>Uwagi

Obiekt można opcjonalnie utworzyć `SECURITY_DESCRIPTOR` przy użyciu struktury lub wcześniej zdefiniowanego `CSecurityDesc` obiektu. `CSecurityDesc`

##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzieloną zasoby.

##  <a name="fromstring"></a>CSecurityDesc:: FromString

Konwertuje deskryptor zabezpieczeń w formacie ciągu na prawidłowy, funkcjonalny deskryptor zabezpieczeń.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik na ciąg zakończony znakiem null, który zawiera [deskryptor zabezpieczeń formatu ciągu](/windows/desktop/SecAuthZ/security-descriptor-string-format) do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia. Zgłasza wyjątek w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ciąg można utworzyć za pomocą [CSecurityDesc:: ToString](#tostring). Konwertowanie deskryptora zabezpieczeń na ciąg ułatwia ich przechowywanie i przesyłanie.

Ta metoda wywołuje [podczas operacji convertstringsecuritydescriptortosecuritydescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

##  <a name="getcontrol"></a>CSecurityDesc:: GetControl

Pobiera informacje o kontrolkach z deskryptora zabezpieczeń.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Wskaźnik na `SECURITY_DESCRIPTOR_CONTROL` strukturę, która otrzymuje informacje sterujące deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda zakończy się pomyślnie, FAŁSZ, jeśli to się nie powiedzie.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

##  <a name="getdacl"></a>CSecurityDesc:: GetDacl

Pobiera z deskryptora zabezpieczeń informacje o poufnej liście kontroli dostępu (DACL).

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Wskaźnik na `CDacl` strukturę, w której ma być przechowywana kopia listy DACL deskryptora zabezpieczeń. Jeśli istnieje poufna lista kontroli dostępu, Metoda ustawia *pDacl* na adres poufnej listy kontroli dostępu deskryptora zabezpieczeń. Jeśli lista DACL nie istnieje, nie jest przechowywana żadna wartość.

*pbPresent*<br/>
Wskaźnik na wartość wskazującą obecność poufnej listy ACL w określonym deskryptorze zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera poufną listę kontroli dostępu, ten parametr ma wartość true. Jeśli deskryptor zabezpieczeń nie zawiera poufnej listy kontroli dostępu, ten parametr jest ustawiany na wartość false.

*pbDefaulted*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_DACL_DEFAULTED w strukturze, `SECURITY_DESCRIPTOR_CONTROL` Jeśli istnieje poufna lista kontroli dostępu dla deskryptora zabezpieczeń. Jeśli ta flaga ma wartość true, poufna lista ACL została pobrana przy użyciu domyślnego mechanizmu; w przypadku wartości "false" poufny list ACL został jawnie określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda zakończy się pomyślnie, FAŁSZ, jeśli to się nie powiedzie.

##  <a name="getgroup"></a>CSecurityDesc:: getGroup

Pobiera informacje o grupie podstawowej z deskryptora zabezpieczeń.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do identyfikatora [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), który otrzymuje kopię grupy przechowywanej w CDacl.

*pbDefaulted*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_GROUP_DEFAULTED w strukturze, `SECURITY_DESCRIPTOR_CONTROL` gdy metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda zakończy się pomyślnie, FAŁSZ, jeśli to się nie powiedzie.

##  <a name="getowner"></a>CSecurityDesc:: getOwner

Pobiera właściciela informacji z deskryptora zabezpieczeń.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do identyfikatora [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), który otrzymuje kopię grupy przechowywanej w CDacl.

*pbDefaulted*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_OWNER_DEFAULTED w strukturze, `SECURITY_DESCRIPTOR_CONTROL` gdy metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda zakończy się pomyślnie, FAŁSZ, jeśli to się nie powiedzie.

##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor) .

##  <a name="getsacl"></a>CSecurityDesc:: getsacl

Pobiera informacje o systemowej liście kontroli dostępu (SACL) z deskryptora zabezpieczeń.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl*<br/>
Wskaźnik na `CSacl` strukturę, w której ma być przechowywana kopia listy SACL deskryptora zabezpieczeń. Jeśli istnieje systemowa lista kontroli dostępu, Metoda ustawia *pSacl* na adres listy ACL systemu deskryptora zabezpieczeń. Jeśli lista ACL systemu nie istnieje, nie jest przechowywana żadna wartość.

*pbPresent*<br/>
Wskaźnik do flagi ustawia metodę, aby wskazać obecność listy ACL systemu w określonym deskryptorze zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera systemową listę kontroli dostępu, ten parametr ma wartość true. Jeśli deskryptor zabezpieczeń nie zawiera systemowej listy kontroli dostępu, ten parametr jest ustawiany na wartość false.

*pbDefaulted*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_SACL_DEFAULTED w strukturze, `SECURITY_DESCRIPTOR_CONTROL` Jeśli istnieje lista ACL systemu dla deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda zakończy się pomyślnie, FAŁSZ, jeśli to się nie powiedzie.

##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Określa, czy lista arbitralnej kontroli dostępu (DACL) jest skonfigurowana do obsługi automatycznego propagacji.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera listę DACL, która jest skonfigurowana do obsługi automatycznej propagacji dziedziczonych wpisów kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, gdy wykonuje algorytm automatycznego dziedziczenia dla obiektu i jego istniejących obiektów podrzędnych.

##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Określa, czy deskryptor zabezpieczeń jest skonfigurowany przy użyciu domyślnej poufnej listy kontroli dostępu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera domyślną listę DACL, FAŁSZ w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób traktowania listy DACL przez system w odniesieniu do dziedziczenia wpisów kontroli dostępu (ACE). Na przykład jeśli twórca obiektu nie określa listy DACL, obiekt otrzymuje domyślną listę DACL z tokenu dostępu twórcy. System ignoruje tę flagę, jeśli flaga SE_DACL_PRESENT nie została ustawiona.

Ta flaga służy do określenia, jak Ostatnia lista DACL na obiekcie ma być obliczana i nie jest fizycznie przechowywana w kontroli deskryptora zabezpieczeń obiektu zabezpieczanego.

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetDacl](#setdacl) .

##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Określa, czy deskryptor zabezpieczeń zawiera poufną listę kontroli dostępu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera listę DACL, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Jeśli ta flaga nie jest ustawiona lub jeśli ta flaga jest ustawiona, a lista DACL ma wartość NULL, deskryptor zabezpieczeń zezwoli na pełny dostęp do wszystkich.

Ta flaga służy do przechowywania informacji o zabezpieczeniach określonych przez obiekt wywołujący do momentu skojarzenia deskryptora zabezpieczeń z zabezpieczanym obiektem. Po skojarzeniu deskryptora zabezpieczeń z obiektem zabezpieczonym flaga SE_DACL_PRESENT jest zawsze ustawiana w kontrolce deskryptora zabezpieczeń.

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetDacl](#setdacl) .

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

Określa, czy lista arbitralnej kontroli dostępu (DACL) jest skonfigurowana tak, aby zapobiec modyfikowaniu.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista DACL jest skonfigurowana tak, aby zapobiec modyfikowaniu deskryptora zabezpieczeń przez dziedziczenie wpisów kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetDacl](#setdacl) .

Ta metoda obsługuje automatyczną propagację dziedziczonych ACE.

##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Określa, czy identyfikator zabezpieczeń grupy (SID) deskryptora zabezpieczeń został ustawiony domyślnie.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli domyślny mechanizm, a nie oryginalny dostawca deskryptora zabezpieczeń, dostarczył identyfikator SID grupy deskryptora zabezpieczeń. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetGroup](#setgroup) .

##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Określa, czy identyfikator zabezpieczeń właściciela (SID) deskryptora zabezpieczeń został ustawiony domyślnie.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli domyślny mechanizm, a nie oryginalny dostawca deskryptora zabezpieczeń, dostarczył identyfikator SID właściciela deskryptora zabezpieczeń. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetOwner](#setowner) .

##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Określa, czy systemowa lista kontroli dostępu (SACL) jest skonfigurowana do obsługi automatycznego propagacji.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera listę SACL, która została skonfigurowana do obsługi automatycznej propagacji dziedziczonych wpisów kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, gdy wykonuje algorytm automatycznego dziedziczenia dla obiektu i jego istniejących obiektów podrzędnych.

##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną systemową listą kontroli dostępu (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera domyślną listę SACL, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób traktowania listy SACL przez system w odniesieniu do dziedziczenia wpisu kontroli dostępu (ACE). System ignoruje tę flagę, jeśli flaga SE_SACL_PRESENT nie została ustawiona.

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

Określa, czy deskryptor zabezpieczeń zawiera systemową listę kontroli dostępu (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera listę SACL, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

Określa, czy systemowa lista kontroli dostępu (SACL) jest skonfigurowana tak, aby zapobiec modyfikowaniu.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista SACL jest skonfigurowana tak, aby zapobiec modyfikowaniu deskryptora zabezpieczeń przez dziedziczenie wpisów kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj metody [CSecurityDesc:: SetSacl](#setsacl) .

Ta metoda obsługuje automatyczną propagację dziedziczonych ACE.

##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Określa, czy deskryptor zabezpieczeń jest w formacie autorelacyjnym.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń jest w formacie samodzielnym ze wszystkimi informacjami o zabezpieczeniach w ciągłym bloku pamięci. Zwraca wartość false, jeśli deskryptor zabezpieczeń jest w formacie bezwzględnym. Aby uzyskać więcej informacji, zobacz bezwzględne [i samodzielne deskryptory zabezpieczeń](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Wywołaj tę metodę, aby przekonwertować deskryptor zabezpieczeń na format bezwzględny.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym zawiera wskaźniki do informacji, które zawiera, a nie samych informacji. Deskryptor zabezpieczeń w formacie samodzielnym zawiera informacje w ciągłym bloku pamięci. W przypadku samodzielnego deskryptora zabezpieczeń, `SECURITY_DESCRIPTOR` struktura zawsze uruchamia te informacje, ale inne składniki deskryptora zabezpieczeń mogą śledzić strukturę w dowolnej kolejności. Zamiast korzystać z adresów pamięci, składniki deskryptora zabezpieczeń samodzielnego są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatny, gdy deskryptor zabezpieczeń musi być przechowywany na dysku lub przesłany przy użyciu protokołu komunikacyjnego. Aby uzyskać więcej informacji, zobacz bezwzględne [i samodzielne deskryptory zabezpieczeń](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Wywołaj tę metodę, aby skonwertować deskryptor zabezpieczeń do formatu samoobsługowego.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym zawiera wskaźniki do informacji, które zawiera, a nie zawierające same informacje. Deskryptor zabezpieczeń w formacie samodzielnym zawiera informacje w ciągłym bloku pamięci. W przypadku samodzielnego deskryptora zabezpieczeń, `SECURITY_DESCRIPTOR` struktura zawsze uruchamia te informacje, ale inne składniki deskryptora zabezpieczeń mogą śledzić strukturę w dowolnej kolejności. Zamiast korzystać z adresów pamięci, składniki deskryptora zabezpieczeń są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatny, gdy deskryptor zabezpieczeń musi być przechowywany na dysku lub przesłany przy użyciu protokołu komunikacyjnego. Aby uzyskać więcej informacji, zobacz bezwzględne [i samodzielne deskryptory zabezpieczeń](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="operator_eq"></a>CSecurityDesc:: operator =

Operator przypisania.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SECURITY_DESCRIPTOR` Struktura lub `CSecurityDesc` obiekt`CSecurityDesc` , który ma zostać przypisany do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CSecurityDesc` obiekt.

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

Rzutuje wartość na wskaźnik do `SECURITY_DESCRIPTOR` struktury.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

Ustawia bity kontrolne deskryptora zabezpieczeń.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parametry

*ControlBitsOfInterest*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, która wskazuje bity sterujące do ustawienia. Aby uzyskać listę flag, które można ustawiać, zobacz [SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, która wskazuje nowe wartości dla bitów kontroli określonych przez maskę *ControlBitsOfInterest* . Ten parametr może być kombinacją flag wymienionych dla parametru *ControlBitsOfInterest* .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

##  <a name="setdacl"></a>CSecurityDesc:: SetDacl

Ustawia informacje na poufnej liście kontroli dostępu (DACL). Jeśli lista DACL jest już obecna w deskryptorze zabezpieczeń, zostanie zastąpiona.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Lista*<br/>
Odwołanie do `CDacl` obiektu określającego listę DACL dla deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL. Aby ustawić listę DACL o wartości NULL w deskryptorze zabezpieczeń, należy użyć pierwszej formy metody z opcją *bPresent* ustawioną na wartość false.

*bPresent*<br/>
Określa flagę wskazującą obecność listy DACL w deskryptorze zabezpieczeń. Jeśli ten parametr ma wartość true, Metoda ustawia flagę SE_DACL_PRESENT w `SECURITY_DESCRIPTOR_CONTROL` strukturze i używa wartości z parametrów *DACL* i *bDefaulted* . Jeśli ma wartość false, Metoda czyści flagę SE_DACL_PRESENT, a *bDefaulted* jest ignorowana.

*bDefaulted*<br/>
Określa flagę wskazującą źródło listy DACL. Jeśli ta flaga ma wartość true, lista DACL została pobrana przez jakiś domyślny mechanizm. W przypadku wartości false lista DACL została jawnie określona przez użytkownika. Metoda przechowuje tę wartość w flagi `SECURITY_DESCRIPTOR_CONTROL` SE_DACL_DEFAULTED struktury. Jeśli ten parametr nie jest określony, flaga SE_DACL_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Istnieje ważna różnica między pustą i nieistniejącą LISTą DACL. Gdy lista DACL jest pusta, nie zawiera żadnych wpisów kontroli dostępu, a prawa dostępu nie zostały jawnie przyznane. W efekcie dostęp do obiektu jest niejawnie zabroniony. Jeśli obiekt nie ma listy DACL, z drugiej strony nie jest przypisana żadna ochrona do obiektu i zostanie udzielone wszelkie żądanie dostępu.

##  <a name="setgroup"></a>CSecurityDesc:: SetGroup

Ustawia informacje o grupie podstawowej deskryptora zabezpieczeń w formacie bezwzględnym, zastępując wszystkie już obecne informacje o grupie podstawowej.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*SID*<br/>
Odwołanie do obiektu [CSid](../../atl/reference/csid-class.md) dla nowej grupy podstawowej deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL. Deskryptor zabezpieczeń można oznaczyć jako niemający listy DACL lub SACL, ale musi mieć grupę i właściciela, nawet jeśli są to identyfikatory SID o wartości NULL (który jest wbudowanym identyfikatorem SID o specjalnym znaczeniu).

*bDefaulted*<br/>
Wskazuje, czy informacje o grupie podstawowej były uzyskiwane z poziomu domyślnego. Jeśli wartość jest równa true, jest to informacja domyślna, a metoda przechowuje tę wartość jako flagę SE_GROUP_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` strukturze. Jeśli ten parametr ma wartość zero, flaga SE_GROUP_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

Ustawia informacje o właścicielu deskryptora zabezpieczeń w formacie bezwzględnym. Zastępuje wszystkie informacje o właścicielu już obecne.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*SID*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) dla nowego podstawowego właściciela deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL.

*bDefaulted*<br/>
Wskazuje, czy informacje o właścicielu pochodzą od domyślnego mechanizmu. Jeśli wartość jest równa true, jest to informacja domyślna. Metoda przechowuje tę wartość jako flagę SE_OWNER_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` strukturze. Jeśli ten parametr ma wartość zero, flaga SE_OWNER_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

Ustawia informacje w systemowej liście kontroli dostępu (SACL). Jeśli lista SACL jest już obecna w deskryptorze zabezpieczeń, zostanie zastąpiona.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*SACL*<br/>
Wskaźnik do `CSacl` obiektu określającego listę SACL deskryptora zabezpieczeń. Ten parametr nie może mieć wartości NULL i musi być obiektem CSacl. W przeciwieństwie do listy DACL nie ma różnicy między wartością NULL a pustą listą SACL, ponieważ obiekty SACL nie określają praw dostępu, tylko informacje inspekcji.

*bDefaulted*<br/>
Określa flagę wskazującą źródło listy SACL. Jeśli ta flaga ma wartość true, lista SACL została pobrana przez jakiś domyślny mechanizm. W przypadku wartości false, użytkownik jawnie określił listę SACL. Metoda przechowuje tę wartość w flagi `SECURITY_DESCRIPTOR_CONTROL` SE_SACL_DEFAULTED struktury. Jeśli ten parametr nie jest określony, Flaga SE_SACL_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="tostring"></a>CSecurityDesc:: ToString

Konwertuje deskryptor zabezpieczeń na format ciągu.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik na ciąg zakończony znakiem null, który będzie odbierać [deskryptor zabezpieczeń w formacie ciągu](/windows/desktop/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Określa kombinację SECURITY_INFORMATION bitowych flag, aby wskazać składniki deskryptora zabezpieczeń do uwzględnienia w ciągu danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy deskryptor zabezpieczeń jest w formacie ciągu, można łatwiej go przechowywać lub przesyłać. Użyj metody `CSecurityDesc::FromString` , aby przekonwertować ciąg z powrotem do deskryptora zabezpieczeń.

Parametr *si* może zawierać następujące flagi SECURITY_INFORMATION:

|Wartość|Znaczenie|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Uwzględnij właściciela.|
|GROUP_SECURITY_INFORMATION|Uwzględnij grupę podstawową.|
|DACL_SECURITY_INFORMATION|Uwzględnij listę DACL.|
|SACL_SECURITY_INFORMATION|Uwzględnij listę SACL.|

Jeśli lista DACL ma wartość NULL, a bit kontrolki SE_DACL_PRESENT jest ustawiony w deskryptorze zabezpieczeń wejściowych, metoda zakończy się niepowodzeniem.

Jeśli lista DACL ma wartość NULL, a bit sterujący SE_DACL_PRESENT nie jest ustawiony w deskryptorze zabezpieczeń wejścia, otrzymany ciąg deskryptora zabezpieczeń nie ma składnika D:. Aby uzyskać więcej informacji, zobacz [Format ciągu deskryptora zabezpieczeń](/windows/desktop/SecAuthZ/security-descriptor-string-format) .

Ta metoda wywołuje [podczas operacji convertstringsecuritydescriptortosecuritydescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

## <a name="see-also"></a>Zobacz także

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
