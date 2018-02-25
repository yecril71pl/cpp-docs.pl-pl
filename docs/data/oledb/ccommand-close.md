---
title: CCommand::Close | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d25c726ef5961f7504eb72fef230a94588e7734
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandclose"></a>CCommand::Close
Zwalnia akcesor zestawu wierszy skojarzonego z poleceniem.  
  
## <a name="syntax"></a>Składnia

```cpp
void Close();  
```  
  
## <a name="remarks"></a>Uwagi  
 Polecenie używa zestawu wierszy, wynik metody dostępu set i (opcjonalnie) akcesor parametru (w przeciwieństwie do tabel, które nie obsługują parametrów i nie ma potrzeby akcesor parametru).  
  
 Podczas wykonywania polecenia, należy wywołać zarówno `Close` i [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) po poleceniu.  
  
 Umożliwia wykonanie tego samego polecenia wielokrotnie powinien wersji każdej metody dostępu set wynik przez wywołanie metody `Close` przed wywołaniem `Execute`. Na końcu serii, należy zwolnić akcesor parametru przez wywołanie metody `ReleaseCommand`. Inny typowy scenariusz powoduje wywołanie procedury przechowywanej, która ma parametry wyjściowe. W wielu dostawców (na przykład dostawca OLE DB dla programu SQL Server) wartości parametrów wyjściowych nie będą dostępne do czasu zamknięcia akcesor zestawu wyników. Wywołanie `Close` zamknąć zwróconych wierszy i metody dostępu set wynik, ale nie akcesor parametru, co pozwala na pobieranie wartości parametru wyjściowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak można wywołać `Close` i `ReleaseCommand` podczas wykonywania tego samego polecenia wielokrotnie.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand — klasa](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)