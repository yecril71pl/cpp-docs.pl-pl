---
title: __readcr3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr3
dev_langs:
- C++
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 486a21506ea4b8c388dcf495f348987c3464ddc6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465257"
---
# <a name="readcr3"></a>__readcr3
**Microsoft Specific**  
  
 Odczytuje rejestru przedsiębiorstw CR3 i zwraca jego wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __readcr3(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru przedsiębiorstw CR3.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readcr3`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)