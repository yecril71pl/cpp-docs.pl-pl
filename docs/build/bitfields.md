---
title: Pola bitów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85db49f138cc733326e47a3008e79bae5ab4b7cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bitfields"></a>Pola bitów
Pola bitowe struktury są ograniczone do 64-bitowy i może być typu podpisany int, int bez znaku, int64 lub int64 bez znaku. Pola bitowe, które przekraczają granicę typu pominie usługi bits, aby były wyrównane bitfield do następnego wyrównania typu. Pola bitów liczba całkowita może na przykład przecina graniczny 32-bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i magazyn](../build/types-and-storage.md)