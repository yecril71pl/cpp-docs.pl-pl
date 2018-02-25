---
title: __invlpg | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6977d9a8cb21cf1eeefb404ddbff263643189d9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="invlpg"></a>__invlpg
**Microsoft Specific**  
  
 Generuje x86 `invlpg` instrukcji, co spowoduje unieważnienie translacji równoległej buforu (TLB) dla strony skojarzone z pamięci wskazywanej przez `Address`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]  `Address`  
 64-bitowy adres.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__invlpg`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Wewnętrzna `__invlpg` emituje uprzywilejowanej instrukcji i jest dostępna tylko w trybie jądra z poziomem uprawnień (Panel sterowania) 0.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)