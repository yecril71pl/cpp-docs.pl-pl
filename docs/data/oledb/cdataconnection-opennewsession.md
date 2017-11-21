---
title: CDataConnection::OpenNewSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
dev_langs: C++
helpviewer_keywords: OpenNewSession method
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 733834dcb7df6addd9b3953019b367f9e12951dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionopennewsession"></a>CDataConnection::OpenNewSession
Otwiera nową sesję przy użyciu bieżącego obiektu połączenia źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT OpenNewSession(   
   CSession & session    
) throw( );  
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
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)