---
title: CDynamicAccessor::SetBlobHandling | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs: C++
helpviewer_keywords: SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 02b9be4b187f55d9bfb8f3ee5e572f682742f538
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
Ustawia BLOB obsługi wartość dla bieżącego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      bool SetBlobHandling(  
   DBBLOBHANDLINGENUM eBlobHandling   
);  
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