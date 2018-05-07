---
title: CDataConnection::CDataConnection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 267341f88886f3ff94a6b828034e8acbaa2dc0c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Tworzy i inicjuje `CDataConnection` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ds`  
 [in] Odwołanie do istniejącego połączenia danych.  
  
## <a name="remarks"></a>Uwagi  
 Zastąpienie pierwszy tworzy nową `CDataConnection` obiektu przy użyciu ustawień domyślnych.  
  
 Drugi zastąpienie tworzy nową `CDataConnection` obiektu z ustawieniami odpowiednikiem należy określić obiekt połączenia danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataConnection, klasa](../../data/oledb/cdataconnection-class.md)