---
title: __readmsr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readmsr
dev_langs: C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afea34f438770fb1faace8ecc40eaadf084d8028
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="readmsr"></a>__readmsr
**Dotyczące firmy Microsoft**  
  
 Generuje `rdmsr` instrukcji odczytuje rejestru specyficzne dla modelu, określony przez `register` i zwraca jego wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`register`  
 Rejestr określonego modelu do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość w określonym rejestrze.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readmsr`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
 Aby uzyskać więcej informacji zobacz dokumentację AMD.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)