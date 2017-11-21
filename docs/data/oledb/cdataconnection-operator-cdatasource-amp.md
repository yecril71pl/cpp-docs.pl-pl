---
title: CDataConnection::operator CDataSource&amp; | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs: C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc2309b7b97a97d19ff9a68895fef3ed3bda8b7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>CDataConnection::operator CDataSource&amp;
Zwraca odwołanie do ograniczonego `CDataSource` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
operator const CDataSource&() throw( );  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten operator zwraca odwołanie do ograniczonego `CDataSource` obiektu pozwala przekazywać `CDataConnection` obiektu gdzie `CDataSource` Oczekiwano odwołania.  
  
## <a name="example"></a>Przykład  
 Jeśli masz funkcji (takich jak `func` poniżej) pobierającej `CDataSource` odniesienia, można użyć **CDataSource &** do przekazania `CDataConnection` zamiast tego obiektu.  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdataconnection — klasa](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource *](../../data/oledb/cdataconnection-operator-cdatasource-star.md)