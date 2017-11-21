---
title: CDataConnection::operator BOOL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs: C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9a9cfd88e2c1ce141da2a4b345a926cdb412a2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-bool"></a>CDataConnection::operator BOOL
Określa, czy bieżąca sesja jest otwarty.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
operator BOOL( ) throw( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwraca **BOOL** wartość (MFC typedef). **Wartość TRUE,** oznacza, że bieżąca sesja jest otwarty; **FALSE** oznacza, że bieżąca sesja jest zamknięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [Cdataconnection::operator — wartość logiczna](../../data/oledb/cdataconnection-operator-bool-ole-db.md)