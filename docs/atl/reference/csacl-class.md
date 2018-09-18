---
title: Klasa CSacl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d408ab5d0575984fb597cec28f01484d9b878ebf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108394"
---
# <a name="csacl-class"></a>Klasa CSacl

Ta klasa jest otoką dla struktury SACL (systemowa lista kontroli dostępu).

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CSacl::AddAuditAce](#addauditace)|Dodaje wpis kontroli dostępu (ACE) inspekcji `CSacl` obiektu.|
|[CSacl::GetAceCount](#getacecount)|Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiektu.|
|[CSacl::RemoveAce](#removeace)|Usuwa określone ACE (wpis kontroli dostępu) z `CSacl` obiektu.|
|[CSacl::RemoveAllAces](#removeallaces)|Usuwa wszystkie wpisy kontroli dostępu, zawarte w `CSacl` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSacl::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

DEFINIUJ zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordów inspekcji w dzienniku zdarzeń zabezpieczeń kontrolera domeny. Należy pamiętać, że SACL generuje wpisy dziennika tylko na kontrolerze domeny, w których wystąpiła próba uzyskania dostępu, a nie na każdym kontrolerze domeny, który zawiera repliki obiektu.

Aby ustawić lub pobrać SACL w deskryptora zabezpieczeń obiektu, uprawnień SE_SECURITY_NAME musi być włączona w tokenie dostępu żądania wątku. Grupa Administratorzy ma to uprawnienie przyznane domyślnie i mogą być udzielone innym użytkownikom lub grupom. Posiadanie uprawnień przyznanych nie jest wymagane jest: przed wykonaniem operacji zdefiniowanej przez uprawnienia, uprawnień musi być włączona w token dostępu, aby zaczęły obowiązywać. Model umożliwia uprawnienia, aby włączyć tylko w przypadku operacji systemu, a następnie wyłączone, gdy nie są już potrzebne. Zobacz [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl) przykładów dotyczących włączania SE_SECURITY_NAME.

Należy użyć metod klasy dostarczonych do dodawania, usuwania, tworzyć i usuwać wpisy kontroli dostępu z `SACL` obiektu. Zobacz też [AtlGetSacl](security-global-functions.md#atlgetsacl) i [AtlSetSacl](security-global-functions.md#atlsetsacl).

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="addauditace"></a>  CSacl::AddAuditAce

Dodaje wpis kontroli dostępu (ACE) inspekcji `CSacl` obiektu.

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
[CSid](../../atl/reference/csid-class.md) obiektu.

*AccessMask*<br/>
Określa maskę uprawnień dostępu do inspekcji dla określonego `CSid` obiektu.

*bSuccess*<br/>
Określa, czy prób dozwolonych dostępu są poddawane inspekcji. Należy ustawić tą flagę na wartość PRAWDA, aby włączyć inspekcję; w przeciwnym wypadku ustaw ją na wartość false.

*bFailure*<br/>
Określa, czy prób odmowy dostępu są poddawane inspekcji. Należy ustawić tą flagę na wartość PRAWDA, aby włączyć inspekcję; w przeciwnym wypadku ustaw ją na wartość false.

*AceFlags*<br/>
Zestaw flag bitowych, określające ACE dziedziczenia.

*pObjectType*<br/>
Typ obiektu.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ACE jest dodawany do `CSacl` obiektu FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

A `CSacl` obiekt zawiera wpisy kontroli dostępu (ACE), które określają typy prób dostępu, które generują rekordów inspekcji w dzienniku zdarzeń zabezpieczeń. Metoda ta umożliwia dodanie AS, do `CSacl` obiektu.

Zobacz [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) opis różnych flag, które można ustawić w *AceFlags* parametru.

##  <a name="csacl"></a>  CSacl::CSacl

Konstruktor.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Istniejące `ACL` struktury (lista kontroli dostępu).

### <a name="remarks"></a>Uwagi

`CSacl` Obiektu można opcjonalnie utworzyć przy użyciu istniejącego `ACL` struktury. Upewnij się, że ten parametr jest system listy kontroli dostępu (SACL) i nie list arbitralnej kontroli dostępu (DACL). W przypadku kompilacji do debugowania, jeśli nie dostarczono listy DACL potwierdzenie zostanie przeprowadzona. W kompilacjach wydania wszystkie wpisy z listy DACL są ignorowane.

##  <a name="dtor"></a>  CSacl:: ~ CSacl

Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby, uzyskanych przez obiekt, w tym wszystkie wpisy kontroli dostępu (ACE).

##  <a name="getacecount"></a>  CSacl::GetAceCount

Zwraca liczbę wpisów kontroli dostępu (ACE) w `CSacl` obiektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE zawarte w `CSacl` obiektu.

##  <a name="operator_eq"></a>  CSacl::operator =

Operator przypisania.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`ACL` (Lista kontroli dostępu), aby przypisać do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CSacl` obiektu. Upewnij się, że `ACL` parametr jest w rzeczywistości systemu-listy kontroli dostępu (SACL) i nie list arbitralnej kontroli dostępu (DACL). W kompilacjach do debugowania nastąpi potwierdzenie, a w wydawanych wersjach `ACL` parametr zostanie zignorowany.

##  <a name="removeace"></a>  CSacl::RemoveAce

Usuwa określone ACE (wpis kontroli dostępu) z `CSacl` obiektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu ACE do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda jest tworzony na podstawie [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

Usuwa wszystkie wpisy kontroli dostępu (ACE) zawartych w `CSacl` obiektu.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa co `ACE` struktury (jeśli istnieją) w `CSacl` obiektu.

## <a name="see-also"></a>Zobacz też

[Klasa CAcl](../../atl/reference/cacl-class.md)<br/>
[Listy kontroli dostępu](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[Wpisy kontroli dostępu](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
