---
title: CDataConnection::operator CDataSource * | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs: C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3010f0774224cd02a35aeaa185bca32f370d5ba0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
Zwraca wskaźnik do zamkniętego `CDataSource` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
operator const CDataSource*() throw( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten operator zwraca wskaźnik do zamkniętego `CDataSource` obiektu pozwala przekazywać `CDataConnection` obiektu gdzie `CDataSource` oczekiwano wskaźnika.  
  
 Zobacz [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) na przykład użycia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)