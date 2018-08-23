---
title: __vmx_vmptrld | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f12ff4f0f109ac97f9e9e2e4f8d800455159a10b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466233"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Microsoft Specific**  
  
 Ładuje wskaźnik do bieżącej struktury sterowania maszyny wirtualnej (VMCS) z określonego adresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w] *`VmcsPhysicalAddress`  
 Adres, gdzie jest przechowywany wskaźnik VMCS.  
  
## <a name="return-value"></a>Wartość zwracana  
 0  
 Operacja zakończyła się pomyślnie.  
  
 1  
 Operacja nie powiodła się z rozszerzonych informacji o stanie w `VM-instruction error field` z bieżącym VMCS.  
  
 2  
 Operacja nie powiodła się bez informacji o stanie.  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik VMCS jest 64-bitowy adres fizyczny.  
  
 `__vmx_vmptrld` Funkcji jest odpowiednikiem `VMPTRLD` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Intel Virtualization Technical Preview specyfikacji dla IA-32 architekturze firmy Intel," dokumentu numer C97063-002 w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrld`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)