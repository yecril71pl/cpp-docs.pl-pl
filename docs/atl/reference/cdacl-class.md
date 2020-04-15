---
title: Klasa CDacl
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327149"
---
# <a name="cdacl-class"></a>Klasa CDacl

Ta klasa jest otoką dla struktury DACL (uznaniowej listy kontroli dostępu).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CDacl : public CAcl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Konstruktor.|
|[CDacl::~CDacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Dodaje dozwolony wpis ACE (wpis kontroli `CDacl` dostępu) do obiektu.|
|[CDacl::AddDeniedAce](#adddeniedace)|Dodaje odmowę ACE `CDacl` do obiektu.|
|[CDacl::GetAceCount](#getacecount)|Zwraca liczbę wpisów ACE (wpisów kontroli `CDacl` dostępu) w obiekcie.|
|[CDacl::UsuńAce](#removeace)|Usuwa określony wpis ACE (wpis kontroli `CDacl` dostępu) z obiektu.|
|[CDacl::UsuńWszystkie](#removeallaces)|Usuwa wszystkie wpisy ACE zawarte `CDacl` w obiekcie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń obiektu może zawierać listy DACL. Listy DACL zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, które mogą uzyskać dostęp do obiektu. Jeśli dacl jest pusty (oznacza to, że zawiera zero wpisów ACE), nie ma dostępu jawnie przyznane, więc dostęp jest niejawnie odmówiono. Jeśli jednak deskryptor zabezpieczeń obiektu nie ma listy DACL, obiekt jest niechroniony i każdy ma pełny dostęp.

Aby pobrać listy DACL obiektu, użytkownik musi być właścicielem obiektu lub mieć READ_CONTROL dostęp do obiektu. Aby zmienić dacl obiektu, musisz mieć WRITE_DAC dostęp do obiektu.

Za pomocą podanych metod klasy można tworzyć, dodawać, usuwać i usuwać wpisy ACE z `CDacl` obiektu. Zobacz [też: AtlGetDacl](security-global-functions.md#atlgetdacl) i [AtlSetDacl](security-global-functions.md#atlsetdacl).

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cacl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce

Dodaje dozwolony wpis ACE (wpis kontroli `CDacl` dostępu) do obiektu.

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

*rSid (wyd.*<br/>
Obiekt [CSid.](../../atl/reference/csid-class.md)

*Maska dostępu*<br/>
Określa maskę praw dostępu, które mają `CSid` być dozwolone dla określonego obiektu.

*AceFlags (AceFlags)*<br/>
Zestaw flag bitowych sterujących dziedziczeniem ACE.

*pObiektyp*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczonego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wpis `CDacl` ACE zostanie dodany do obiektu, FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Obiekt `CDacl` zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, które mogą uzyskać dostęp do obiektu. Ta metoda dodaje ACE, który `CDacl` umożliwia dostęp do obiektu.

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) opis różnych flag, które można ustawić w `AceFlags` parametrze.

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce

Dodaje odmowę wpisu ACE (wpis `CDacl` kontroli dostępu) do obiektu.

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

*rSid (wyd.*<br/>
Obiekt `CSid`.

*Maska dostępu*<br/>
Określa maskę praw dostępu, które mają `CSid` zostać odrzucone dla określonego obiektu.

*AceFlags (AceFlags)*<br/>
Zestaw flag bitowych sterujących dziedziczeniem ACE. Wartość domyślna wartość 0 w pierwszej formie metody.

*pObiektyp*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczonego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wpis `CDacl` ACE zostanie dodany do obiektu, FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Obiekt `CDacl` zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, które mogą uzyskać dostęp do obiektu. Ta metoda dodaje ACE, który `CDacl` odmawia dostępu do obiektu.

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) opis różnych flag, które można ustawić w `AceFlags` parametrze.

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl

Konstruktor.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Istniejąca `ACL` struktura (lista kontroli dostępu).

### <a name="remarks"></a>Uwagi

Obiekt `CDacl` można opcjonalnie utworzyć przy `ACL` użyciu istniejącej struktury. Należy pamiętać, że tylko DACL (uznaniowa lista kontroli dostępu), a nie SACL (lista kontroli dostępu do systemu), powinny być przekazywane jako ten parametr. W kompilacjach debugowania przekazywanie SACL spowoduje ASSERT. W kompilacjach wersji przekazywanie sacl spowoduje, że wpisy ACE (wpisy kontroli dostępu) w akcesach zostaną zignorowane i nie wystąpi żaden błąd.

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl::~CDacl

Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby nabyte przez obiekt, w tym wszystkie wpisy ACE (wpisy kontroli dostępu) przy użyciu [CDacl::RemoveAllAces](#removeallaces).

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount

Zwraca liczbę wpisów ACE (wpisów kontroli `CDacl` dostępu) w obiekcie.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE `CDacl` zawartych w obiekcie.

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::operator =

Operator przypisania.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Lista ACL (lista kontroli dostępu) do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CDacl` zaktualizowanego obiektu.

### <a name="remarks"></a>Uwagi

Należy upewnić się, że tylko przekazać DACL (uznaniowa lista kontroli dostępu) do tej funkcji. Przekazywanie SACL (lista kontroli dostępu do systemu) do tej funkcji spowoduje ASSERT w debugowania kompilacji, ale spowoduje brak błędu w kompilacjach wydania.

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::UsuńAce

Usuwa określony wpis ACE (wpis kontroli `CDacl` dostępu) z obiektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks do wpisu ACE, aby usunąć.

### <a name="remarks"></a>Uwagi

Ta metoda jest pochodną [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::UsuńWszystkie

Usuwa wszystkie wpisy ACE (wpisy kontroli dostępu) `CDacl` zawarte w obiekcie.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa każdą `ACE` (wpis kontroli dostępu) struktury (jeśli `CDacl` istnieje) w obiekcie.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Klasa CAcl](../../atl/reference/cacl-class.md)<br/>
[Listy acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Asy](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
