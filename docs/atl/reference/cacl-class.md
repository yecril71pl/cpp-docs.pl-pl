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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864908"
---
# <a name="cacl-class"></a>Cacls — Klasa

Ta klasa jest otoką dla struktury `ACL` (lista kontroli dostępu).

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAcl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Cacls:: CAccessMaskArray](#caccessmaskarray)|Tablica ACCESS_MASKs.|
|[Cacls:: CAceFlagArray](#caceflagarray)|Tablica bajtów.|
|[Cacls:: CAceTypeArray](#cacetypearray)|Tablica bajtów.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Cacls:: cacls](#cacl)|Konstruktor.|
|[Cacls:: ~ cacls](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Cacls:: GetAceCount](#getacecount)|Zwraca liczbę obiektów wpisów kontroli dostępu (ACE).|
|[Cacls:: GetAclEntries](#getaclentries)|Pobiera wpisy listy kontroli dostępu (ACL) z obiektu `CAcl`.|
|[Cacls:: GetAclEntry](#getaclentry)|Pobiera wszystkie informacje o wpisie w obiekcie `CAcl`.|
|[Cacls:: GetLength](#getlength)|Zwraca długość listy ACL.|
|[Cacls:: GetPACL](#getpacl)|Zwraca PACL (wskaźnik do listy ACL).|
|[Cacls:: IsEmpty](#isempty)|Testuje `CAcl` obiektu dla wpisów.|
|[Cacls:: IsNull](#isnull)|Zwraca stan obiektu `CAcl`.|
|[Cacls:: RemoveAce](#removeace)|Usuwa określoną wartość ACE (wpis kontroli dostępu) z obiektu `CAcl`.|
|[Cacls:: RemoveAces](#removeaces)|Usuwa wszystkie ACE (wpisy kontroli dostępu) z `CAcl`, które mają zastosowanie do danego `CSid`.|
|[Cacls:: SetEmpty](#setempty)|Oznacza obiekt `CAcl` jako pusty.|
|[Cacls:: SetNull](#setnull)|Oznacza obiekt `CAcl` jako wartość NULL.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Cacls:: operator — lista kontroli dostępu *](#operator_const_acl__star)|Rzutuje obiekt `CAcl` na strukturę `ACL`.|
|[Cacls:: operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Struktura `ACL` jest nagłówkiem listy ACL (lista kontroli dostępu). Lista ACL zawiera sekwencyjną listę wartości zerowych lub większej liczby [ACE](/windows/win32/SecAuthZ/access-control-entries) (wpisy kontroli dostępu). Poszczególne wpisy kontroli dostępu są numerowane od 0 do *n-1*, gdzie *n* to liczba ACE na liście ACL. Podczas edytowania listy ACL aplikacja odwołuje się do wpisu kontroli dostępu (ACE) na liście ACL według jego indeksu.

Istnieją dwa typy list ACL:

- Poufnej

- System

Poufna lista kontroli dostępu jest kontrolowana przez właściciela obiektu lub każdego, kto udzielił WRITE_DAC dostępu do obiektu. Określa dostęp określonych użytkowników i grup do obiektu. Na przykład właściciel pliku może używać poufnej listy kontroli dostępu do kontrolowania użytkowników i grup, które mogą i nie mogą uzyskać dostępu do pliku.

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

Ten element typedef określa typ tablicy służący do definiowania flag kontroli specyficznej dla typu wpisu kontroli dostępu (ACE). Zapoznaj się z definicją [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać pełną listę możliwych flag.

##  <a name="cacetypearray"></a>Cacls:: CAceTypeArray

Tablica bajtów.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Uwagi

Ten element typedef określa typ tablicy używany do definiowania charakteru obiektów wpisów kontroli dostępu (ACE), takich jak ACCESS_ALLOWED_ACE_TYPE lub ACCESS_DENIED_ACE_TYPE. Zapoznaj się z definicją [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) , aby uzyskać pełną listę możliwych typów.

##  <a name="cacl"></a>Cacls:: cacls

Konstruktor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Istniejący obiekt `CAcl`.

### <a name="remarks"></a>Uwagi

Obiekt `CAcl` można opcjonalnie utworzyć przy użyciu istniejącego obiektu `CAcl`.

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

### <a name="return-value"></a>Wartość zwrócona

Zwraca liczbę wpisów ACE w obiekcie `CAcl`.

##  <a name="getaclentries"></a>Cacls:: GetAclEntries

Pobiera wpisy listy kontroli dostępu (ACL) z obiektu `CAcl`.

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

Ta metoda wypełnia parametry tablicy informacjami o każdym obiekcie ACE zawartym w obiekcie `CAcl`. Użyj wartości NULL, jeśli szczegóły dla danej tablicy nie są wymagane.

Zawartość każdej tablicy odpowiada sobie nawzajem, czyli pierwszy element tablicy `CAccessMaskArray` odnosi się do pierwszego elementu w tablicy `CSidArray` i tak dalej.

Aby uzyskać więcej informacji na temat typów i flag ACE, zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

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

Aby uzyskać więcej informacji na temat typów i flag ACE, zobacz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

##  <a name="getlength"></a>Cacls:: GetLength

Zwraca długość listy kontroli dostępu (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wymaganą długość w bajtach wymaganą do przechowywania struktury `ACL`.

##  <a name="getpacl"></a>Cacls:: GetPACL

Zwraca wskaźnik do listy kontroli dostępu (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wskaźnik do struktury `ACL`.

##  <a name="isempty"></a>Cacls:: IsEmpty

Testuje `CAcl` obiektu dla wpisów.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość TRUE, jeśli obiekt `CAcl` nie ma wartości NULL i nie zawiera żadnych wpisów. Zwraca wartość FALSE, jeśli obiekt `CAcl` ma wartość NULL lub zawiera co najmniej jeden wpis.

##  <a name="isnull"></a>Cacls:: IsNull

Zwraca stan obiektu `CAcl`.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE, jeśli obiekt `CAcl` ma wartość NULL, w przeciwnym razie FALSE.

##  <a name="operator_const_acl__star"></a>Cacls:: operator — lista kontroli dostępu *

Rzutuje obiekt `CAcl` na strukturę `ACL` (lista kontroli dostępu).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Zwraca adres struktury `ACL`.

##  <a name="operator_eq"></a>Cacls:: operator =

Operator przypisania.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CAcl` do przypisania do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca odwołanie do zaktualizowanego obiektu `CAcl`.

##  <a name="removeace"></a>Cacls:: RemoveAce

Usuwa określoną wartość ACE (wpis kontroli dostępu) z obiektu `CAcl`.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wpisu ACE do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda pochodzi z [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>Cacls:: RemoveAces

Usuwa alls ACE (wpisy kontroli dostępu) z `CAcl`, które mają zastosowanie do danego `CSid`.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odwołanie do obiektu `CSid`.

##  <a name="setempty"></a>Cacls:: SetEmpty

Oznacza obiekt `CAcl` jako pusty.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Uwagi

`CAcl` można ustawić na wartość pustą lub NULL: dwa stany są różne.

##  <a name="setnull"></a>Cacls:: SetNull

Oznacza obiekt `CAcl` jako wartość NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Uwagi

`CAcl` można ustawić na wartość pustą lub NULL: dwa stany są różne.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
