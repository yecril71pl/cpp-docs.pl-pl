---
title: __indwordstring | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __indwordstring
- __indwordstring_cpp
dev_langs: C++
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a5150ceba7d85732c2b7db4d83cd2b1aa6cc0f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="indwordstring"></a>__indwordstring
**Dotyczące firmy Microsoft**  
  
 Odczytuje dane z określonego portu przy użyciu `rep insd` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __indwordstring(  
   unsigned short Port,  
   unsigned long* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Port`  
 Port do odczytu.  
  
 [out]`Buffer`  
 Dane odczytywane z portu są zapisywane w tym miejscu.  
  
 [in]`Count`  
 Liczba bajtów danych do odczytu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__indwordstring`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)