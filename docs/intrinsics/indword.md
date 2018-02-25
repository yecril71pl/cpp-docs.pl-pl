---
title: __indword | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __indword_cpp
- __indword
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 529d83982b1797678b421fbacb4ad6c69cad030d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="indword"></a>__indword
**Microsoft Specific**  
  
 Odczytuje dane o jedno słowo o podwójnej precyzji z przy użyciu określonego portu `in` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned long __indword(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wyraz odczytu z portu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__indword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)