---
title: __sidt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __sidt
dev_langs: C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c952c23af6e1695ca9032e0687334c4ebb881a1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sidt"></a>__sidt
**Dotyczące firmy Microsoft**  
  
 Przechowuje wartość rejestru tabeli deskryptora przerwań (IDTR) w lokalizacji określonej pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`Destination`|Wskaźnik do przechowywania IDTR lokalizacji w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__sidt`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__sidt` Funkcji jest odpowiednikiem `SIDT` maszyny instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: Odwołanie zestaw instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) lokacji.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)