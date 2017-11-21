---
title: __lidt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs: C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 729df3d4dd415891a9e89ea373e0b4f740e13c1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="lidt"></a>__lidt
**Dotyczące firmy Microsoft**  
  
 Ładuje deskryptora tabeli Rejestr przerwań (IDTR) z wartością w lokalizacji określonej pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`Source`|Wskaźnik do wartości, które ma zostać skopiowany na IDTR.|  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__lidt`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__lidt` Funkcji jest odpowiednikiem `LIDT` maszyny instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: Odwołanie zestaw instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) lokacji.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)