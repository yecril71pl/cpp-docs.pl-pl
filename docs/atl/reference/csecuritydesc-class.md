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
ms.openlocfilehash: 615c9a409b66ca0f515b15fbb55fd794102524fd
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694078"
---
# <a name="csecuritydesc-class"></a>Klasa CSecurityDesc

Ta klasa jest otoką `SECURITY_DESCRIPTOR` struktury.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CSecurityDesc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor.|
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Konwertuje format ciągu deskryptora zabezpieczeń do deskryptora zabezpieczeń. prawidłowy, funkcjonalności.|
|[CSecurityDesc::GetControl](#getcontrol)|Pobiera kontrolować informacji z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetDacl](#getdacl)|Pobiera arbitralnej kontroli dostępu (DACL) listy informacji z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetGroup](#getgroup)|Pobiera informacje o podstawowej grupy z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetOwner](#getowner)|Pobiera właściciela informacji z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::GetSacl](#getsacl)|Pobiera informacje o systemie kontroli dostępu (SACL) listy z deskryptora zabezpieczeń.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Określa, jeśli lista DACL jest skonfigurowany do obsługi automatycznego propagacji.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Określa, czy skonfigurowano deskryptora zabezpieczeń, z domyślną listą DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Określa, czy zawiera wartość DACL deskryptora zabezpieczeń.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Określa, czy skonfigurowano listy DACL, aby zapobiec modyfikacji.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Określa, jeśli identyfikator zabezpieczeń grupy deskryptora zabezpieczeń (SID) została ustawiona domyślnie.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Określa, jeśli identyfikator SID właściciela deskryptora zabezpieczeń została ustawiona domyślnie.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Określa, czy SACL jest skonfigurowany do obsługi propagacji automatyczne.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Określa, czy skonfigurowano deskryptora zabezpieczeń, z domyślną SACL.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Określa, czy deskryptor zabezpieczeń zawiera listę kontroli dostępu.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Określa, czy skonfigurowano SACL, aby zapobiec modyfikacji.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Określa, czy deskryptor zabezpieczeń w formacie autorelacyjnym.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń w formacie bezwzględnym.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń w formacie autorelacyjnym.|
|[CSecurityDesc::SetControl](#setcontrol)|Ustawia bity kontrolne deskryptora zabezpieczeń.|
|[CSecurityDesc::SetDacl](#setdacl)|Ustawia informacje przy użyciu listy DACL. Jeśli lista DACL jest już obecny w deskryptora zabezpieczeń, jest on zastępowany.|
|[CSecurityDesc::SetGroup](#setgroup)|Ustawia informacje o podstawowej grupy deskryptora zabezpieczeń formacie bezwzględnym, zastępując wszystkie podstawowe informacje o grupach już istnieje.|
|[CSecurityDesc::SetOwner](#setowner)|Ustawia informacje o właścicielu w formacie bezwzględnym deskryptora zabezpieczeń, zastępując wszystkie informacje o właścicielu już istnieje.|
|[CSecurityDesc::SetSacl](#setsacl)|Ustawia informacje na liście. Jeśli SACL znajduje się już w deskryptora zabezpieczeń, jest on zastępowany.|
|[CSecurityDesc::ToString](#tostring)|Konwertuje format ciągu deskryptora zabezpieczeń.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

`SECURITY_DESCRIPTOR` Struktura zawiera informacje o zabezpieczeniach skojarzone z obiektem. Ta struktura jest używana przez aplikacje do ustaw i kwerendy stanu zabezpieczeń obiektu. Zobacz też [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikacje nie należy modyfikować `SECURITY_DESCRIPTOR` struktury bezpośrednio, a zamiast tego należy używać metod klasy, pod warunkiem.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

Konstruktor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CSecurityDesc` Obiektu lub `SECURITY_DESCRIPTOR` struktury można przypisać do nowego `CSecurityDesc` obiektu.

### <a name="remarks"></a>Uwagi

`CSecurityDesc` Opcjonalnie można utworzyć obiekt przy użyciu `SECURITY_DESCRIPTOR` struktury lub uprzednio zdefiniowany `CSecurityDesc` obiektu.

##  <a name="dtor"></a>  CSecurityDesc:: ~ CSecurityDesc

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

##  <a name="fromstring"></a>  CSecurityDesc::FromString

Konwertuje format ciągu deskryptora zabezpieczeń do deskryptora zabezpieczeń. prawidłowy, funkcjonalności.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik na ciąg zakończony znakiem null, który zawiera [format ciągu deskryptora zabezpieczeń](/windows/desktop/SecAuthZ/security-descriptor-string-format) ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia. Zgłasza wyjątek w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ciąg można utworzyć za pomocą [CSecurityDesc::ToString](#tostring). Konwersja deskryptora zabezpieczeń w ciąg ułatwia do przechowywania i przesyłania.

Ta metoda wywołuje [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

Pobiera kontrolować informacji z deskryptora zabezpieczeń.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Wskaźnik do `SECURITY_DESCRIPTOR_CONTROL` strukturę, która otrzymuje informacje kontrolne deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false Jeśli zakończy się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

Pobiera arbitralnej kontroli dostępu (DACL) listy informacji z deskryptora zabezpieczeń.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Wskaźnik do `CDacl` struktury, w której chcesz przechowywać kopię listy DACL deskryptora zabezpieczeń. Jeśli istnieje poufnej listy kontroli dostępu, metoda ustawia *pDacl* adres deskryptora zabezpieczeń poufnej listy kontroli dostępu. Jeśli poufnej listy kontroli dostępu nie istnieje, wartość nie jest przechowywany.

*pbPresent*<br/>
Wskaźnik na wartość informującą o występowaniu poufnej listy kontroli dostępu w podany deskryptor zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera poufne listy kontroli dostępu, ten parametr ma wartość true. Jeśli deskryptor zabezpieczeń nie zawiera poufne listy kontroli dostępu, ten parametr ma wartość false.

*pbDefaulted*<br/>
Wskaźnik flagi ustawioną wartość flagi SE_DACL_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury istnienie poufnej listy kontroli dostępu dla deskryptora zabezpieczeń. Jeśli ta flaga ma wartość true, poufnej listy kontroli dostępu została pobrana przez domyślnego mechanizmu; w przypadku wartości FAŁSZ poufnej listy kontroli dostępu została jawnie określona przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false Jeśli zakończy się niepowodzeniem.

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

Pobiera informacje o podstawowej grupy z deskryptora zabezpieczeń.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), która otrzymuje kopię grupy przechowywane w CDacl.

*pbDefaulted*<br/>
Wskaźnik flagi ustawioną wartość flagi SE_GROUP_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury w przypadku zwrotu metody.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false Jeśli zakończy się niepowodzeniem.

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

Pobiera właściciela informacji z deskryptora zabezpieczeń.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), która otrzymuje kopię grupy przechowywane w CDacl.

*pbDefaulted*<br/>
Wskaźnik flagi ustawioną wartość flagi SE_OWNER_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury w przypadku zwrotu metody.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false Jeśli zakończy się niepowodzeniem.

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) struktury.

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

Pobiera informacje o systemie kontroli dostępu (SACL) listy z deskryptora zabezpieczeń.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl*<br/>
Wskaźnik do `CSacl` struktury, w której chcesz przechowywać kopię SACL deskryptora zabezpieczeń. Jeśli istnieje system listy kontroli dostępu, metoda ustawia *pSacl* adres deskryptora zabezpieczeń system listy kontroli dostępu. Jeśli system listy kontroli dostępu nie istnieje, wartość nie jest przechowywany.

*pbPresent*<br/>
Wskaźnik flagi metody ustawia obecności system listy kontroli dostępu w podany deskryptor zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera listy ACL systemu, ten parametr ma wartość true. Jeśli deskryptor zabezpieczeń nie zawiera listy ACL systemu, ten parametr ma wartość false.

*pbDefaulted*<br/>
Wskaźnik flagi ustawioną wartość flagi SE_SACL_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury, gdy system listy kontroli dostępu dla deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false Jeśli zakończy się niepowodzeniem.

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

Określa, czy list arbitralnej kontroli dostępu (DACL) jest skonfigurowany do obsługi propagacji automatyczne.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera DACL, który jest skonfigurowany do obsługi automatycznego propagacji wpisy dziedziczne kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, podczas wykonywania algorytmu automatycznego dziedziczenia obiektu i jego istniejących obiektów podrzędnych.

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

Określa, czy skonfigurowano deskryptora zabezpieczeń, za pomocą domyślnej listy arbitralnej kontroli dostępu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera domyślną listą DACL, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób system traktuje listy DACL w odniesieniu do dziedziczenia wpisu kontroli dostępu. Na przykład jeśli twórca obiektu nie określa listy DACL, obiekt odbiera domyślnej listy DACL z tokenu dostępu twórcy. System ignorują tę flagę, jeśli nie jest ustawiona flaga SE_DACL_PRESENT.

Ta flaga służy do określania, jak jest ostatnim listy DACL w obiekcie ma zostać obliczony i nie są przechowywane w fizycznie w formancie deskryptora zabezpieczeń obiektu zabezpieczanego.

Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

Określa, czy deskryptor zabezpieczeń zawiera listę arbitralnej kontroli dostępu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera DACL, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli ta flaga nie jest ustawiona lub jeśli ta flaga jest ustawiona, a lista DACL ma wartość NULL, deskryptor zabezpieczeń umożliwia pełny dostęp do wszystkich użytkowników.

Ta flaga służy do przechowywania informacji o zabezpieczeniach określone przez obiekt wywołujący, dopóki nie zostanie skojarzony z obiektem zabezpieczanego deskryptora zabezpieczeń. Gdy deskryptor zabezpieczeń jest skojarzona z zabezpieczanego obiektu, Flaga SE_DACL_PRESENT ma zawsze wartość w formancie deskryptora zabezpieczeń.

Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

Określa, czy skonfigurowano list arbitralnej kontroli dostępu (DACL), aby zapobiec modyfikacji.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista DACL jest skonfigurowany do deskryptora zabezpieczeń uniemożliwiają modyfikowana przez wpisy dziedziczne kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [CSecurityDesc::SetDacl](#setdacl) metody.

Ta metoda obsługuje automatyczne propagacji dziedziczne wpisy kontroli dostępu.

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

Określa, jeśli identyfikator zabezpieczeń grupy deskryptora zabezpieczeń (SID) została ustawiona domyślnie.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli mechanizmu domyślnego zamiast oryginalnej dostawcy deskryptora zabezpieczeń Podany deskryptor zabezpieczeń grupy identyfikatorów SID. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [CSecurityDesc::SetGroup](#setgroup) metody.

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

Określa, jeśli identyfikator zabezpieczeń właściciela deskryptora zabezpieczeń (SID) została ustawiona domyślnie.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli mechanizmu domyślnego zamiast oryginalnej dostawcy deskryptora zabezpieczeń podany identyfikator SID właściciela deskryptora zabezpieczeń. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [CSecurityDesc::SetOwner](#setowner) metody.

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

Określa, czy system listy kontroli dostępu (SACL) jest skonfigurowany do obsługi automatycznego propagacji.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera listę kontroli dostępu, który jest skonfigurowany do obsługi automatycznego propagacji wpisy dziedziczne kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, podczas wykonywania algorytmu automatycznego dziedziczenia obiektu i jego istniejących obiektów podrzędnych.

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

Określa, czy skonfigurowano deskryptora zabezpieczeń, za pomocą domyślnego system listy kontroli dostępu (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera domyślne SACL, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób system traktuje SACL, w odniesieniu do dziedziczenia wpisu kontroli dostępu. System ignorują tę flagę, jeśli nie jest ustawiona flaga SE_SACL_PRESENT.

Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

Określa, czy deskryptor zabezpieczeń zawiera system listy kontroli dostępu (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń zawiera listę kontroli dostępu, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

Określa, czy skonfigurowano system listy kontroli dostępu (SACL), aby zapobiec modyfikacji.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli skonfigurowano SACL deskryptora zabezpieczeń uniemożliwiają modyfikowana przez wpisy dziedziczne kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [CSecurityDesc::SetSacl](#setsacl) metody.

Ta metoda obsługuje automatyczne propagacji dziedziczne wpisy kontroli dostępu.

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

Określa, czy deskryptor zabezpieczeń w formacie autorelacyjnym.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli deskryptor zabezpieczeń jest w formacie autorelacyjnym wszystkich informacji zabezpieczeń w ciągłym bloku pamięci. Zwraca wartość false, jeśli deskryptor zabezpieczeń jest w formacie bezwzględnym. Aby uzyskać więcej informacji, zobacz [bezwzględne i deskryptorami zabezpieczeń Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń w formacie bezwzględnym.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym podano łącza do informacji zawartych w nim, zamiast samych informacji. Deskryptor zabezpieczeń w formacie autorelacyjnym zawiera informacje zawarte w ciągłym bloku pamięci. W deskryptorze zabezpieczeń autorelacyjnym `SECURITY_DESCRIPTOR` struktury zawsze zaczynają się od informacji, ale deskryptora zabezpieczeń przez inne składniki można zgodny ze strukturą w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń autorelacyjnym są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest użyteczny, gdy deskryptora zabezpieczeń, które muszą być przechowywane na dysku lub przesyłane przy użyciu protokołu komunikacji. Aby uzyskać więcej informacji, zobacz [bezwzględne i deskryptorami zabezpieczeń Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń w formacie autorelacyjnym.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli metoda się powiedzie, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym podano łącza do informacji zawartych w nim, a nie samych informacji. Deskryptor zabezpieczeń w formacie autorelacyjnym zawiera informacje zawarte w ciągłym bloku pamięci. W deskryptorze zabezpieczeń autorelacyjnym `SECURITY_DESCRIPTOR` struktury zawsze zaczynają się od informacji, ale deskryptora zabezpieczeń przez inne składniki można zgodny ze strukturą w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest użyteczny, gdy deskryptora zabezpieczeń, które muszą być przechowywane na dysku lub przesyłane przy użyciu protokołu komunikacji. Aby uzyskać więcej informacji, zobacz [bezwzględne i deskryptorami zabezpieczeń Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="operator_eq"></a>  CSecurityDesc::operator =

Operator przypisania.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`SECURITY_DESCRIPTOR` Struktury lub `CSecurityDesc` obiekt można przypisać do `CSecurityDesc` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CSecurityDesc` obiektu.

##  <a name="operator_const_security_descriptor__star"></a>  CSecurityDesc::operator const SECURITY_DESCRIPTOR *

Rzutuje na wskaźnik do wartości `SECURITY_DESCRIPTOR` struktury.

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
Maska SECURITY_DESCRIPTOR_CONTROL, która wskazuje bity kontrolne do ustawienia. Aby uzyskać listę flag, które można ustawiać, zobacz [SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Wskazuje nowe wartości dla bitów kontrolnych określonych przez maskę SECURITY_DESCRIPTOR_CONTROL *ControlBitsOfInterest* maski. Ten parametr może być kombinacją flag wymienionych dla *ControlBitsOfInterest* parametru.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

Ustawia informacje o liście arbitralnej kontroli dostępu (DACL). Jeśli lista DACL jest już obecny w deskryptora zabezpieczeń, jest on zastępowany.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Lista DACL*<br/>
Odwołanie do `CDacl` określenie listy DACL deskryptora zabezpieczeń obiektu. Ten parametr nie może być równa NULL. Aby ustawić PUSTEGO DACL deskryptora zabezpieczeń, pierwszy formularz metody powinien być używany z *bPresent* ustawiony na wartość false.

*bPresent*<br/>
Określa flagi wskazujące na obecność listy DACL w deskryptora zabezpieczeń. Jeśli ten parametr ma wartość true, metoda ustawia flagę SE_DACL_PRESENT `SECURITY_DESCRIPTOR_CONTROL` struktury i używa wartości w *Dacl* i *bDefaulted* parametrów. Jeśli jest to wartość false, metoda czyści flagę SE_DACL_PRESENT i *bDefaulted* jest ignorowana.

*bDefaulted*<br/>
Określa flagę wskazującą, źródło listy DACL. Jeśli ta flaga ma wartość true, lista DACL ma zostały pobrane przez niektóre domyślnego mechanizmu. W przypadku wartości FAŁSZ listy DACL został jawnie określony przez użytkownika. Metoda przechowuje wartość w Flaga SE_DACL_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` struktury. Jeśli ten parametr nie jest określony, Flaga SE_DACL_DEFAULTED jest wyczyszczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Istnieje ważna różnica między pusta i nieistniejącej DACL. Gdy lista DACL jest pusta, zawiera on żadnych wpisów kontroli dostępu i jawnie przyznano żadnych praw dostępu. W rezultacie niejawnie odmowa dostępu do obiektu. Gdy obiekt nie ma żadnych DACL, z drugiej strony Brak ochrony jest przypisana do obiektu, a każde żądanie dostęp jest udzielany.

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

Ustawia informacje o podstawowej grupy deskryptora zabezpieczeń formacie bezwzględnym, zastępując wszystkie podstawowe informacje o grupach już istnieje.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Identyfikator SID*<br/>
Odwołanie do [CSid](../../atl/reference/csid-class.md) obiektu dla nowej grupy podstawowej deskryptora zabezpieczeń. Ten parametr nie może być równa NULL. Deskryptor zabezpieczeń może być oznaczona jako nie posiadają DACL lub SACL, ale musi mieć grupę i właściciela, a nawet te są NULL identyfikatora SID (która jest wbudowana SID o specjalnym znaczeniu).

*bDefaulted*<br/>
Wskazuje, czy informacje o podstawowej grupie został utworzony na podstawie domyślnego mechanizmu. Jeśli ta wartość wynosi true, to domyślne informacje i metody przechowuje tej wartości jako flagi SE_GROUP_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury. Jeśli ten parametr wynosi zero, Flaga SE_GROUP_DEFAULTED jest wyczyszczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

Ustawia informacje o właścicielu deskryptora zabezpieczeń w formacie bezwzględnym. Zastępuje ona wszelkie informacje o właścicielu już istnieje.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Identyfikator SID*<br/>
[CSid](../../atl/reference/csid-class.md) obiekt podstawowy właściciel nowego deskryptora zabezpieczeń. Ten parametr nie może być równa NULL.

*bDefaulted*<br/>
Wskazuje, czy informacje o właścicielu jest tworzony na podstawie domyślnego mechanizmu. Jeśli ta wartość wynosi true, to domyślne informacje. Metoda przechowuje tej wartości jako flagi SE_OWNER_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` struktury. Jeśli ten parametr wynosi zero, Flaga SE_OWNER_DEFAULTED jest wyczyszczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

Ustawia informacje w system listy kontroli dostępu (SACL). Jeśli SACL znajduje się już w deskryptora zabezpieczeń, jest on zastępowany.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*SACL*<br/>
Wskaźnik do `CSacl` Określanie SACL deskryptora zabezpieczeń obiektu. Ten parametr nie może być równa NULL i musi być obiektem CSacl. W przeciwieństwie do listy DACL nie ma żadnej różnicy między wartością NULL i pustych SACL, jak obiekty z SACL należy określać prawa dostępu, tylko informacje dotyczące inspekcji.

*bDefaulted*<br/>
Określa flagę wskazującą, źródło SACL. Jeśli ta flaga ma wartość true, Lista SACL ma zostały pobrane przez niektóre domyślnego mechanizmu. W przypadku wartości FAŁSZ SACL został jawnie określony przez użytkownika. Metoda przechowuje wartość w Flaga SE_SACL_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` struktury. Jeśli ten parametr nie jest określony, Flaga SE_SACL_DEFAULTED jest wyczyszczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

##  <a name="tostring"></a>  CSecurityDesc::ToString

Konwertuje format ciągu deskryptora zabezpieczeń.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik na ciąg zakończony znakiem null, który otrzyma [format ciągu deskryptora zabezpieczeń](/windows/desktop/SecAuthZ/security-descriptor-string-format).

*SI*<br/>
Określa kombinacja flag bitowych SECURITY_INFORMATION, aby wskazać składniki deskryptora zabezpieczeń, aby uwzględnić w ciągu wyjściowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Po deskryptor zabezpieczeń jest w formacie ciągu, można ją łatwiej przechowywane lub przekazywane. Użyj `CSecurityDesc::FromString` metodę, aby przekonwertować ciąg do deskryptora zabezpieczeń.

*Si* parametru może zawierać następujące flagi SECURITY_INFORMATION:

|Wartość|Znaczenie|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Obejmować właściciela.|
|GROUP_SECURITY_INFORMATION|Uwzględnić grupy podstawowej.|
|DACL_SECURITY_INFORMATION|Zawiera listy DACL.|
|SACL_SECURITY_INFORMATION|Obejmują SACL.|

Jeśli wejściowy deskryptor zabezpieczeń jest ustawiony bit kontroli SE_DACL_PRESENT listy DACL ma wartość NULL, metoda kończy się niepowodzeniem.

Jeśli nie ustawiono bitu kontroli SE_DACL_PRESENT w deskryptorze zabezpieczeń listy DACL ma wartość NULL, wynikowego ciągu deskryptora zabezpieczeń nie ma składnika D:. Zobacz [Format ciągu deskryptora zabezpieczeń](/windows/desktop/SecAuthZ/security-descriptor-string-format) Aby uzyskać więcej informacji.

Ta metoda wywołuje [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia — przykład](../../visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
