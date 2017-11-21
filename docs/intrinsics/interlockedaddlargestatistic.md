---
title: _InterlockedAddLargeStatistic | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs: C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7930f1411c419fbf5f47164029fe42dd82455ff8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Dotyczące firmy Microsoft**  
  
 Wykonuje dodatek blokowanego, w którym pierwszy argument operacji jest wartość 64-bitowa.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out]`Addend`  
 Wskaźnik do pierwszego argumentu operacji dodawania. Wartość wskazywana zastępuje wynik operacji dodawania.  
  
 [in]`Value`  
 Drugi argument operacji; wartość do dodania do pierwszego argumentu operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość drugiego argumentu operacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrznej nie jest atomic, ponieważ jest wprowadzana jako dwa osobne instrukcje zablokowanym. Niepodzielne odczytu 64-bitowych, występujący w innym wątku podczas wykonywania tego wewnętrzne może spowodować niespójne wartości odczytu.  
  
 Ta funkcja działa jako bariery odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [_ReadWriteBarrier](../intrinsics/readwritebarrier.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Powoduje konflikt z x86 kompilatora](../build/conflicts-with-the-x86-compiler.md)