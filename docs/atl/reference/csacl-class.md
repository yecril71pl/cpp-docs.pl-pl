---
title: Klasa CSacl
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: c4bbdfccb2d6d8b167c537b7ae4df57c89438479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496514"
---
# <a name="csacl-class"></a>Klasa CSacl

Ta klasa jest otoką dla struktury SACL (lista kontroli dostępu do systemu).

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CSacl::AddAuditAce](#addauditace)|Dodaje wpis kontroli dostępu inspekcji (ACE) do `CSacl` obiektu.|
|[CSacl::GetAceCount](#getacecount)|Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiekcie.|
|[CSacl::RemoveAce](#removeace)|Usuwa określony element ACE (wpis kontroli dostępu) z `CSacl` obiektu.|
|[CSacl::RemoveAllAces](#removeallaces)|Usuwa wszystkie wpisy ACE zawarte w `CSacl` obiekcie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSacl:: operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Lista SACL zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordy inspekcji w dzienniku zdarzeń zabezpieczeń kontrolera domeny. Należy zauważyć, że lista SACL generuje wpisy dziennika tylko na kontrolerze domeny, w którym nastąpiła próba dostępu, a nie na każdym kontrolerze domeny zawierającym replikę obiektu.

Aby ustawić lub pobrać listę SACL w deskryptorze zabezpieczeń obiektu, należy włączyć uprawnienie SE_SECURITY_NAME w tokenie dostępu żądającego wątku. Grupa Administratorzy ma przyznane uprawnienie domyślnie i może być przyznana innym użytkownikom lub grupom. Po udzieleniu uprawnień nie wszystkie są wymagane: przed wykonaniem operacji zdefiniowanej przez to uprawnienie musi być włączone w tokenie dostępu zabezpieczeń, aby zaczęło obowiązywać. Model umożliwia włączenie uprawnień tylko do określonych operacji systemowych, a następnie wyłączenie ich, gdy nie są już potrzebne. Przykłady włączania SE_SECURITY_NAME można znaleźć w tematach [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl) .

Użyj metod klasy dostarczonych do dodawania, usuwania, tworzenia i usuwania ACE z `SACL` obiektu. Zobacz również [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl).

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/win32/SecAuthZ/access-control) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cacls](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="addauditace"></a>CSacl::AddAuditAce

Dodaje wpis kontroli dostępu inspekcji (ACE) do `CSacl` obiektu.

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

*rSid*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Określa maskę praw dostępu do inspekcji dla określonego `CSid` obiektu.

*bSuccess*<br/>
Określa, czy mają być przeprowadzane inspekcje dozwolonych prób dostępu. Ustaw tę flagę na wartość true, aby włączyć inspekcję; w przeciwnym razie ustaw dla niego wartość false.

*bFailure*<br/>
Określa, czy odmowa dostępu ma być przeprowadzana inspekcją. Ustaw tę flagę na wartość true, aby włączyć inspekcję; w przeciwnym razie ustaw dla niego wartość false.

*AceFlags*<br/>
Zestaw flag bitowych kontrolujących dziedziczenie ACE.

*pObjectType*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ dziedziczonego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli do `CSacl` obiektu zostanie dodany wpis ACE, wartość false w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CSacl` Obiekt zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordy inspekcji w dzienniku zdarzeń zabezpieczeń. Ta metoda dodaje takie ACE do `CSacl` obiektu.

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać opis różnych flag, które można ustawić w parametrze *AceFlags* .

##  <a name="csacl"></a>CSacl::CSacl

Konstruktor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Istniejąca `ACL` struktura (lista kontroli dostępu).

### <a name="remarks"></a>Uwagi

Obiekt można opcjonalnie utworzyć przy użyciu istniejącej `ACL` struktury. `CSacl` Upewnij się, że ten parametr jest systemową listą kontroli dostępu (SACL), a nie poufną listą kontroli dostępu (DACL). W przypadku kompilacji debugowania, jeśli zostanie dostarczona lista DACL, zostanie wykonane potwierdzenie. W wersji Kompilacja wszystkich wpisów z listy DACL jest ignorowana.

##  <a name="dtor"></a>CSacl:: ~ CSacl

Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby uzyskane przez obiekt, w tym wszystkie wpisy kontroli dostępu (ACE).

##  <a name="getacecount"></a>CSacl::GetAceCount

Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiekcie.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę ACE zawartą w `CSacl` obiekcie.

##  <a name="operator_eq"></a>CSacl:: operator =

Operator przypisania.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`ACL` (Lista kontroli dostępu) do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CSacl` obiektu. Upewnij się, `ACL` że parametr jest rzeczywiście systemową listą kontroli dostępu (SACL), a nie poufną listą kontroli dostępu (DACL). W obszarze kompilacje debugowania zostanie wykonane potwierdzenie, a w kompilacjach `ACL` wydania parametr zostanie zignorowany.

##  <a name="removeace"></a>CSacl::RemoveAce

Usuwa określony element ACE (wpis kontroli dostępu) z `CSacl` obiektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu ACE do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda pochodzi z [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>CSacl::RemoveAllAces

Usuwa wszystkie wpisy kontroli dostępu (ACE) zawarte w `CSacl` obiekcie.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa każdą `ACE` strukturę (jeśli istnieje) `CSacl` w obiekcie.

## <a name="see-also"></a>Zobacz także

[Klasa CAcl](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Kontrola](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
