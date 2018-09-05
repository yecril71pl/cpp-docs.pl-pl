---
title: __svm_vmrun | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 086fbbc2a25c4af2b09f40d83ac0b20399860ca1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679809"
---
# <a name="svmvmrun"></a>__svm_vmrun
**Microsoft Specific**  
  
 Rozpoczyna wykonywanie kodu gościa maszyny wirtualnej, który odnosi się do bloku sterowania określonej maszyny wirtualnej (VMCB).  
  
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
 `__svm_vmrun` Funkcja używa minimalnej ilości informacji w VMCB umożliwiającą wykonywanie kodu gościa maszyny wirtualnej. Użyj [__svm_vmsave](../intrinsics/svm-vmsave.md) lub [__svm_vmload](../intrinsics/svm-vmload.md) działać, jeśli potrzebujesz więcej informacji, do obsługi złożonych przerwania lub przełączyć się do innego gościa.  
  
 `__svm_vmrun` Funkcji jest odpowiednikiem `VMRUN` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" dokument o numerze 24593, wersji 3.11 lub później, w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)