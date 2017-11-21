---
title: __readcr8 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readcr8
dev_langs: C++
helpviewer_keywords: __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d05200d031da60ebd32707648a260b511ba4088
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="readcr8"></a>__readcr8
**Dotyczące firmy Microsoft**  
  
 Odczytuje rejestru CR8 i zwraca jego wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __readcr8(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru CR8.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readcr8`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)