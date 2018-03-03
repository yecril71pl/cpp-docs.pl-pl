---
title: __p__fmode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 341eab038db17b39e5b2a408db7c61c69d432fe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pfmode"></a>__p__fmode
Wskazuje `_fmode` zmiennej globalnej, która określa domyślny *tryb tłumaczenia pliku* dla operacji We/Wy pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `_fmode` zmiennej globalnej.  
  
## <a name="remarks"></a>Uwagi  
 `__p__fmode` Funkcji jest tylko do użytku wewnętrznego i nie powinna być wywoływana z kodu użytkownika.  
  
 Określa tryb tłumaczenia pliku `binary` lub `text` Translacja [_otwórz](../c-runtime-library/reference/open-wopen.md) i [_pipe —](../c-runtime-library/reference/pipe.md) operacji We/Wy. Aby uzyskać więcej informacji, zobacz [_fmode —](../c-runtime-library/fmode.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__p\__fmode —|stdlib.h|