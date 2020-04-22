---
title: Klasa CAcl
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
ms.openlocfilehash: 458f7cd50462a145d005f3f81d87cc06fc7e01b1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748774"
---
# <a name="cacl-class"></a>Klasa CAcl

Ta klasa jest otoką `ACL` dla struktury (lista kontroli dostępu).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAcl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Tablica ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Tablica BYTEs.|
|[CAcl::CAceTypeArray](#cacetypearray)|Tablica BYTEs.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Konstruktor.|
|[CAcl::~CAcl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Zwraca liczbę obiektów wejścia kontroli dostępu (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Pobiera wpisy listy kontroli dostępu (ACL) `CAcl` z obiektu.|
|[CAcl::GetAclEntry](#getaclentry)|Pobiera wszystkie informacje o wpisie `CAcl` w obiekcie.|
|[CAcl::GetLength](#getlength)|Zwraca długość listy ACL.|
|[CAcl::GetPACL](#getpacl)|Zwraca pacl (wskaźnik do listy ACL).|
|[CAcl::IsEmpty](#isempty)|Testuje `CAcl` obiekt pod kątem wpisów.|
|[CAcl::Isnull](#isnull)|Zwraca stan `CAcl` obiektu.|
|[CAcl::RemoveAce](#removeace)|Usuwa określony wpis ACE (wpis kontroli `CAcl` dostępu) z obiektu.|
|[CAcl::RemoveAces](#removeaces)|Usuwa wszystkie wpisy ACE (wpisy `CAcl` kontroli dostępu) `CSid`z tych, które mają zastosowanie do danego .|
|[CAcl::SetEmpty](#setempty)|Oznacza `CAcl` obiekt jako pusty.|
|[CAcl::SetNull](#setnull)|Oznacza `CAcl` obiekt jako NULL.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAcl::operator const ACL *](#operator_const_acl__star)|Rzutuje `CAcl` obiekt na `ACL` strukturę.|
|[CAcl::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Struktura `ACL` jest nagłówkiem listy ACL (listy kontroli dostępu). Lista ACL zawiera sekwencyjną listę zero lub więcej [wpisów ACE](/windows/win32/SecAuthZ/access-control-entries) (wpisy kontroli dostępu). Poszczególne ACE w ACL są numerowane od 0 do *n-1*, gdzie *n* jest liczbą ACE w ACL. Podczas edytowania listy ACL aplikacja odwołuje się do wpisu kontroli dostępu (ACE) w acl przez jego indeks.

Istnieją dwa typy ACL:

- Uznaniowe

- System

Dyskrecjonalny ACL jest kontrolowany przez właściciela obiektu lub osobę, która udzieliła WRITE_DAC dostępu do obiektu. Określa dostęp poszczególnych użytkowników i grup może mieć do obiektu. Na przykład właściciel pliku może użyć dyskrecjonacyjnej listy ACL do kontrolowania, którzy użytkownicy i grupy mogą i nie mogą mieć dostępu do pliku.

Obiekt może również mieć powiązane z nim informacje zabezpieczeń na poziomie systemu w postaci listy ACL systemu kontrolowanej przez administratora systemu. ACL systemu może umożliwić administratorowi systemu do inspekcji wszelkich prób uzyskania dostępu do obiektu.

Aby uzyskać więcej informacji, zobacz dyskusję na listy [ACL](/windows/win32/SecAuthZ/access-control-lists) w programie Windows SDK.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Tablica obiektów ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Uwagi

Ta typedef określa typ tablicy, który może służyć do przechowywania praw dostępu używanych we wpisach kontroli dostępu (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray

Tablica BYTEs.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Uwagi

Ta typedef określa typ tablicy używany do definiowania flag sterujących typu ace (access-control) . Pełna lista możliwych flag znajduje się w [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) definicji.

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray

Tablica BYTEs.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Uwagi

Ta typedef określa typ tablicy używany do definiowania charakteru obiektu wpisu kontroli dostępu (ACE), takiego jak ACCESS_ALLOWED_ACE_TYPE lub ACCESS_DENIED_ACE_TYPE. Pełna lista możliwych typów znajduje się w [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) definicji.

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

Konstruktor.

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Istniejący `CAcl` obiekt.

### <a name="remarks"></a>Uwagi

Obiekt `CAcl` można opcjonalnie utworzyć przy `CAcl` użyciu istniejącego obiektu.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl::~CAcl

Destruktor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszelkie zasoby nabyte przez obiekt.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount

Zwraca liczbę obiektów wejścia kontroli dostępu (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów ACE `CAcl` w obiekcie.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries

Pobiera wpisy listy kontroli dostępu (ACL) `CAcl` z obiektu.

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*PSydy*<br/>
Wskaźnik do tablicy obiektów [CSid.](../../atl/reference/csid-class.md)

*maska pAccess*<br/>
Maski dostępu.

*pAceTypy*<br/>
Typy wpisu kontroli dostępu (ACE).

*pAceSlags*<br/>
Flagi ACE.

### <a name="remarks"></a>Uwagi

Ta metoda wypełnia parametry tablicy szczegółami każdego obiektu ACE znajdującego `CAcl` się w obiekcie. Użyj null, gdy szczegóły dla tej konkretnej tablicy nie są wymagane.

Zawartość każdej tablicy odpowiadają sobie nawzajem, oznacza to, że pierwszy element `CAccessMaskArray` tablicy odpowiada pierwszemu elementowi w `CSidArray` tablicy i tak dalej.

Zobacz [ACE_HEADER,](/windows/win32/api/winnt/ns-winnt-ace_header) aby uzyskać więcej informacji na temat typów i flag ACE.

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry

Pobiera wszystkie informacje o wpisie na liście kontroli dostępu (ACL).

```cpp
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

*Nindex*<br/>
Indeks do wpisu listy ACL do pobrania.

*pSid*<br/>
Obiekt [CSid,](../../atl/reference/csid-class.md) do którego ma zastosowanie wpis ACL.

*pMask (mask)*<br/>
Maska określająca uprawnienia do udzielania lub odmowy dostępu.

*pTyp*<br/>
Typ ACE.

*pFlags*<br/>
Flagi ACE.

*pObiektyp*<br/>
Typ obiektu. Zostanie to ustawione na GUID_NULL, jeśli typ obiektu nie jest określony w ACE lub jeśli wpis ACE nie jest obiektem ACE.

*pInheritedObjectType*<br/>
Typ obiektu dziedziczonego. Zostanie to ustawione na GUID_NULL, jeśli typ obiektu dziedziczonego nie jest określony w ACE lub jeśli wpis ACE nie jest obiektem ACE.

### <a name="remarks"></a>Uwagi

Ta metoda będzie pobierać wszystkie informacje o poszczególnych ACE, zapewniając więcej informacji niż [CAcl::GetAclEntries](#getaclentries) sam udostępnia.

Zobacz [ACE_HEADER,](/windows/win32/api/winnt/ns-winnt-ace_header) aby uzyskać więcej informacji na temat typów i flag ACE.

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl::GetLength

Zwraca długość listy kontroli dostępu (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wymaganą długość w bajtach `ACL` niezbędną do przechowywania konstrukcji.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Zwraca wskaźnik do listy kontroli dostępu (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `ACL` struktury.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::IsEmpty

Testuje `CAcl` obiekt pod kątem wpisów.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość `CAcl` PRAWDA, jeśli obiekt nie ma wartości NULL i nie zawiera żadnych wpisów. Zwraca wartość `CAcl` FAŁSZ, jeśli obiekt ma wartość NULL lub zawiera co najmniej jeden wpis.

## <a name="caclisnull"></a><a name="isnull"></a>CAcl::Isnull

Zwraca stan `CAcl` obiektu.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CAcl` PRAWDA, jeśli obiekt ma wartość NULL, wartość FAŁSZ w przeciwnym razie.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::operator const ACL *

Rzutuje `CAcl` obiekt na `ACL` strukturę (lista kontroli dostępu).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Zwraca adres `ACL` struktury.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::operator =

Operator przypisania.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Aby `CAcl` przypisać do istniejącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CAcl` zaktualizowanego obiektu.

## <a name="caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce

Usuwa określony wpis ACE (wpis kontroli `CAcl` dostępu) z obiektu.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks do wpisu ACE, aby usunąć.

### <a name="remarks"></a>Uwagi

Ta metoda jest pochodną [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Usuwa wszystkie wpisy ACE (wpisy kontroli `CAcl` dostępu) z `CSid`tych, które mają zastosowanie do danego .

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
Odwołanie do `CSid` obiektu.

## <a name="caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty

Oznacza `CAcl` obiekt jako pusty.

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>Uwagi

Można `CAcl` ustawić na pusty lub null: dwa stany są różne.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::SetNull

Oznacza `CAcl` obiekt jako NULL.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Uwagi

Można `CAcl` ustawić na pusty lub null: dwa stany są różne.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
