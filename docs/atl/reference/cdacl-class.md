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
ms.openlocfilehash: edfa7a47fa94e659d6529706d04021dfc800c269
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280124"
---
# <a name="cdacl-class"></a>Klasa CDacl

Ta klasa jest otoką dla struktury DACL (list arbitralnej kontroli dostępu).

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CDacl::AddAllowedAce](#addallowedace)|Dodaje dozwolonych ACE (wpis kontroli dostępu) do `CDacl` obiektu.|
|[CDacl::AddDeniedAce](#adddeniedace)|Dodaje odmowy ACE `CDacl` obiektu.|
|[CDacl::GetAceCount](#getacecount)|Zwraca liczbę wpisy kontroli dostępu (wpisy kontroli dostępu) w `CDacl` obiektu.|
|[CDacl::RemoveAce](#removeace)|Usuwa określone ACE (wpis kontroli dostępu) z `CDacl` obiektu.|
|[CDacl::RemoveAllAces](#removeallaces)|Usuwa wszystkie wpisy kontroli dostępu, zawarte w `CDacl` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Deskryptora zabezpieczeń obiektu może zawierać DACL. Lista DACL zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Jeśli lista DACL jest pusty (czyli zawiera zero ACE), bez dostępu ma jawnie przyznane uprawnienia, aby niejawnie odmowa dostępu. Jeśli jednak deskryptora zabezpieczeń obiektu ma DACL, obiekt nie jest chroniony i każdy z nich ma pełny dostęp.

Można pobrać listy DACL w obiekcie, musisz być właścicielem obiektu lub mieć READ_CONTROL dostępu do obiektu. Aby zmienić DACL obiektu, musi mieć WRITE_DAC dostępu do obiektu.

Należy użyć metod klasy dostarczonych do tworzenia, dodawania, usuwania i Usuń wpisy kontroli dostępu z `CDacl` obiektu. Zobacz też [AtlGetDacl](security-global-functions.md#atlgetdacl) i [AtlSetDacl](security-global-functions.md#atlsetdacl).

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Dodaje dozwolonych ACE (wpis kontroli dostępu) do `CDacl` obiektu.

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

*rSid*<br/>
A [CSid](../../atl/reference/csid-class.md) obiektu.

*AccessMask*<br/>
Określa maskę prawa dostępu, które mają być dozwolone dla określonego `CSid` obiektu.

*AceFlags*<br/>
Zestaw flag bitowych, określające ACE dziedziczenia.

*pObjectType*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ACE jest dodawany do `CDacl` obiektu FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

A `CDacl` obiektów zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Metoda ta umożliwia dodanie wpisu kontroli dostępu, który umożliwia dostęp do `CDacl` obiektu.

Zobacz [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) opis różnych flag, które można ustawić w `AceFlags` parametru.

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

*rSid*<br/>
Element `CSid` obiektu.

*AccessMask*<br/>
Określa maskę odmawiania praw dostępu dla określonego `CSid` obiektu.

*AceFlags*<br/>
Zestaw flag bitowych, określające ACE dziedziczenia. Wartość domyślna to 0, w pierwszej formie metody.

*pObjectType*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ACE jest dodawany do `CDacl` obiektu FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

A `CDacl` obiektów zawiera zero lub więcej wpisów ACE (wpisy kontroli dostępu), które identyfikują użytkowników i grupy, którzy mogą uzyskiwać dostęp do obiektu. Metoda ta umożliwia dodanie wpisu kontroli dostępu, który nie zezwala na dostęp do `CDacl` obiektu.

Zobacz [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) opis różnych flag, które można ustawić w `AceFlags` parametru.

##  <a name="cdacl"></a>  CDacl::CDacl

Konstruktor.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Istniejące `ACL` struktury (lista kontroli dostępu).

### <a name="remarks"></a>Uwagi

`CDacl` Obiektu można opcjonalnie utworzyć przy użyciu istniejącego `ACL` struktury. Należy pamiętać, że tylko DACL (list arbitralnej kontroli dostępu), a nie SACL (systemowa lista kontroli dostępu), powinien zostać przekazany jako parametr. W kompilacjach debugowania przekazywanie SACL spowoduje, że ASERCJA. W kompilacjach do wydania przekazywanie SACL spowoduje, że wpisy kontroli dostępu (wpisy kontroli dostępu) na liście ACL są ignorowane, a błąd nie wystąpi.

##  <a name="dtor"></a>  CDacl::~CDacl

Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby uzyskanych przez obiekt, w tym wszystkie wpisy kontroli dostępu (wpisy kontroli dostępu) za pomocą [CDacl::RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>  CDacl::GetAceCount

Zwraca liczbę wpisy kontroli dostępu (wpisy kontroli dostępu) w `CDacl` obiektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE zawarte w `CDacl` obiektu.

##  <a name="operator_eq"></a>  CDacl::operator =

Operator przypisania.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Listy kontroli dostępu (listy kontroli dostępu) do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CDacl` obiektu.

### <a name="remarks"></a>Uwagi

Należy upewnić się, aby były tylko przekazywane DACL (list arbitralnej kontroli dostępu) do tej funkcji. Przekazywanie SACL (systemowa lista kontroli dostępu) do tej funkcji spowoduje, że ASERCJA w kompilacjach debugowania, ale spowoduje nie błąd w wydawanych wersjach.

##  <a name="removeace"></a>  CDacl::RemoveAce

Usuwa określone ACE (wpis kontroli dostępu) z `CDacl` obiektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu ACE do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda jest tworzony na podstawie [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

Usuwa wszystkie wpisy kontroli dostępu (wpisy kontroli dostępu) zawartych w `CDacl` obiektu.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa co `ACE` struktury (wpis kontroli dostępu) (jeśli istnieją) w `CDacl` obiektu.

## <a name="see-also"></a>Zobacz także

[Zabezpieczenia — przykład](../../visual-cpp-samples.md)<br/>
[Klasa CAcl](../../atl/reference/cacl-class.md)<br/>
[Listy kontroli dostępu](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[Wpisy kontroli dostępu](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
