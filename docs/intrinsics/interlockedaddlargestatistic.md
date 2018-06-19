---
title: _InterlockedAddLargeStatistic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 602cfb415c17c9e57d9fc1e932777cd1929e5f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331400"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Microsoft Specific**  
  
 Wykonuje dodatek blokowanego, w którym pierwszy argument operacji jest wartość 64-bitowa.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out] `Addend`  
 Wskaźnik do pierwszego argumentu operacji dodawania. Wartość wskazywana zastępuje wynik operacji dodawania.  
  
 [in] `Value`  
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
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)