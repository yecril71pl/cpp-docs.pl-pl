---
title: CDataConnection::operator CSession&amp; | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
dev_langs: C++
helpviewer_keywords:
- operator CSession&
- CSession& operator
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 526d7957eacaca5c6198c369e08d23e0d3ecc319
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-csessionamp"></a>CDataConnection::operator CSession&amp;
Zwraca odwołanie do ograniczonego `CSession` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
operator const CSession&();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten operator zwraca odwołanie do ograniczonego `CSession` obiektu pozwala przekazywać `CDataConnection` obiektu gdzie `CSession` Oczekiwano odwołania.  
  
## <a name="example"></a>Przykład  
 Jeśli masz funkcji (takich jak `func` poniżej) pobierającej `CSession` odniesienia, można użyć **CSession &** do przekazania `CDataConnection` zamiast tego obiektu.  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)