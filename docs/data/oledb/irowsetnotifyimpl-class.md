---
title: "Irowsetnotifyimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs: C++
helpviewer_keywords: IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7473e63c7ca67dff200d5cf96f1774ca9a2d6817
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl — Klasa
Implementuje i rejestruje [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) na konsumenta (znanej także jako "sink"), aby mogły obsługiwać powiadomień.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Powiadamia użytkownika o wszelkich zmianach wartość kolumny.|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|Powiadamia użytkownika zmiany pierwszy wiersz lub żadnych zmian, które ma wpływ na cały wiersz.|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|Powiadamia użytkownika o wszelkich zmianach wpływu na cały zestaw wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md) o implementacji interfejsu punktu połączenia dla konsumenta.  
  
 `IRowsetNotifyImpl`udostępnia implementację fikcyjny dla `IRowsetNotify`, pusty funkcje dla `IRowsetNotify` metody [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx), [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx), i [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx). Jeśli pochodne względem tej klasy w przypadku implementowania `IRowsetNotify` interfejsu, można wdrożyć tylko te metody, które są potrzebne. Należy również samodzielnie pusty implementacji dla innych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [Irowsetnotifycp — klasa](../../data/oledb/irowsetnotifycp-class.md)