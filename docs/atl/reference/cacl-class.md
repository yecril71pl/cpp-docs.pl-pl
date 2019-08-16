---
title: Cacls — Klasa
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 5d03154597f800042846e82d0a0cf5e7c46b613f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497887"
---
# <a name="cacl-class"></a>Cacls — Klasa

Ta klasa jest otoką dla `ACL` struktury (lista kontroli dostępu).

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAcl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[Cacls:: CAccessMaskArray](#caccessmaskarray)|Tablica ACCESS_MASKs.|
|[Cacls:: CAceFlagArray](#caceflagarray)|Tablica bajtów.|
|[Cacls:: CAceTypeArray](#cacetypearray)|Tablica bajtów.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Cacls:: cacls](#cacl)|Konstruktor.|
|[Cacls:: ~ cacls](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Zwraca liczbę obiektów wpisów kontroli dostępu (ACE).|
|[Cacls:: GetAclEntries](#getaclentries)|Pobiera wpisy listy kontroli dostępu (ACL) z `CAcl` obiektu.|
|[Cacls:: GetAclEntry](#getaclentry)|Pobiera wszystkie informacje o wpisie w `CAcl` obiekcie.|
|[Cacls:: GetLength](#getlength)|Zwraca długość listy ACL.|
|[Cacls:: GetPACL](#getpacl)|Zwraca PACL (wskaźnik do listy ACL).|
|[Cacls:: IsEmpty](#isempty)|Testuje `CAcl` obiekt dla wpisów.|
|[Cacls:: IsNull](#isnull)|Zwraca stan `CAcl` obiektu.|
|[Cacls:: RemoveAce](#removeace)|Usuwa określony element ACE (wpis kontroli dostępu) z `CAcl` obiektu.|
|[Cacls:: RemoveAces](#removeaces)|Usuwa wszystkie ACE (wpisy kontroli dostępu) `CAcl` , które mają zastosowanie do danego. `CSid`|
|[Cacls:: SetEmpty](#setempty)|`CAcl` Oznacza obiekt jako pusty.|
|[Cacls:: SetNull](#setnull)|`CAcl` Oznacza obiekt jako wartość null.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Cacls:: operator — lista kontroli dostępu *](#operator_const_acl__star)|Rzutuje `ACL` obiekt na strukturę. `CAcl`|
|[Cacls:: operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

`ACL` Struktura jest nagłówkiem listy kontroli dostępu (ACL). Lista ACL zawiera sekwencyjną listę wartości zerowych lub większej liczby [ACE](/windows/win32/SecAuthZ/access-control-entries) (wpisy kontroli dostępu). Poszczególne wpisy kontroli dostępu są numerowane od 0 do *n-1*, gdzie *n* to liczba ACE na liście ACL. Podczas edytowania listy ACL aplikacja odwołuje się do wpisu kontroli dostępu (ACE) na liście ACL według jego indeksu.

Istnieją dwa typy list ACL:

- Poufnej

- System

Poufna lista kontroli dostępu jest kontrolowana przez właściciela obiektu lub każdy udzielił dostępu WRITE_DAC do obiektu. Określa dostęp określonych użytkowników i grup do obiektu. Na przykład właściciel pliku może używać poufnej listy kontroli dostępu do kontrolowania użytkowników i grup, które mogą i nie mogą uzyskać dostępu do pliku.

Obiekt może także mieć skojarzone z nim informacje o zabezpieczeniach na poziomie systemu w postaci listy ACL systemu kontrolowanej przez administratora systemu. Lista ACL systemu może pozwolić administratorowi systemu na inspekcję wszelkich prób uzyskania dostępu do obiektu.

Aby uzyskać więcej informacji, zobacz Omówienie [listy ACL](/windows/win32/SecAuthZ/access-control-lists) w Windows SDK.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/win32/SecAuthZ/access-control) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="caccessmaskarray"></a>Cacls:: CAccessMaskArray

Tablica obiektów ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef określa typ tablicy, który może służyć do przechowywania praw dostępu używanych w wpisach kontroli dostępu (ACE).

##  <a name="caceflagarray"></a>Cacls:: CAceFlagArray

Tablica bajtów.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef określa typ tablicy służący do definiowania flag kontroli specyficznej dla typu wpisu kontroli dostępu (ACE). Zobacz definicję [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać pełną listę możliwych flag.

##  <a name="cacetypearray"></a>Cacls:: CAceTypeArray

Tablica bajtów.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef określa typ tablicy używany do definiowania charakteru obiektów wpisów kontroli dostępu (ACE), takich jak ACCESS_ALLOWED_ACE_TYPE lub ACCESS_DENIED_ACE_TYPE. Zobacz definicję [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać pełną listę możliwych typów.

##  <a name="cacl"></a>Cacls:: cacls

Konstruktor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Istniejący `CAcl` obiekt.

### <a name="remarks"></a>Uwagi

Obiekt można opcjonalnie utworzyć przy użyciu istniejącego `CAcl` obiektu. `CAcl`

##  <a name="dtor"></a>Cacls:: ~ cacls

Destruktor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie zasoby uzyskane przez obiekt.

##  <a name="getacecount"></a>Cacls:: GetAceCount

Zwraca liczbę obiektów wpisów kontroli dostępu (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE w `CAcl` obiekcie.

##  <a name="getaclentries"></a>Cacls:: GetAclEntries

Pobiera wpisy listy kontroli dostępu (ACL) z `CAcl` obiektu.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Wskaźnik do tablicy obiektów [CSid](../../atl/reference/csid-class.md) .

*pAccessMasks*<br/>
Maski dostępu.

*pAceTypes*<br/>
Typy wpisów kontroli dostępu (ACE).

*pAceFlags*<br/>
Flagi ACE.

### <a name="remarks"></a>Uwagi

Ta metoda wypełnia parametry tablicy informacjami o każdym obiekcie Ace zawartym w `CAcl` obiekcie. Użyj wartości NULL, jeśli szczegóły dla danej tablicy nie są wymagane.

Zawartość każdej tablicy odpowiada sobie nawzajem, czyli pierwszy element `CAccessMaskArray` tablicy odnosi się do pierwszego elementu `CSidArray` w tablicy i tak dalej.

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać więcej szczegółów na temat typów i flag ACE.

##  <a name="getaclentry"></a>Cacls:: GetAclEntry

Pobiera wszystkie informacje o wpisie na liście kontroli dostępu (ACL).

```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu listy ACL do pobrania.

*Pusty PSID*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) , do którego stosuje się wpis listy ACL.

*pMask*<br/>
Maska określająca uprawnienia do udzielenia lub odmowy dostępu.

*pType*<br/>
Typ ACE.

*pFlags*<br/>
Flagi ACE.

*pObjectType*<br/>
Typ obiektu. Ta wartość zostanie ustawiona na GUID_NULL, jeśli typ obiektu nie zostanie określony w ACE lub jeśli ACE nie jest ACE obiektu.

*pInheritedObjectType*<br/>
Typ dziedziczonego obiektu. Ta wartość zostanie ustawiona na GUID_NULL, jeśli Dziedziczony typ obiektu nie jest określony w ACE lub jeśli ACE nie jest ACE obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje pobranie wszystkich informacji o indywidualnym wpisie dostępu, co zapewnia więcej informacji niż [cacls:: GetAclEntries](#getaclentries) .

Zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać więcej szczegółów na temat typów i flag ACE.

##  <a name="getlength"></a>Cacls:: GetLength

Zwraca długość listy kontroli dostępu (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wymaganą długość w bajtach wymaganą do `ACL` przechowania struktury.

##  <a name="getpacl"></a>Cacls:: GetPACL

Zwraca wskaźnik do listy kontroli dostępu (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `ACL` struktury.

##  <a name="isempty"></a>Cacls:: IsEmpty

Testuje `CAcl` obiekt dla wpisów.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość true, `CAcl` Jeśli obiekt nie ma wartości null i nie zawiera żadnych wpisów. Zwraca wartość false, `CAcl` Jeśli obiekt ma wartość null lub zawiera co najmniej jeden wpis.

##  <a name="isnull"></a>Cacls:: IsNull

Zwraca stan `CAcl` obiektu.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, `CAcl` Jeśli obiekt ma wartość null, w przeciwnym razie false.

##  <a name="operator_const_acl__star"></a>Cacls:: operator — lista kontroli dostępu *

Rzutuje `ACL` obiekt na strukturę (listę kontroli dostępu). `CAcl`

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Zwraca adres `ACL` struktury.

##  <a name="operator_eq"></a>Cacls:: operator =

Operator przypisania.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CAcl` Do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CAcl` obiektu.

##  <a name="removeace"></a>Cacls:: RemoveAce

Usuwa określony element ACE (wpis kontroli dostępu) z `CAcl` obiektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu ACE do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda pochodzi z [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>Cacls:: RemoveAces

Usuwa alls ACE (wpisy kontroli dostępu) `CAcl` , które mają zastosowanie do danego. `CSid`

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odwołanie do `CSid` obiektu.

##  <a name="setempty"></a>Cacls:: SetEmpty

`CAcl` Oznacza obiekt jako pusty.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Uwagi

`CAcl` Można ustawić wartość pustą lub null: dwa stany są różne.

##  <a name="setnull"></a>Cacls:: SetNull

`CAcl` Oznacza obiekt jako wartość null.

```
void SetNull() throw();
```

### <a name="remarks"></a>Uwagi

`CAcl` Można ustawić wartość pustą lub null: dwa stany są różne.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
