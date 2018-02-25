---
title: CDynamicAccessor::CDynamicAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4d660b3e7fa537e7abd3ea2b713e5b4f7a0ce798
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
Tworzy i inicjuje `CDynamicAccessor` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Określa sposób obsługi danych dużego obiektu binarnego (BLOB). Wartość domyślna to **DBBLOBHANDLING_DEFAULT**. Zobacz [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) opis **DBBLOBHANDLINGENUM** wartości.  
  
 `nBlobSize`  
 Maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych za pośrednictwem tej wartości są traktowane jako obiektu BLOB. Wartość domyślna to 8000. Zobacz [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) szczegółowe informacje.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz konstruktora zainicjować `CDynamicAccessor` obiektu, można określić sposób powiązania obiektów blob. Obiekty BLOB może zawierać danych binarnych, takich jak grafiki, dźwięku lub skompilowanego kodu. Domyślnym zachowaniem jest Traktuj więcej niż 8000 bajtów kolumn jako obiekty BLOB, a następnie spróbuj je, aby powiązać `ISequentialStream` obiektu. Można jednak określić inną wartość na rozmiar obiektu BLOB.  
  
 Można również określić, jak `CDynamicAccessor` obsługi danych kolumny, która zaliczamy do danych obiektów BLOB: danych obiektów BLOB w ten sposób domyślne może obsługiwać; ją pominąć (nie jest powiązana) lub obiektu BLOB danych; można powiązać danych obiektów BLOB w pamięci przydzielony dostawcy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)