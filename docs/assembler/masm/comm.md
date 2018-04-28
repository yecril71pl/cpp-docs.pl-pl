---
title: COMM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111dac47089fea13febe787e5b73557b287beea8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="comm"></a>COMM
Tworzy zmienną gminna z atrybutów określonych w `definition`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Uwagi  
 Każdy `definition` ma następujący format:  
  
 [[*langtype*]] [[**NEAR** &#124; **DALEKIEGO**]] *etykiety ***:**`type`[[**:*** Liczba*]]  
  
 *Etykiety* to nazwa zmiennej. `type` Może być dowolnym specyfikatora typu ([BAJTÓW](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)i tak dalej) lub liczba całkowita określająca liczbę bajtów. *Liczba* określa liczbę obiektów danych (co jest ustawieniem domyślnym).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)