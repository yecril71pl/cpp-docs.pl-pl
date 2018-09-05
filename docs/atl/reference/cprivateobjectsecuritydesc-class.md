---
title: Klasa CPrivateObjectSecurityDesc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb24b1d00c7c70b545213a64e685f238d6b5157
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757965"
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
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Wywołaj tę metodę, aby przekonwertować do formatu, który obsługuje automatyczne propagacji wpisy dziedziczne kontroli dostępu (ACE) deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL).|
|[CPrivateObjectSecurityDesc::Create](#create)|Wywołaj tę metodę, aby przydzielić i zainicjować deskryptora zabezpieczeń autorelacyjnym dla prywatnych obiekt utworzony przez wywołującego usługi resource manager.|
|[CPrivateObjectSecurityDesc::Get](#get)|Wywołaj tę metodę, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.|
|[CPrivateObjectSecurityDesc::Set](#set)|Wywołaj tę metodę, aby zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), zawiera metody służące do tworzenia i zarządzania nimi deskryptora zabezpieczeń obiektu prywatnego.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Wywołaj tę metodę, aby przekonwertować do formatu, który obsługuje automatyczne propagacji wpisy dziedziczne kontroli dostępu (ACE) deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL).

```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Parametry

*pParent*  
Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) odwołuje się do obiektu nadrzędnego kontenera obiektu. W przypadku braku kontenera nadrzędnego, ten parametr ma wartość NULL.

*Typ obiektu*  
Wskaźnik do `GUID` strukturę, która identyfikuje typ obiekt skojarzony z bieżącym obiektem. Ustaw *ObjectType* na wartość NULL, jeśli obiekt nie jest identyfikatorem GUID.

*bIsDirectoryObject*  
Określa, czy nowy obiekt mogą zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*GenericMapping*  
Wskaźnik do [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) strukturę, która określa mapowanie z każdego ogólne prawa do określonych praw dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda próbuje określić, czy ACE arbitralnej kontroli dostępu lista (DACL) i system listy kontroli dostępu (SACL) bieżącego deskryptora zabezpieczeń były dziedziczone z nadrzędnego deskryptora zabezpieczeń. Wywołuje [ConvertToAutoInheritPrivateObjectSecurity](https://msdn.microsoft.com/library/windows/desktop/aa376403) funkcji.

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Konstruktor.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje `CPrivateObjectSecurityDesc` obiektu.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc

Destruktor.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby i usuwa deskryptora zabezpieczeń obiektu prywatnego.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Wywołaj tę metodę, aby przydzielić i zainicjować deskryptora zabezpieczeń autorelacyjnym dla prywatnych obiekt utworzony przez wywołującego usługi resource manager.

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

*pParent*  
Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiekt odwołuje się do katalogu nadrzędnego, w którym tworzony jest nowy obiekt. Jeśli katalog nadrzędny nie, należy ustawić na wartość NULL.

*pCreator*  
Wskaźnik na podany przez twórcę obiekt deskryptora zabezpieczeń. Jeśli twórca obiektu nie jawnie przekazuje informacje o zabezpieczeniach dla nowego obiektu, należy ustawić ten parametr na wartość NULL.

*bIsDirectoryObject*  
Określa, czy nowy obiekt mogą zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*Token*  
Odwołanie do [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt dla procesu klienta, w którego imieniu obiekt jest tworzony.

*GenericMapping*  
Wskaźnik do [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) strukturę, która określa mapowanie z każdego ogólne prawa do określonych praw dla obiektu.

*Typ obiektu*  
Wskaźnik do `GUID` strukturę, która identyfikuje typ obiekt skojarzony z bieżącym obiektem. Ustaw *ObjectType* na wartość NULL, jeśli obiekt nie jest identyfikatorem GUID.

*bIsContainerObject*  
Określa, czy nowy obiekt mogą zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.

*AutoInheritFlags*  
Zestaw flag bitowych, które kontrolują, jak wpisy kontroli dostępu (ACE) są dziedziczone z *pParent*. Zobacz [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CreatePrivateObjectSercurity](https://msdn.microsoft.com/library/windows/desktop/aa376405) lub [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581).

Druga metoda zezwala na określanie typu obiektu identyfikator GUID nowego obiektu lub kontrolowania, jak wpisy kontroli dostępu są dziedziczone.

> [!NOTE]
>  Deskryptor zabezpieczeń autorelacyjnym jest deskryptora zabezpieczeń, która przechowuje wszystkie informacje o zabezpieczeniach w ciągłym bloku pamięci.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Wywołaj tę metodę, aby pobrać informacje z deskryptora zabezpieczeń obiektu prywatnego.

```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Parametry

*SI*  
Zestaw flag bitowych, które wskazują częściami deskryptor zabezpieczeń do pobrania. Ta wartość może być kombinacją [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) flagi bitowe.

*pResult*  
Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiekt, który otrzymuje kopię żądanych informacji z Podany deskryptor zabezpieczeń.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Deskryptor zabezpieczeń jest struktury i skojarzone dane, który zawiera informacje dotyczące zabezpieczeń dla obiektu zabezpieczanego.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Operator przypisania.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*  
`CPrivateObjectSecurityDesc` Obiekt można przypisać do bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CPrivateObjectSecurityDesc` obiektu.

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

Wywołaj tę metodę, aby zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.

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

*SI*  
Zestaw flag bitowych, które wskazują częściami deskryptor zabezpieczeń można ustawić. Ta wartość może być kombinacją [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) flagi bitowe.

*Modyfikacja*  
Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiektu. Częściami deskryptor zabezpieczeń wskazywanym przez *si* parametru są stosowane do deskryptora zabezpieczeń obiektu.

*GenericMapping*  
Wskaźnik do [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) strukturę, która określa mapowanie z każdego ogólne prawa do określonych praw dla obiektu.

*Token*  
Odwołanie do [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt dla procesu klienta, w którego imieniu obiekt jest tworzony.

*AutoInheritFlags*  
Zestaw flag bitowych, które kontrolują, jak wpisy kontroli dostępu (ACE) są dziedziczone z *pParent*. Zobacz [CreatePrivateObjectSecurityEx](https://msdn.microsoft.com/library/windows/desktop/aa446581) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.

### <a name="remarks"></a>Uwagi

Druga metoda zezwala na określanie typu obiektu identyfikator GUID obiektu lub kontrolowania, jak wpisy kontroli dostępu są dziedziczone.

## <a name="see-also"></a>Zobacz też

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)   
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)   
[Klasa CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
