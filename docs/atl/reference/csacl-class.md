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
ms.openlocfilehash: d5a060555901361ef6c70c6a4f801605eafd92cf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746548"
---
# <a name="csacl-class"></a>Klasa CSacl

Ta klasa jest otoką dla struktury SACL (lista kontroli dostępu do systemu).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSacl : public CAcl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|Konstruktor.|
|[CSacl::~CSacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Dodaje wpis kontroli dostępu inspekcji (ACE) do `CSacl` obiektu.|
|[CSacl::GetAceCount](#getacecount)|Zwraca liczbę wpisów kontroli dostępu (ACE) `CSacl` w obiekcie.|
|[CSacl::UsuńAce](#removeace)|Usuwa określony wpis ACE (wpis kontroli `CSacl` dostępu) z obiektu.|
|[CSacl::UsuńWszystkie](#removeallaces)|Usuwa wszystkie wpisy ACE zawarte `CSacl` w obiekcie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSacl::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Znak SACL zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordy inspekcji w dzienniku zdarzeń zabezpieczeń kontrolera domeny. Należy zauważyć, że biblioteka SACL generuje wpisy dziennika tylko na kontrolerze domeny, na którym wystąpiła próba dostępu, a nie na każdym kontrolerze domeny zawierającym replikę obiektu.

Aby ustawić lub pobrać sacl w deskryptorze zabezpieczeń obiektu, uprawnienie SE_SECURITY_NAME musi być włączone w tokenie dostępu wątku żądającego. Grupa administratorów ma domyślnie przyznane to uprawnienie i może być przyznane innym użytkownikom lub grupom. Posiadanie przyznanego uprawnienia nie jest wszystko, co jest wymagane: przed operacją zdefiniowaną przez uprawnienie mogą być wykonywane, uprawnienie musi być włączone w tokenie dostępu zabezpieczającego, aby wejść w życie. Model umożliwia włączenie uprawnień tylko dla określonych operacji systemowych, a następnie wyłączone, gdy nie są już potrzebne. Zobacz [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl) przykłady włączania SE_SECURITY_NAME.

Za pomocą podanych metod klasy można dodawać, usuwać, tworzyć i usuwać wpisy ACE z `SACL` obiektu. Zobacz [też: AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl).

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cacl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce

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

*rSid (wyd.*<br/>
Obiekt [CSid.](../../atl/reference/csid-class.md)

*Maska dostępu*<br/>
Określa maskę praw dostępu, które mają `CSid` być poddane inspekcji dla określonego obiektu.

*bSukcesa*<br/>
Określa, czy dozwolone próby dostępu mają być poddane inspekcji. Ustaw tę flagę na true, aby włączyć inspekcję; w przeciwnym razie ustaw go na false.

*bWłażalna*<br/>
Określa, czy próby odmowy dostępu mają być poddane inspekcji. Ustaw tę flagę na true, aby włączyć inspekcję; w przeciwnym razie ustaw go na false.

*AceFlags (AceFlags)*<br/>
Zestaw flag bitowych sterujących dziedziczeniem ACE.

*pObiektyp*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczonego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wpis `CSacl` ACE zostanie dodany do obiektu, FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Obiekt `CSacl` zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordy inspekcji w dzienniku zdarzeń zabezpieczeń. Ta metoda dodaje taki ACE do `CSacl` obiektu.

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) opis różnych flag, które można ustawić w *parametrze AceFlags.*

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl

Konstruktor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Istniejąca `ACL` struktura (lista kontroli dostępu).

### <a name="remarks"></a>Uwagi

Obiekt `CSacl` można opcjonalnie utworzyć przy `ACL` użyciu istniejącej struktury. Upewnij się, że ten parametr jest listą kontroli dostępu do systemu (SACL), a nie uznaniową listą kontroli dostępu (DACL). W debugowania kompilacji, jeśli DACL jest dostarczany potwierdzenia wystąpi. W wersji kompilacje wszelkie wpisy z listy DACL są ignorowane.

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl::~CSacl

Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby nabyte przez obiekt, w tym wszystkie wpisy kontroli dostępu (ACE).

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount

Zwraca liczbę wpisów kontroli dostępu (ACE) `CSacl` w obiekcie.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE `CSacl` zawartych w obiekcie.

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::operator =

Operator przypisania.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
(Lista `ACL` kontroli dostępu) do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CSacl` zaktualizowanego obiektu. Upewnij się, że `ACL` parametr jest rzeczywiście lista kontroli dostępu do systemu (SACL), a nie uznaniowej listy kontroli dostępu (DACL). W debugowaniu kompilacje potwierdzenia nastąpi, a `ACL` w kompilacjach wydania parametr zostanie zignorowany.

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::UsuńAce

Usuwa określony wpis ACE (wpis kontroli `CSacl` dostępu) z obiektu.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks do wpisu ACE, aby usunąć.

### <a name="remarks"></a>Uwagi

Ta metoda jest pochodną [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::UsuńWszystkie

Usuwa wszystkie wpisy kontroli dostępu (ACE) zawarte `CSacl` w obiekcie.

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa każdą `ACE` strukturę (jeśli `CSacl` istnieje) w obiekcie.

## <a name="see-also"></a>Zobacz też

[Klasa CAcl](../../atl/reference/cacl-class.md)<br/>
[Listy acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Asy](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
