---
title: IRowsetNotifyImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: 552fcdcee99f1bfe78a28c6ea41a89557f1682f4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026071"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl — Klasa

Implementuje i rejestruje [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) na odbiorców (znany także jako "obiekt sink"), dzięki czemu może obsługiwać powiadomienia.

## <a name="syntax"></a>Składnia

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[OnFieldChange](#onfieldchange)|Powiadamia konsumenta każdą zmianę wartości kolumny.|
|[OnRowChange](#onrowchange)|Powiadamia klientów zmiany pierwszy wiersz lub wszelkich zmian, który ma wpływ na cały wiersz.|
|[OnRowsetChange](#onrowsetchange)|Powiadamia klientów wszelkich zmian wpływających na cały zestaw wierszy.|

## <a name="remarks"></a>Uwagi

Zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md) dotyczących implementowania interfejsu punktu połączenia na odbiorcy.

`IRowsetNotifyImpl` dostarcza implementację zastępczy dla `IRowsetNotify`, za pomocą funkcji puste dla `IRowsetNotify` metody [onfieldchange —](/previous-versions/windows/desktop/ms715961(v=vs.85)), [onrowchange —](/previous-versions/windows/desktop/ms722694(v=vs.85)), i [onrowsetchange —](/previous-versions/windows/desktop/ms722669(v=vs.85)). Jeśli pochodne względem tej klasy, podczas implementowania `IRowsetNotify` interfejsu, można zaimplementować tylko te metody, które są potrzebne. Należy również samodzielnie pusty implementacje dla innych metod.

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange

Powiadamia konsumenta każdą zmianę wartości kolumny.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) opisy parametrów.

### <a name="return-value"></a>Wartość zwracana

Zobacz [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) dla zwracają opisy wartości.

### <a name="remarks"></a>Uwagi

Ta metoda opakowuje [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange

Powiadamia klientów zmiany pierwszy wiersz lub wszelkich zmian, który ma wpływ na cały wiersz.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) opisy parametrów.

### <a name="return-value"></a>Wartość zwracana

Zobacz [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) dla zwracają opisy wartości.

### <a name="remarks"></a>Uwagi

Ta metoda opakowuje [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange

Powiadamia klientów wszelkich zmian wpływających na cały zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) opisy parametrów.

### <a name="return-value"></a>Wartość zwracana

Zobacz [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) dla zwracają opisy wartości.

### <a name="remarks"></a>Uwagi

Ta metoda opakowuje [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[irowsetnotifycp — klasa](../../data/oledb/irowsetnotifycp-class.md)