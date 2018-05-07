---
title: 'Zarządzanie pamięcią: Bloki pamięci o zmiennych rozmiarach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bbd97899261f85454824fcab261d330b04e25fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach
**Nowe** i **usunąć** operatorów, opisaną w artykule [zarządzanie pamięcią: przykłady](../mfc/memory-management-examples.md), są odpowiednie w alokowanie i dealokowanie bloki pamięci o stałym rozmiarze i obiekty. Czasami może być konieczne aplikacji bloki pamięci o zmiennych rozmiarach. Należy użyć standardowe funkcje biblioteki wykonawczej języka C [— funkcja malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), i [wolnego](../c-runtime-library/reference/free.md) do zarządzania bloki pamięci o zmiennych rozmiarach na stosie.  
  
> [!IMPORTANT]
>  Mieszanie **nowe** i **usunąć** uszkodzony pamięci w wersji do debugowania MFC spowoduje operatory funkcji alokacji pamięci o zmiennych rozmiarach, w tym samym bloku pamięci. Nie należy używać `realloc` na blok pamięci przydzielony z **nowe**. Podobnie, nie należy przydzielić bloku pamięci z **nowe** operatora i usuń go z **wolnego**, lub użyj **usunąć** operator na blok pamięci przydzielony z `malloc`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)

