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
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331415"
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
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL) do formatu, który obsługuje automatyczne propagowanie dziedzicznych wpisów kontroli dostępu (ACE).|
|[CPrivateObjectSecurityDesc::Tworzenie](#create)|Wywołanie tej metody, aby przydzielić i zainicjować samowymiarowy deskryptora zabezpieczeń dla obiektu prywatnego utworzonego przez wywołującego menedżera zasobów.|
|[CPrivateObjectSecurityDesc::Get](#get)|Wywołanie tej metody, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.|
|[CPrivateObjectSecurityDesc::Ustaw](#set)|Wywołanie tej metody, aby zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Ta klasa, pochodząca z [CSecurityDesc,](../../atl/reference/csecuritydesc-class.md)udostępnia metody tworzenia deskryptora zabezpieczeń obiektu prywatnego i zarządzania nim.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit

Wywołanie tej metody, aby przekonwertować deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL) do formatu, który obsługuje automatyczne propagowanie dziedzicznych wpisów kontroli dostępu (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odwołującego się do kontenera nadrzędnego obiektu. Jeśli nie ma kontenera nadrzędnego, ten parametr ma wartość NULL.

*Objecttype*<br/>
Wskaźnik do `GUID` struktury, która identyfikuje typ obiektu skojarzonego z bieżącym obiektem. Ustaw *typ obiektu* na WARTOŚĆ NULL, jeśli obiekt nie ma identyfikatora GUID.

*bIsDirectoryObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*Mapowanie ogólne*<br/>
Wskaźnik do [struktury GENERIC_MAPPING,](/windows/win32/api/winnt/ns-winnt-generic_mapping) która określa mapowanie z każdego ogólnego prawa do określonych praw dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje ustalić, czy wpisy dostępu na liście uznaniowej kontroli dostępu (DACL) i listy kontroli dostępu do systemu (SACL) bieżącego deskryptora zabezpieczeń zostały odziedziczone po nadrzędnym deskryptorze zabezpieczeń. Wywołuje [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) funkcji.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Konstruktor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje `CPrivateObjectSecurityDesc` obiekt.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby i usuwa deskryptor zabezpieczeń obiektu prywatnego.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Tworzenie

Wywołanie tej metody, aby przydzielić i zainicjować samowymiarowy deskryptora zabezpieczeń dla obiektu prywatnego utworzonego przez wywołującego menedżera zasobów.

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

*pRoczysz*<br/>
Wskaźnik do obiektu [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odwołującego się do katalogu nadrzędnego, w którym tworzony jest nowy obiekt. Ustaw wartość NULL, jeśli nie ma katalogu nadrzędnego.

*pCreator (pCreator)*<br/>
Wskaźnik do deskryptora zabezpieczeń dostarczonego przez twórcę obiektu. Jeśli twórca obiektu nie przekazuje jawnie informacji zabezpieczających dla nowego obiektu, ustaw ten parametr na WARTOŚĆ NULL.

*bIsDirectoryObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*Tokenu*<br/>
Odwołanie do [obiektu CAccessToken](../../atl/reference/caccesstoken-class.md) dla procesu klienta, w którego imieniu tworzony jest obiekt.

*Mapowanie ogólne*<br/>
Wskaźnik do [struktury GENERIC_MAPPING,](/windows/win32/api/winnt/ns-winnt-generic_mapping) która określa mapowanie z każdego ogólnego prawa do określonych praw dla obiektu.

*Objecttype*<br/>
Wskaźnik do `GUID` struktury, która identyfikuje typ obiektu skojarzonego z bieżącym obiektem. Ustaw *typ obiektu* na WARTOŚĆ NULL, jeśli obiekt nie ma identyfikatora GUID.

*bIsContainerObject*<br/>
Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*AutoinheritFlags*<br/>
Zestaw flag bitowych, które kontrolują sposób dziedziczenia wpisów kontroli dostępu (CE) z *pParent*. Zobacz [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) lub [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

Druga metoda pozwala na określenie identyfikatora GUID typu obiektu lub kontrolowanie sposobu dziedziczenia obiektów ACE.

> [!NOTE]
> Samowymiejsty deskryptor zabezpieczeń to deskryptor zabezpieczeń, który przechowuje wszystkie informacje o zabezpieczeniach w ciągłym bloku pamięci.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get

Wywołanie tej metody, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*Si*<br/>
Zestaw flag bitowych wskazujących części deskryptora zabezpieczeń do pobrania. Ta wartość może być kombinacją [flag bitowych SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*Presult*<br/>
Wskaźnik do obiektu [CSecurityDesc,](../../atl/reference/csecuritydesc-class.md) który odbiera kopię żądanych informacji z określonego deskryptora zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń jest strukturą i skojarzonymi danymi zawierającymi informacje o zabezpieczeniach zabezpieczanego obiektu.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =

Operator przypisania.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Obiekt `CPrivateObjectSecurityDesc` do przypisania do bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CPrivateObjectSecurityDesc` obiekt.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Ustaw

Wywołanie tej metody, aby zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.

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

*Si*<br/>
Zestaw flag bitowych wskazujących części deskryptora zabezpieczeń do ustawienia. Ta wartość może być kombinacją [flag bitowych SECURITY_INFORMATION.](/windows/win32/SecAuthZ/security-information)

*Modyfikowanie*<br/>
Wskaźnik do obiektu [CSecurityDesc.](../../atl/reference/csecuritydesc-class.md) Części tego deskryptora zabezpieczeń oznaczone parametrem *si* są stosowane do deskryptora zabezpieczeń obiektu.

*Mapowanie ogólne*<br/>
Wskaźnik do [struktury GENERIC_MAPPING,](/windows/win32/api/winnt/ns-winnt-generic_mapping) która określa mapowanie z każdego ogólnego prawa do określonych praw dla obiektu.

*Tokenu*<br/>
Odwołanie do [obiektu CAccessToken](../../atl/reference/caccesstoken-class.md) dla procesu klienta, w którego imieniu tworzony jest obiekt.

*AutoinheritFlags*<br/>
Zestaw flag bitowych, które kontrolują sposób dziedziczenia wpisów kontroli dostępu (CE) z *pParent*. Zobacz [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Druga metoda pozwala na określenie identyfikatora GUID typu obiektu lub kontrolowanie sposobu dziedziczenia obiektów ACE.

## <a name="see-also"></a>Zobacz też

[Security_descriptor](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)<br/>
[Klasa CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
