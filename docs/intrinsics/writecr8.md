---
title: __writecr8 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _writecr8
dev_langs: C++
helpviewer_keywords: _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9285d2c9c47b260f9cfc9dd9b62e5d278422adee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="writecr8"></a>__writecr8
**Dotyczące firmy Microsoft**  
  
 Zapisuje wartość `Data` do rejestru CR8.  
  
## <a name="syntax"></a>Składnia  
  
```  
void writecr8(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Data`  
 Wartość do zapisu do rejestru CR8.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writecr8`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)