---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2fac05c1380e2b612cb39994716387d99bef237
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
Ustawia maksymalny rozmiar obiektu BLOB w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBlobSize`  
 Określa limit rozmiaru obiektu BLOB.  
  
## <a name="remarks"></a>Uwagi  
 Ustawia maksymalny rozmiar obiektu BLOB w bajtach; kolumny danych większych niż ta wartość jest traktowany jako obiektu BLOB. Niektórzy dostawcy zapewniają bardzo duże rozmiary kolumn (na przykład 2 GB). Zamiast próbuje przydzielić pamięci dla kolumny tego rozmiaru, czy zwykle spróbuj powiązać te kolumny jako obiekty BLOB. Dzięki temu nie trzeba przydzielić jej całą pamięć, ale nadal można odczytać wszystkich danych bez obawy obcięcie. Jednak istnieją przypadki, w których można wymusić `CDynamicAccessor` powiązać dużych kolumn w ich typach danych w trybie macierzystym. Aby to zrobić, należy wywołać `SetBlobSizeLimit` przed wywołaniem **Otwórz**.  
  
 Metody konstruktora [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) Ustawia maksymalny rozmiar obiektu BLOB do wartości domyślnej 8000 bajtów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)