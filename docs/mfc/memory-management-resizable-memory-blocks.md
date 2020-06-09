---
title: 'Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626277"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach

Operatory **New** i **delete** , opisane w artykule [Zarządzanie pamięcią artykułu: przykłady](memory-management-examples.md), są przydatne do przydzielania i cofania przydziału bloków pamięci o ustalonym rozmiarze i obiektów. Czasami aplikacja może potrzebować bloków pamięci o zmiennym rozmiarze. Aby zarządzać blokami pamięci o zmiennym rozmiarze na stercie, należy użyć standardowej biblioteki wykonawczej C funkcji [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)i [Free](../c-runtime-library/reference/free.md) .

> [!IMPORTANT]
> Mieszanie **nowych** i **usuwających** operatorów przy użyciu funkcji alokacji pamięci o zmiennym rozmiarze w tym samym bloku pamięci spowoduje uszkodzenie pamięci w debugowanej wersji biblioteki MFC. Nie należy używać **realloc** w bloku pamięci przydzielonym przez **Nowy**. Podobnie nie należy przydzielić bloku pamięci z operatorem **New** i usunąć go z opcją **Free**lub użyć operatora **delete** w bloku pamięci przydzielonej za pomocą funkcji **malloc**.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią: alokacja sterty](memory-management-heap-allocation.md)
