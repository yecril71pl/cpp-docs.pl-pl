---
title: __readeflags | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readeflags
dev_langs: C++
helpviewer_keywords: __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86e1497bccadf9afd6d26ec3bf4ab8b83e2a2a21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="readeflags"></a>__readeflags
Odczytuje stan programu i kontroli (EFLAGS) do rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned     int __readeflags(void);  
unsigned __int64 __readeflags(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru EFLAGS. Wartość zwracana jest 32-bitowy długo na platformie 32-bitowe i 64-bitowy długo na 64-bitowej platformy.  
  
## <a name="remarks"></a>Uwagi  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readeflags`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__writeeflags](../intrinsics/writeeflags.md)