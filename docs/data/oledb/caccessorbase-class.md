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
ms.openlocfilehash: e29883b2a42010daee19f915c49c31686b232cf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233460"
---
# <a name="caccessorbase-class"></a>CAccessorBase — Klasa

Wszystkie metody dostępu w szablonach OLE DB pochodzą od tej klasy. `CAccessorBase`umożliwia jednemu zestawowi wierszy zarządzanie wieloma metod dostępu. Zawiera również powiązanie zarówno z parametrami, jak i kolumnami wyjściowymi.

## <a name="syntax"></a>Składnia

```cpp
// Replace with syntax
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Zamknij](#close)|Zamyka metody dostępu.|
|[GetHAccessor](#geth)|Pobiera dojście metody dostępu.|
|[GetNumAccessors](#getnum)|Pobiera liczbę metod dostępu utworzonych przez klasę.|
|[IsAutoAccessor](#isauto)|Testuje, czy określony akcesor jest autodostępnym.|
|[ReleaseAccessors](#release)|Zwalnia metody dostępu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase:: Close

Zamyka metody dostępu.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Należy najpierw wywołać [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) .

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase:: GetHAccessor

Pobiera dojście metody dostępu do określonego akcesora.

### <a name="syntax"></a>Składnia

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
podczas Numer przesunięcia zerowego dla metody dostępu.

### <a name="return-value"></a>Wartość zwracana

Dojście metody dostępu.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase:: GetNumAccessors

Pobiera liczbę metod dostępu utworzonych przez klasę.

### <a name="syntax"></a>Składnia

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba metod dostępu utworzonych przez klasę.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase:: IsAutoAccessor

Zwraca wartość PRAWDA, jeśli dane są automatycznie pobierane dla metody dostępu podczas operacji przenoszenia.

### <a name="syntax"></a>Składnia

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
podczas Numer przesunięcia zerowego dla metody dostępu.

### <a name="return-value"></a>Wartość zwracana

Zwraca **`true`** czy akcesor jest autodostępnym. W przeciwnym razie zwraca **`false`** .

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase:: ReleaseAccessors

Zwalnia metody dostępu utworzone przez klasę.

### <a name="syntax"></a>Składnia

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do `IUnknown` interfejsu obiektu com, dla którego utworzono metody dostępu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wywoływana z [CAccessorRowset:: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Zobacz także

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasa CAccessorBase](../../data/oledb/caccessorbase-class.md)
