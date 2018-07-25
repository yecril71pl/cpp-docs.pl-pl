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
ms.openlocfilehash: 8b39a5428fa5ba57e38e0190255ac0dcf60b1a5e
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233714"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl — Klasa
Implementuje i rejestruje [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx) na odbiorców (znany także jako "obiekt sink"), dzięki czemu może obsługiwać powiadomienia.  
  
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
  
 `IRowsetNotifyImpl` dostarcza implementację zastępczy dla `IRowsetNotify`, za pomocą funkcji puste dla `IRowsetNotify` metody [onfieldchange —](https://msdn.microsoft.com/library/ms715961.aspx), [onrowchange —](https://msdn.microsoft.com/library/ms722694.aspx), i [onrowsetchange —](https://msdn.microsoft.com/library/ms722669.aspx). Jeśli pochodne względem tej klasy, podczas implementowania `IRowsetNotify` interfejsu, można zaimplementować tylko te metody, które są potrzebne. Należy również samodzielnie pusty implementacje dla innych metod.  

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
 Zobacz [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda opakowuje [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.  

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
 Zobacz [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda opakowuje [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje. 

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
 Zobacz [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) opisy parametrów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) dla zwracają opisy wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda opakowuje [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) metody. Zobacz opis tej metody w odwołaniu OLE DB programisty, aby uzyskać szczegółowe informacje.
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx)   
 [IRowsetNotifyCP, klasa](../../data/oledb/irowsetnotifycp-class.md)