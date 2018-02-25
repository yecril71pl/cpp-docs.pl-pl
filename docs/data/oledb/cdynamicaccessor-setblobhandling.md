---
title: CDynamicAccessor::SetBlobHandling | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 21a877cb3aa3d6ff96521348350857c141b8e7b0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
Ustawia BLOB obsługi wartość dla bieżącego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Określa sposób obsługi danych obiektów BLOB. Przyjmuje następujące wartości:  
  
-   **DBBLOBHANDLING_DEFAULT**: obsługi danych kolumny jest większa niż `nBlobSize` (jak ustawione przez `SetBlobSizeLimit`) jako obiektu BLOB danych i pobrać ją przy użyciu `ISequentialStream` lub `IStream` obiektu. Ta opcja będzie podejmować próby powiązać każdy kolumny zawierającej dane, które są większe niż `nBlobSize` lub wymienionych jako **DBTYPE_IUNKNOWN** jako dane obiektów BLOB.  
  
-   **DBBLOBHANDLING_NOSTREAMS**: obsługi danych kolumny jest większa niż `nBlobSize` (jak ustawione przez `SetBlobSizeLimit`) jako obiektu BLOB danych i pobierania jej przez odwołanie w pamięci przydzielony dostawcy, należące do użytkownika. Ta opcja przydaje się do tabel, które mają więcej niż jedną kolumnę obiektów BLOB, a dostawca obsługuje tylko jeden `ISequentialStream` obiektu na dostępu.  
  
-   **DBBLOBHANDLING_SKIP**: Pomiń (nie powiązuj) kolumny uważane za zawierające obiekty BLOB (akcesor nie będzie powiązanie lub pobrać wartości kolumny, ale nadal będzie pobierał stan kolumny i długości).  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać `SetBlobHandling` przed wywołaniem **Otwórz**.  
  
 Metody konstruktora [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) ustawia obsługi wartość do obiektu BLOB **DBBLOBHANDLING_DEFAULT**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)