---
title: CDataConnection::operator CDataSource * | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs:
- C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bade9d813fb9804ae353f7c5139f063f278da225
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
Zwraca wskaźnik do zamkniętego `CDataSource` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
operator const CDataSource*() throw();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten operator zwraca wskaźnik do zamkniętego `CDataSource` obiektu pozwala przekazywać `CDataConnection` obiektu gdzie `CDataSource` oczekiwano wskaźnika.  
  
 Zobacz [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) na przykład użycia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)