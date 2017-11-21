---
title: __outword | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __outword
dev_langs: C++
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e686160a0ac49bac10e576570970d4afcb2eba3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="outword"></a>__outword
**Dotyczące firmy Microsoft**  
  
 Generuje `out` instrukcji, która wysyła wyraz `Data` z portu We/Wy, określony przez `Port`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __outword(   
   unsigned short Port,   
   unsigned short Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Port`  
 Port do wysyłania danych do.  
  
 [in]`Data`  
 Dane do wysłania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__outword`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)