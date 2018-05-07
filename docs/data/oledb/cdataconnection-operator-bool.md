---
title: CDataConnection::operator BOOL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5597e99b23a928df1d5052ed6354baf2dae21864
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionoperator-bool"></a>CDataConnection::operator BOOL
Określa, czy bieżąca sesja jest otwarty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
operator BOOL() throw();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwraca **BOOL** wartość (MFC typedef). **Wartość TRUE,** oznacza, że bieżąca sesja jest otwarty; **FALSE** oznacza, że bieżąca sesja jest zamknięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [Cdataconnection::operator — wartość logiczna](../../data/oledb/cdataconnection-operator-bool-ole-db.md)