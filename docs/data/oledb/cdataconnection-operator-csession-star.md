---
title: CDataConnection::operator CSession * | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs:
- C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 957e13346cb187540c21cbec71a642a917b69908
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
Zwraca wskaźnik do zamkniętego `CSession` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
operator const CSession*() throw();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten operator zwraca wskaźnik do zamkniętego `CSession` obiektu pozwala przekazywać `CDataConnection` obiektu gdzie `CSession` oczekiwano wskaźnika.  
  
## <a name="example"></a>Przykład  
 Zobacz [operator CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) na przykład użycia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)