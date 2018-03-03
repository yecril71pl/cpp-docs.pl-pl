---
title: "Pola bitów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 231d84e5d99cd9e6c1238ae12c143636f62ce80d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bitfields"></a>Pola bitów
Pola bitowe struktury są ograniczone do 64-bitowy i może być typu podpisany int, int bez znaku, int64 lub int64 bez znaku. Pola bitowe, które przekraczają granicę typu pominie usługi bits, aby były wyrównane bitfield do następnego wyrównania typu. Pola bitów liczba całkowita może na przykład przecina graniczny 32-bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i magazyn](../build/types-and-storage.md)