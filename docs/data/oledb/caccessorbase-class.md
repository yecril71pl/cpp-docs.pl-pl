---
title: Caccessorbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e62c4242513c5147dcfd84ee5d69ec51a4816d1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053334"
---
# <a name="caccessorbase-class"></a>CAccessorBase — Klasa

Wszystkie metody dostępu przesłanianej w szablonach OLE DB pochodzi od tej klasy. `CAccessorBase` Umożliwia jeden zestaw wierszy do zarządzania wielu metod dostępu. Umożliwia także powiązanie dla kolumny wyjściowe i parametry.

## <a name="syntax"></a>Składnia

```cpp
// Replace with syntax
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Zamknij](#close)|Zamyka metod dostępu.|
|[GetHAccessor](#geth)|Pobiera dojście metody dostępu.|
|[Getnumaccessors —](#getnum)|Pobiera liczbę metod dostępu tworzone przez klasę.|
|[IsAutoAccessor](#isauto)|Sprawdza, czy określonej metody dostępu jest autoaccessor.|
|[Releaseaccessors —](#release)|Udostępnia metody dostępu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="close"></a> CAccessorBase::Close

Zamyka metod dostępu.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Należy wywołać [releaseaccessors —](../../data/oledb/caccessorbase-releaseaccessors.md) pierwszy.

## <a name="geth"></a> CAccessorBase::GetHAccessor

Pobiera dojście metody dostępu określonej metody dostępu.

### <a name="syntax"></a>Składnia

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
[in] Numer przesunięcie zero akcesor.

### <a name="return-value"></a>Wartość zwracana

Dojście metody dostępu.

## <a name="getnum"></a> CAccessorBase::GetNumAccessors

Pobiera liczbę metod dostępu tworzone przez klasę.

### <a name="syntax"></a>Składnia

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba metod dostępu tworzone przez klasę.

## <a name="isauto"></a> CAccessorBase::IsAutoAccessor

Zwraca wartość PRAWDA, jeśli dane są automatycznie pobierane dla metody dostępu podczas operacji przenoszenia.

### <a name="syntax"></a>Składnia

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
[in] Numer przesunięcie zero akcesor.

### <a name="return-value"></a>Wartość zwracana

Zwraca **true** autoaccessor przypadku akcesor. W przeciwnym razie zwraca **false**.

## <a name="release"></a> CAccessorBase::ReleaseAccessors

Udostępnia metody dostępu tworzone przez klasę.

### <a name="syntax"></a>Składnia

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Wskaźnik do `IUnknown` interfejs dla obiektu COM, dla którego utworzono metody dostępu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Wywoływane z [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase, klasa](../../data/oledb/caccessorbase-class.md)