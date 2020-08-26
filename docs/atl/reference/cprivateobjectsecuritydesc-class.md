---
title: Klasa CPrivateObjectSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: f62d289418280a05f390bf9cdec23ea30632aed2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833507"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Klasa CPrivateObjectSecurityDesc

Ta klasa reprezentuje obiekt deskryptora zabezpieczeń obiektu prywatnego.

## <a name="syntax"></a>Składnia

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Konstruktor.|
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Wywołaj tę metodę, aby przekonwertować deskryptor zabezpieczeń i jego listy kontroli dostępu (ACL) na format obsługujący automatyczną propagację dziedziczonych wpisów kontroli dostępu (ACE).|
|[CPrivateObjectSecurityDesc:: Create](#create)|Wywołaj tę metodę, aby przydzielić i zainicjować deskryptor zabezpieczeń dla samego siebie dla obiektu prywatnego utworzonego przez wywołującego Menedżera zasobów.|
|[CPrivateObjectSecurityDesc:: Get](#get)|Wywołaj tę metodę, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.|
|[CPrivateObjectSecurityDesc:: Set](#set)|Wywołaj tę metodę, aby zmodyfikować deskryptor zabezpieczeń obiektu prywatnego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Ta klasa, pochodna od [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), zapewnia metody tworzenia deskryptora zabezpieczeń obiektu prywatnego i zarządzania nim.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/win32/SecAuthZ/access-control) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a> CPrivateObjectSecurityDesc::ConvertToAutoInherit

Wywołaj tę metodę, aby przekonwertować deskryptor zabezpieczeń i jego listy kontroli dostępu (ACL) na format obsługujący automatyczną propagację dziedziczonych wpisów kontroli dostępu (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odwołującego się do kontenera nadrzędnego obiektu. Jeśli nie ma kontenera nadrzędnego, ten parametr ma wartość NULL.

*ObjectType*<br/>
Wskaźnik do `GUID` struktury, która identyfikuje typ obiektu skojarzonego z bieżącym obiektem. Jeśli obiekt nie ma identyfikatora GUID, należy ustawić dla elementu *ObjectType* wartość null.

*bIsDirectoryObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*GenericMapping*<br/>
Wskaźnik do struktury [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , która określa mapowanie od poszczególnych rodzajów prawa do określonych praw dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje określić, czy asy na poufnej liście kontroli dostępu (DACL) i systemowej listy kontroli dostępu (SACL) obecnego deskryptora zabezpieczeń były dziedziczone z nadrzędnego deskryptora zabezpieczeń. Wywołuje funkcję [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) .

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a> CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Konstruktor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje `CPrivateObjectSecurityDesc` obiekt.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a> CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzieloną zasoby i usuwa deskryptor zabezpieczeń obiektu prywatnego.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a> CPrivateObjectSecurityDesc:: Create

Wywołaj tę metodę, aby przydzielić i zainicjować deskryptor zabezpieczeń dla samego siebie dla obiektu prywatnego utworzonego przez wywołującego Menedżera zasobów.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odwołujący się do katalogu nadrzędnego, w którym tworzony jest nowy obiekt. Ustaw wartość NULL, jeśli nie ma katalogu nadrzędnego.

*pCreator*<br/>
Wskaźnik do deskryptora zabezpieczeń dostarczonego przez twórcę obiektu. Jeśli twórca obiektu nie przekazuje jawnie informacji o zabezpieczeniach dla nowego obiektu, ustaw ten parametr na wartość NULL.

*bIsDirectoryObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*Token*<br/>
Odwołanie do obiektu [CAccessToken](../../atl/reference/caccesstoken-class.md) dla procesu klienta, na którym tworzony jest obiekt.

*GenericMapping*<br/>
Wskaźnik do struktury [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , która określa mapowanie od poszczególnych rodzajów prawa do określonych praw dla obiektu.

*ObjectType*<br/>
Wskaźnik do `GUID` struktury, która identyfikuje typ obiektu skojarzonego z bieżącym obiektem. Jeśli obiekt nie ma identyfikatora GUID, należy ustawić dla elementu *ObjectType* wartość null.

*bIsContainerObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*AutoInheritFlags*<br/>
Zestaw flag bitowych kontrolujących sposób, w jaki wpisy kontroli dostępu (ACE) są dziedziczone z *pParent*. Aby uzyskać więcej informacji, zobacz [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) lub [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

Druga metoda pozwala określić identyfikator GUID obiektu nowego obiektu lub kontrolować sposób dziedziczenia ACE.

> [!NOTE]
> Samodzielny deskryptor zabezpieczeń jest deskryptorem zabezpieczeń, który przechowuje wszystkie informacje o zabezpieczeniach w ciągłym bloku pamięci.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a> CPrivateObjectSecurityDesc:: Get

Wywołaj tę metodę, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*tożsamości*<br/>
Zestaw flag bitowych wskazujących części deskryptora zabezpieczeń do pobrania. Ta wartość może być kombinacją [SECURITY_INFORMATIONych](/windows/win32/SecAuthZ/security-information) flag bitowych.

*pResult*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) , który otrzymuje kopię żądanych informacji z określonego deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń to struktura i powiązane dane, które zawierają informacje o zabezpieczeniach zabezpieczanego obiektu.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a> CPrivateObjectSecurityDesc:: operator =

Operator przypisania.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CPrivateObjectSecurityDesc`Obiekt, który ma zostać przypisany do bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CPrivateObjectSecurityDesc` obiekt.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a> CPrivateObjectSecurityDesc:: Set

Wywołaj tę metodę, aby zmodyfikować deskryptor zabezpieczeń obiektu prywatnego.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Parametry

*tożsamości*<br/>
Zestaw flag bitowych wskazujących części deskryptora zabezpieczeń, które mają zostać ustawione. Ta wartość może być kombinacją [SECURITY_INFORMATIONych](/windows/win32/SecAuthZ/security-information) flag bitowych.

*Modyfikowanie*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) . Części tego deskryptora zabezpieczeń wskazywane przez parametr *si* są stosowane do deskryptora zabezpieczeń obiektu.

*GenericMapping*<br/>
Wskaźnik do struktury [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) , która określa mapowanie od poszczególnych rodzajów prawa do określonych praw dla obiektu.

*Token*<br/>
Odwołanie do obiektu [CAccessToken](../../atl/reference/caccesstoken-class.md) dla procesu klienta, na którym tworzony jest obiekt.

*AutoInheritFlags*<br/>
Zestaw flag bitowych kontrolujących sposób, w jaki wpisy kontroli dostępu (ACE) są dziedziczone z *pParent*. Aby uzyskać więcej informacji, zobacz [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Druga metoda pozwala określić typ obiektu GUID obiektu lub kontrolować sposób dziedziczenia ACE.

## <a name="see-also"></a>Zobacz też

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)<br/>
[Klasa CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
