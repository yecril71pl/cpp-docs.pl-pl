---
title: "Zarządzanie pamięcią: Bloki pamięci o zmiennych rozmiarach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1342f1f78b9880e5b24d21707282da39c8d4672e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach
**Nowe** i **usunąć** operatorów, opisaną w artykule [zarządzanie pamięcią: przykłady](../mfc/memory-management-examples.md), są odpowiednie w alokowanie i dealokowanie bloki pamięci o stałym rozmiarze i obiekty. Czasami może być konieczne aplikacji bloki pamięci o zmiennych rozmiarach. Należy użyć standardowe funkcje biblioteki wykonawczej języka C [— funkcja malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), i [wolnego](../c-runtime-library/reference/free.md) do zarządzania bloki pamięci o zmiennych rozmiarach na stosie.  
  
> [!IMPORTANT]
>  Mieszanie **nowe** i **usunąć** uszkodzony pamięci w wersji do debugowania MFC spowoduje operatory funkcji alokacji pamięci o zmiennych rozmiarach, w tym samym bloku pamięci. Nie należy używać `realloc` na blok pamięci przydzielony z **nowe**. Podobnie, nie należy przydzielić bloku pamięci z **nowe** operatora i usuń go z **wolnego**, lub użyj **usunąć** operator na blok pamięci przydzielony z `malloc`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią: Alokacja sterty](../mfc/memory-management-heap-allocation.md)

