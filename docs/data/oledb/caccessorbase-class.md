---
title: CAccessorBase — Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 34c92f9057f2273d57b69bdb42c49a81923c3d2a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034955"
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
|[Zamknięcie](#close)|Zamyka metod dostępu.|
|[Gethaccessor —](#geth)|Pobiera dojście metody dostępu.|
|[GetNumAccessors](#getnum)|Pobiera liczbę metod dostępu tworzone przez klasę.|
|[IsAutoAccessor](#isauto)|Sprawdza, czy określonej metody dostępu jest autoaccessor.|
|[ReleaseAccessors](#release)|Udostępnia metody dostępu.|

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

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — kompendium](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase — Klasa](../../data/oledb/caccessorbase-class.md)