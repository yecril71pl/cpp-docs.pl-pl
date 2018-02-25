---
title: __svm_vmrun | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 988a045bc957d5920fee7e3e659d7a0b4f02d8d2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="svmvmrun"></a>__svm_vmrun
**Microsoft Specific**  
  
 Rozpoczyna wykonywanie kodu gościa maszyny wirtualnej, która odpowiada bloku sterowania określonej maszyny wirtualnej (VMCB).  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|Adres fizyczny VMCB.|  
  
## <a name="remarks"></a>Uwagi  
 `__svm_vmrun` Funkcja używa minimalnej ilości informacji w VMCB, aby rozpocząć wykonywanie kodu gościa maszyny wirtualnej. Użyj [__svm_vmsave](../intrinsics/svm-vmsave.md) lub [__svm_vmload](../intrinsics/svm-vmload.md) funkcji, jeśli potrzebujesz więcej informacji do obsługi złożonych przerwania lub przełączyć się do innego gościa.  
  
 `__svm_vmrun` Funkcji jest odpowiednikiem `VMRUN` maszyny instrukcji. Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektura programisty ręczne wolumin 2: programowania w języku systemu," dokumentu numer 24593, poprawki 3.11 lub nowszym, w [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)