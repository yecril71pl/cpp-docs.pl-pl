---
title: CDataConnection::OpenNewSession | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
dev_langs:
- C++
helpviewer_keywords:
- OpenNewSession method
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f20f66ec6cc494c14e99c50de4824ba68d27264d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094325"
---
# <a name="cdataconnectionopennewsession"></a>CDataConnection::OpenNewSession
Otwiera nową sesję przy użyciu bieżącego obiektu połączenia źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenNewSession(CSession & session) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [We/Wy] Odwołanie do obiektu nowej sesji.  
  
 **Uwagi**  
 Nowej sesji używa obiektu źródła danych zawartych w niej bieżącego obiektu połączenia, jak jego obiekt nadrzędny, a dostęp do wszystkich tych samych informacji dotyczących źródła danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataConnection, klasa](../../data/oledb/cdataconnection-class.md)