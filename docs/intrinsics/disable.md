---
title: _disable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2748d0412c9ee0f7e7684d35a38f3c2b5d133754
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466147"
---
# <a name="disable"></a>_disable
**Microsoft Specific**  
  
 Wyłącza przerwań.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_disable`|x86, ARM, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_disable` powoduje, że procesora, aby wyczyścić flagę przerwania. Na x86 systemów, ta funkcja generuje Wyczyść flagę przerwań (`cli`) instrukcji.  
  
 Ta funkcja jest dostępna tylko w trybie jądra. Jeśli używane w trybie użytkownika, instrukcja uprzywilejowana jest wyjątek w czasie wykonywania.  
  
 Na platformach ARM, ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)