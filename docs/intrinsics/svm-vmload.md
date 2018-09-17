---
title: __svm_vmload | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmload
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce27566075e48fb90b894a21e7a74a3ef1fdbea
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705110"
---
# <a name="svmvmload"></a>__svm_vmload
**Microsoft Specific**  
  
 Ładuje podzbiór procesor, stan z bloku sterowania określonej maszyny wirtualnej (VMCB).  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*VmcbPhysicalAddress*|[in] Adres fizyczny VMCB.|  
  
## <a name="remarks"></a>Uwagi  
 `__svm_vmload` Funkcji jest odpowiednikiem `VMLOAD` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_vmload`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)