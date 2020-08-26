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
ms.openlocfilehash: f938d9e92bc2f447ecfa82f2bfb27c8fda7652ab
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845110"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl — Klasa

Implementuje i rejestruje [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) na odbiorcy (znany również jako "ujścia"), aby mógł obsługiwać powiadomienia.

## <a name="syntax"></a>Składnia

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[OnFieldChange](#onfieldchange)|Powiadamia konsumenta o wszelkich zmianach wartości kolumny.|
|[OnRowChange](#onrowchange)|Powiadamia konsumenta o pierwszej zmianie w wierszu lub o zmianie, która ma wpływ na cały wiersz.|
|[OnRowsetChange](#onrowsetchange)|Powiadamia konsumenta o wszelkich zmianach wpływających na cały zestaw wierszy.|

## <a name="remarks"></a>Uwagi

Zobacz [otrzymywanie powiadomień](../../data/oledb/receiving-notifications.md) dotyczących implementowania interfejsu punktu połączenia na odbiorcy.

`IRowsetNotifyImpl` zapewnia implementację fikcyjną dla `IRowsetNotify` , z pustymi funkcjami dla `IRowsetNotify` metod [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))i [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). W przypadku dziedziczenia z tej klasy podczas implementowania `IRowsetNotify` interfejsu można zaimplementować tylko potrzebne metody. Trzeba również samodzielnie wprowadzić puste implementacje dla innych metod.

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyImpl:: OnFieldChange

Powiadamia konsumenta o wszelkich zmianach wartości kolumny.

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

Opis parametrów można znaleźć w temacie [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) .

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać opis wartości zwracanych, zobacz [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) .

### <a name="remarks"></a>Uwagi

Ta metoda otacza metodę [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) . Aby uzyskać szczegółowe informacje, zobacz opis tej metody w dokumentacji OLE DB programisty.

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a> IRowsetNotifyImpl:: OnRowChange

Powiadamia konsumenta o pierwszej zmianie w wierszu lub o zmianie, która ma wpływ na cały wiersz.

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

Opis parametrów można znaleźć w temacie [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) .

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać opis wartości zwracanych, zobacz [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) .

### <a name="remarks"></a>Uwagi

Ta metoda otacza metodę [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) . Aby uzyskać szczegółowe informacje, zobacz opis tej metody w dokumentacji OLE DB programisty.

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyImpl:: OnRowsetChange

Powiadamia konsumenta o wszelkich zmianach wpływających na cały zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parametry

Opis parametrów można znaleźć w temacie [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) .

### <a name="return-value"></a>Wartość zwracana

Aby uzyskać opis wartości zwracanych, zobacz [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) .

### <a name="remarks"></a>Uwagi

Ta metoda otacza metodę [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) . Aby uzyskać szczegółowe informacje, zobacz opis tej metody w dokumentacji OLE DB programisty.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
 [Klasa IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)
