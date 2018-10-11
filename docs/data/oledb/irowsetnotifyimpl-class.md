---
title: Irowsetnotifyimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ade96e5d73d86519a067d632a4e05250d1264cf
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082309"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl — Klasa

Implementuje i rejestruje [IRowsetNotify](/previous-versions/windows/desktop/ms712959) na odbiorców (znany także jako "obiekt sink"), dzięki czemu może obsługiwać powiadomienia.  
  
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
  
`IRowsetNotifyImpl` dostarcza implementację zastępczy dla `IRowsetNotify`, za pomocą funkcji puste dla `IRowsetNotify` metody [onfieldchange —](/previous-versions/windows/desktop/ms715961), [onrowchange —](/previous-versions/windows/desktop/ms722694), i [onrowsetchange —](/previous-versions/windows/desktop/ms722669). Jeśli pochodne względem tej klasy, podczas implementowania `IRowsetNotify` interfejsu, można zaimplementować tylko te metody, które są potrzebne. Należy również samodzielnie pusty implementacje dla innych metod.  

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

Zobacz [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  

Zobacz [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda opakowuje [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.  

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

Zobacz [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  

Zobacz [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda opakowuje [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje. 

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

Zobacz [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  

Zobacz [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda opakowuje [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959)   
[IRowsetNotifyCP, klasa](../../data/oledb/irowsetnotifycp-class.md)