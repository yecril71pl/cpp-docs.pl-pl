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
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330973"
---
# <a name="csecuritydesc-class"></a>Klasa CSecurityDesc

Ta klasa jest otoką `SECURITY_DESCRIPTOR` dla struktury.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CSecurityDesc::Odsłanianie](#fromstring)|Konwertuje deskryptator zabezpieczeń w formacie ciągu na prawidłowy, funkcjonalny deskryptor zabezpieczeń.|
|[CSecurityDesc::Kontrola](#getcontrol)|Pobiera informacje o kontroli z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetDacl](#getdacl)|Pobiera informacje o uznaniowej liście kontroli dostępu (DACL) z deskryptora zabezpieczeń.|
|[CSecurityDesc::Grupa Get](#getgroup)|Pobiera podstawowe informacje o grupie z deskryptora zabezpieczeń.|
|[CSecurityDesc::Właściciel firmy GetOwn](#getowner)|Pobiera informatora właściciela z deskryptora zabezpieczeń.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::GetSacl](#getsacl)|Pobiera informacje o liście kontroli dostępu do systemu (SACL) z deskryptora zabezpieczeń.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Określa, czy funkcja DACL jest skonfigurowana do obsługi automatycznej propagacji.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną listy DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Określa, czy deskryptor zabezpieczeń zawiera listy DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Określa, czy dacl jest skonfigurowany, aby zapobiec modyfikacjom.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Determines if the security descriptor's group security identifier (SID) was set by default.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Określa, czy identyfikator SID właściciela deskryptora zabezpieczeń został ustawiony domyślnie.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Określa, czy sacl jest skonfigurowany do obsługi automatycznego propagacji.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślnym kodem SACL.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Określa, czy deskryptor zabezpieczeń zawiera kod SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Określa, czy sacl jest skonfigurowany, aby zapobiec modyfikacjom.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Określa, czy deskryptor zabezpieczeń jest w formacie samowzejszym.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń do formatu bezwzględnego.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń do formatu względnego.|
|[CSecurityDesc::SetControl](#setcontrol)|Ustawia bity kontrolne deskryptora zabezpieczeń.|
|[CSecurityDesc::SetDacl](#setdacl)|Ustawia informacje w dacl. Jeśli dacl jest już obecny w deskryptorze zabezpieczeń, jest zastępowany.|
|[CSecurityDesc::SetGroup](#setgroup)|Ustawia podstawowe informacje o grupie deskryptora zabezpieczeń formatu bezwzględnego, zastępując wszystkie informacje o grupie podstawowej już obecne.|
|[CSecurityDesc::SetOwner](#setowner)|Ustawia informacje o właścicielu deskryptora zabezpieczeń formatu bezwzględnego, zastępując wszystkie informacje o właścicielu już obecne.|
|[CSecurityDesc::SetSacl](#setsacl)|Ustawia informacje w sacl. Jeśli sacl jest już obecny w deskryptorze zabezpieczeń, jest zastępowany.|
|[CSecurityDesc::ToString](#tostring)|Konwertuje deskryptora zabezpieczeń na format ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Struktura `SECURITY_DESCRIPTOR` zawiera informacje o zabezpieczeniach skojarzone z obiektem. Aplikacje używają tej struktury do ustawiania i wykonywania zapytań o stan zabezpieczeń obiektu. Zobacz też [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikacje nie `SECURITY_DESCRIPTOR` należy modyfikować struktury bezpośrednio, a zamiast tego należy użyć dostarczonych metod klasy.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Konstruktor.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Obiekt `CSecurityDesc` lub `SECURITY_DESCRIPTOR` struktura do przypisania do nowego `CSecurityDesc` obiektu.

### <a name="remarks"></a>Uwagi

Obiekt `CSecurityDesc` można opcjonalnie utworzyć `SECURITY_DESCRIPTOR` przy użyciu struktury `CSecurityDesc` lub uprzednio zdefiniowanego obiektu.

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc::~CSecurityDesc

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::Odsłanianie

Konwertuje deskryptator zabezpieczeń w formacie ciągu na prawidłowy, funkcjonalny deskryptor zabezpieczeń.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*pstr (włas inie*<br/>
Wskaźnik do ciągu zakończonego zerem, który zawiera [deskryptator zabezpieczeń w formacie ciągu](/windows/win32/SecAuthZ/security-descriptor-string-format) do konwersji.

### <a name="return-value"></a>Wartość zwracana

Powraca prawdziwe na sukces. Zgłasza wyjątek na błąd.

### <a name="remarks"></a>Uwagi

Ciąg można utworzyć za pomocą [CSecurityDesc::ToString](#tostring). Konwersja deskryptora zabezpieczeń na ciąg ułatwia przechowywanie i przesyłanie.

Ta metoda wywołuje [ConvertStringSecurityDescriptorToDescriptor .](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::Kontrola

Pobiera informacje o kontroli z deskryptora zabezpieczeń.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Wskaźnik do `SECURITY_DESCRIPTOR_CONTROL` struktury, która odbiera informacje sterujące deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl

Pobiera informacje o uznaniowej liście kontroli dostępu (DACL) z deskryptora zabezpieczeń.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl (pDacl)*<br/>
Wskaźnik do `CDacl` struktury, w której ma być przechowywana kopia listy DACL deskryptora zabezpieczeń. Jeśli istnieje uznaniowa ACL, metoda ustawia *pDacl* na adres uznaniowej listy ACL deskryptora zabezpieczeń. Jeśli uznaniowa acl nie istnieje, żadna wartość nie jest przechowywana.

*pbPrezentowanie*<br/>
Wskaźnik do wartości, która wskazuje obecność uznaniowej listy ACL w określonym deskryptorze zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera uznaniowącl ACL, ten parametr jest ustawiony na true. Jeśli deskryptor zabezpieczeń nie zawiera uznaniowej listy ACL, ten parametr jest ustawiony na false.

*pbDefaulted (Nieobeczone)*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_DACL_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` w strukturze, jeśli istnieje uznaniowa listy ACL dla deskryptora zabezpieczeń. Jeśli ta flaga jest prawdziwa, uznaniowa listy ACL została pobrana przez domyślny mechanizm; jeśli false, uznaniowe ACL został jawnie określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false, jeśli nie powiedzie się.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::Grupa Get

Pobiera podstawowe informacje o grupie z deskryptora zabezpieczeń.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), który odbiera kopię grupy przechowywane w CDacl.

*pbDefaulted (Nieobeczone)*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_GROUP_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` w strukturze, gdy metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false, jeśli nie powiedzie się.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::Właściciel firmy GetOwn

Pobiera informatora właściciela z deskryptora zabezpieczeń.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [CSid](../../atl/reference/csid-class.md) (identyfikator zabezpieczeń), który odbiera kopię grupy przechowywane w CDacl.

*pbDefaulted (Nieobeczone)*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_OWNER_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` w strukturze, gdy metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false, jeśli nie powiedzie się.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Zwraca wskaźnik do `SECURITY_DESCRIPTOR` struktury.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury [SECURITY_DESCRIPTOR.](/windows/win32/api/winnt/ns-winnt-security_descriptor)

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl

Pobiera informacje o liście kontroli dostępu do systemu (SACL) z deskryptora zabezpieczeń.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl (właswoi)*<br/>
Wskaźnik do `CSacl` struktury, w której ma być przechowywana kopia deskryptora zabezpieczeń SACL. Jeśli systemowa listy ACL istnieje, metoda ustawia *pSacl* na adres listy ACL systemu deskryptora zabezpieczeń. Jeśli systemowa listy ACL nie istnieje, nie jest przechowywana żadna wartość.

*pbPrezentowanie*<br/>
Wskaźnik do flagi ustawia metodę, aby wskazać obecność listy ACL systemu w określonym deskryptorze zabezpieczeń. Jeśli deskryptor zabezpieczeń zawiera systemowącl, ten parametr jest ustawiony na true. Jeśli deskryptor zabezpieczeń nie zawiera listy ACL systemu, ten parametr jest ustawiony na false.

*pbDefaulted (Nieobeczone)*<br/>
Wskaźnik do flagi ustawionej na wartość flagi SE_SACL_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` w strukturze, jeśli istnieje systemowa listy ACL dla deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false, jeśli nie powiedzie się.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Określa, czy uznaniowa lista kontroli dostępu (DACL) jest skonfigurowana do obsługi automatycznego propagacji.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli deskryptor zabezpieczeń zawiera listy DACL skonfigurowane do obsługi automatycznego propagacji dziedziczonych wpisów kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, gdy wykonuje algorytm automatycznego dziedziczenia dla obiektu i jego istniejących obiektów podrzędnych.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną dyskrecjonalistym listą kontroli dostępu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli deskryptor zabezpieczeń zawiera domyślną liczbę dacl, w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób, w jaki system traktuje DACL w odniesieniu do dziedziczenia wpisu kontroli dostępu (ACE). Na przykład jeśli twórca obiektu nie określi listy DACL, obiekt otrzyma domyślną listy DACL z tokenu dostępu twórcy. System ignoruje tę flagę, jeśli flaga SE_DACL_PRESENT nie jest ustawiona.

Ta flaga jest używana do określenia sposobu obliczania ostatecznej listy DACL na obiekcie i nie jest przechowywana fizycznie w formancie deskryptora zabezpieczeń zabezpieczanego obiektu.

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetDacl](#setdacl) metody.

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Określa, czy deskryptor zabezpieczeń zawiera uznaniową listę kontroli dostępu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera listy DACL, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Jeśli ta flaga nie jest ustawiona lub jeśli ta flaga jest ustawiona, a funkcja DACL ma wartość NULL, deskryptor zabezpieczeń umożliwia pełny dostęp do wszystkich.

Ta flaga jest używana do przechowywania informacji o zabezpieczeniach określonych przez obiekt wywołujący, dopóki deskryptor zabezpieczeń nie zostanie skojarzony z zabezpieczalnym obiektem. Po skojarzeniu deskryptora zabezpieczeń z zabezpieczanym obiektem flaga SE_DACL_PRESENT jest zawsze ustawiana w formancie deskryptora zabezpieczeń.

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetDacl](#setdacl) metody.

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected

Określa, czy dyskrecjonacyjna lista kontroli dostępu (DACL) jest skonfigurowana tak, aby zapobiegać modyfikacjom.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli funkcja DACL jest skonfigurowana tak, aby zapobiec modyfikowaniu deskryptora zabezpieczeń przez dziedziczne wpisy kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetDacl](#setdacl) metody.

Ta metoda obsługuje automatyczne propagowanie dziedziczonych ACE.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Determines if the security descriptor's group security identifier (SID) was set by default.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli domyślny mechanizm, a nie oryginalny dostawca deskryptora zabezpieczeń, pod warunkiem, że identyfikator SID grupy zabezpieczeń. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, użyj [metody CSecurityDesc::SetGroup.](#setgroup)

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Określa, czy identyfikator zabezpieczeń właściciela deskryptora zabezpieczeń zabezpieczeń (SID) został ustawiony domyślnie.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli domyślny mechanizm, a nie oryginalny dostawca deskryptora zabezpieczeń, pod warunkiem, że identyfikator SID właściciela deskryptora zabezpieczeń. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetOwner](#setowner) metody.

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Określa, czy lista kontroli dostępu do systemu (SACL) jest skonfigurowana do obsługi automatycznego propagacji.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli deskryptor zabezpieczeń zawiera kod SACL skonfigurowany do obsługi automatycznego propagacji dziedziczonych wpisów kontroli dostępu (ACE) do istniejących obiektów podrzędnych. W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

System ustawia ten bit, gdy wykonuje algorytm automatycznego dziedziczenia dla obiektu i jego istniejących obiektów podrzędnych.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Określa, czy deskryptor zabezpieczeń jest skonfigurowany z domyślną listą kontroli dostępu do systemu (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli deskryptor zabezpieczeń zawiera domyślny kod SACL, w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Ta flaga może mieć wpływ na sposób, w jaki system traktuje SACL w odniesieniu do dziedziczenia wpisu kontroli dostępu (ACE). System ignoruje tę flagę, jeśli flaga SE_SACL_PRESENT nie jest ustawiona.

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetSacl](#setsacl) metody.

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Określa, czy deskryptor zabezpieczeń zawiera listę kontroli dostępu do systemu (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli deskryptor zabezpieczeń zawiera kod SACL, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetSacl](#setsacl) metody.

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected

Określa, czy lista kontroli dostępu do systemu (SACL) jest skonfigurowana w celu zapobiegania modyfikacjom.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli kod SACL jest skonfigurowany tak, aby zapobiec modyfikowaniu deskryptora zabezpieczeń przez dziedziczne wpisy kontroli dostępu (ACE). W przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Aby ustawić tę flagę, należy użyć [CSecurityDesc::SetSacl](#setsacl) metody.

Ta metoda obsługuje automatyczne propagowanie dziedziczonych ACE.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Określa, czy deskryptor zabezpieczeń jest w formacie samowzejszym.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli deskryptor zabezpieczeń jest w formacie samowzejszym ze wszystkimi informacjami o zabezpieczeniach w ciągłym bloku pamięci. Zwraca wartość false, jeśli deskryptor zabezpieczeń jest w formacie bezwzględnym. Aby uzyskać więcej informacji, zobacz [Deskryptory bezpieczeństwa bezwzględnego i względnego](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń do formatu bezwzględnego.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false inaczej.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym zawiera wskaźniki do informacji, które zawiera, a nie do samych informacji. Deskryptor zabezpieczeń w formacie samowzejszym zawiera informacje w ciągłym bloku pamięci. W samowymiarowym deskryptorze `SECURITY_DESCRIPTOR` zabezpieczeń struktura zawsze uruchamia informacje, ale inne składniki deskryptora zabezpieczeń mogą śledzić strukturę w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń względnych są identyfikowane przez odsunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatny, gdy deskryptor zabezpieczeń musi być przechowywany na dysku lub przesyłany za pomocą protokołu komunikacyjnego. Aby uzyskać więcej informacji, zobacz [Deskryptory bezpieczeństwa bezwzględnego i względnego](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń do formatu względnego.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli metoda powiedzie się, false inaczej.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń w formacie bezwzględnym zawiera wskaźniki do informacji, które zawiera, a nie zawierające same informacje. Deskryptor zabezpieczeń w formacie samowzejszym zawiera informacje w ciągłym bloku pamięci. W samowymiarowym deskryptorze `SECURITY_DESCRIPTOR` zabezpieczeń struktura zawsze uruchamia informacje, ale inne składniki deskryptora zabezpieczeń mogą śledzić strukturę w dowolnej kolejności. Zamiast używać adresów pamięci, składniki deskryptora zabezpieczeń są identyfikowane przez przesunięcia od początku deskryptora zabezpieczeń. Ten format jest przydatny, gdy deskryptor zabezpieczeń musi być przechowywany na dysku lub przesyłany za pomocą protokołu komunikacyjnego. Aby uzyskać więcej informacji, zobacz [Deskryptory bezpieczeństwa bezwzględnego i względnego](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::operator =

Operator przypisania.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Struktura `SECURITY_DESCRIPTOR` lub `CSecurityDesc` obiekt do `CSecurityDesc` przypisania do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CSecurityDesc` obiekt.

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *

Rzutuje wartość do wskaźnika `SECURITY_DESCRIPTOR` do struktury.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::SetControl

Ustawia bity kontrolne deskryptora zabezpieczeń.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parametry

*ControlBitsOfInterest*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, która wskazuje bity formantu do ustawionego. Aby uzyskać listę flag, które można ustawić, zobacz [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*Zestaw ControlBitsToSet*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, która wskazuje nowe wartości dla bitów kontrolnych określonych przez *ControlBitsOfInterest* maski. Ten parametr może być kombinacją flag wymienionych dla *parametru ControlBitsOfInterest.*

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl

Ustawia informacje na uznaniowej liście kontroli dostępu (DACL). Jeśli dacl jest już obecny w deskryptorze zabezpieczeń, jest zastępowany.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Dacl*<br/>
Odwołanie do `CDacl` obiektu określającego listy DACL dla deskryptora zabezpieczeń. Ten parametr nie może być null. Aby ustawić null DACL w deskryptorze zabezpieczeń, pierwsza forma metody powinna być używana z *bPresent* ustawiona na false.

*bPrezentowanie*<br/>
Określa flagę wskazującą obecność listy DACL w deskryptorze zabezpieczeń. Jeśli ten parametr jest true, metoda ustawia flagę SE_DACL_PRESENT w `SECURITY_DESCRIPTOR_CONTROL` strukturze i używa wartości w *Dacl* i *bDefaulted* parametrów. Jeśli jest false, metoda czyści flagę SE_DACL_PRESENT, a *bDefaulted* jest ignorowana.

*bDefaulted (Niewzłocha)*<br/>
Określa flagę wskazującą źródło listy DACL. Jeśli ta flaga jest true, DACL został pobrany przez jakiś domyślny mechanizm. Jeśli false, DACL został jawnie określony przez użytkownika. Metoda przechowuje tę wartość w SE_DACL_DEFAULTED `SECURITY_DESCRIPTOR_CONTROL` flagi struktury. Jeśli ten parametr nie jest określony, flaga SE_DACL_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Istnieje istotna różnica między pustym a nieistniejącym DACL. Gdy dacl jest pusty, zawiera żadnych wpisów kontroli dostępu i nie prawa dostępu zostały jawnie przyznane. W rezultacie dostęp do obiektu jest niejawnie odmówiony. Gdy obiekt nie ma listy DACL, z drugiej strony, nie jest przypisana żadna ochrona do obiektu i każde żądanie dostępu jest przyznawane.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup

Ustawia podstawowe informacje o grupie deskryptora zabezpieczeń formatu bezwzględnego, zastępując wszystkie informacje o grupie podstawowej już obecne.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sid*<br/>
Odwołanie do obiektu [CSid](../../atl/reference/csid-class.md) dla nowej grupy podstawowej deskryptora zabezpieczeń. Ten parametr nie może być null. Deskryptor zabezpieczeń może być oznaczony jako nie posiadający DACL lub SACL, ale musi mieć grupę i właściciela, nawet to są to NULL SID (który jest wbudowanym identyfikatorem SID o specjalnym znaczeniu).

*bDefaulted (Niewzłocha)*<br/>
Wskazuje, czy podstawowe informacje o grupie zostały uzyskane z domyślnego mechanizmu. Jeśli ta wartość jest true, jest to informacje domyślne, a metoda przechowuje tę wartość jako flagę SE_GROUP_DEFAULTED w `SECURITY_DESCRIPTOR_CONTROL` strukturze. Jeśli ten parametr wynosi zero, flaga SE_GROUP_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

Ustawia informacje o właścicielu deskryptora zabezpieczeń formatu bezwzględnego. Zastępuje wszystkie informacje o właścicielu już obecne.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sid*<br/>
[CSid](../../atl/reference/csid-class.md) obiektu dla nowego właściciela głównego deskryptora zabezpieczeń. Ten parametr nie może być null.

*bDefaulted (Niewzłocha)*<br/>
Wskazuje, czy informacje o właścicielu pochodzą z mechanizmu domyślnego. Jeśli ta wartość jest true, jest to informacja domyślna. Metoda przechowuje tę wartość jako flagę `SECURITY_DESCRIPTOR_CONTROL` SE_OWNER_DEFAULTED w strukturze. Jeśli ten parametr wynosi zero, flaga SE_OWNER_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl

Ustawia informacje na liście kontroli dostępu do systemu (SACL). Jeśli sacl jest już obecny w deskryptorze zabezpieczeń, jest zastępowany.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sacl*<br/>
Wskaźnik do `CSacl` obiektu określającego sacl deskryptora zabezpieczeń. Ten parametr nie może być null i musi być CSacl obiektu. W przeciwieństwie do dacl, nie ma różnicy między NULL i pusty SACL, jak obiekty SACL nie określają praw dostępu, tylko informacje inspekcji.

*bDefaulted (Niewzłocha)*<br/>
Określa flagę wskazującą źródło SACL. Jeśli ta flaga jest true, SACL został pobrany przez jakiś domyślny mechanizm. Jeśli false, SACL został jawnie określony przez użytkownika. Metoda przechowuje tę wartość w SE_SACL_DEFAULTED flagi `SECURITY_DESCRIPTOR_CONTROL` struktury. Jeśli ten parametr nie jest określony, flaga SE_SACL_DEFAULTED jest wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

## <a name="csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString

Konwertuje deskryptora zabezpieczeń na format ciągu.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*pstr (włas inie*<br/>
Wskaźnik do ciągu zakończonego zerem, który otrzyma [deskryptor zabezpieczeń w formacie ciągu](/windows/win32/SecAuthZ/security-descriptor-string-format).

*Si*<br/>
Określa kombinację flag bitowych SECURITY_INFORMATION, aby wskazać składniki deskryptora zabezpieczeń, które mają być uwzględnione w ciągu wyjściowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy deskryptor zabezpieczeń jest w formacie ciągu, można go łatwiej przechowywać lub przesyłać. Użyj `CSecurityDesc::FromString` metody, aby przekonwertować ciąg z powrotem na deskryptor zabezpieczeń.

Parametr *si* może zawierać następujące flagi SECURITY_INFORMATION:

|Wartość|Znaczenie|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Dołącz właściciela.|
|GROUP_SECURITY_INFORMATION|Uwzględnij grupę podstawową.|
|DACL_SECURITY_INFORMATION|Dołącz DACL.|
|SACL_SECURITY_INFORMATION|Dołącz SACL.|

Jeśli funkcja DACL ma wartość NULL, a bit formantu SE_DACL_PRESENT jest ustawiony w deskryptorze zabezpieczeń wejściowych, metoda kończy się niepowodzeniem.

Jeśli funkcja DACL ma wartość NULL, a bit formantu SE_DACL_PRESENT nie jest ustawiony w deskryptorze zabezpieczeń wejściowych, wynikowy ciąg deskryptora zabezpieczeń nie ma składnika D:. Aby uzyskać więcej informacji, zobacz [Format ciągu deskryptora zabezpieczeń.](/windows/win32/SecAuthZ/security-descriptor-string-format)

Ta metoda wywołuje [ConvertStringSecurityDescriptorToDescriptor .](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Security_descriptor](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
