---
title: _włącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca265bc8a6adc3da747e94ca67cd57749687f21
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465612"
---
# <a name="enable"></a>_enable
**Microsoft Specific**  
  
 Umożliwia przerwań.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _enable(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_enable`|x86, ARM, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_enable` powoduje, że procesor, która ma ustawienie flagi przerwania. Na x86 systemów, ta funkcja generuje Ustaw flagę przerwań (`sti`) instrukcji.  
  
 Ta funkcja jest dostępna tylko w trybie jądra. Jeśli używane w trybie użytkownika, zwracany jest wyjątek instrukcja uprzywilejowana.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)