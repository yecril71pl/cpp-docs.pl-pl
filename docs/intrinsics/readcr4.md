---
title: __readcr4 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readcr4
dev_langs: C++
helpviewer_keywords: __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2438ea27d7d8bee1636b4885d83562752e41c3ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="readcr4"></a>__readcr4
**Dotyczące firmy Microsoft**  
  
 Odczytuje rejestru CR4 i zwraca jego wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __readcr4(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru CR4.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readcr4`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)