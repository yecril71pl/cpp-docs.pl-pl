---
title: Zarządzanie pamięcią
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 1c7f901009d5e1e7f0af20d493bb748b46b18480
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281294"
---
# <a name="memory-management"></a>Zarządzanie pamięcią

Ta grupa artykułów opisano, jak korzystać z usług ogólnego przeznaczenia z Microsoft Foundation Class Library (MFC) związane z zarządzaniem pamięcią. Alokacja pamięci można podzielić na dwie główne kategorie: klatki, alokacji i Alokacje sterty.

Jedną z głównych różnic między techniki alokacji dwóch jest, że za pomocą Alokacja ramek, zwykle działają z rzeczywistych pamięci zablokowanie, gdy za pomocą alokacji stosu, są zawsze podając wskaźnik do bloku pamięci. Inna główna różnica między dwa schematy jest, że obiekty ramki są automatycznie usuwane, gdy sterty obiektów, które muszą zostać jawnie usunięte przez programistę.

Dla innego typu niż MFC informacji na temat zarządzania pamięcią w programach dla Windows, zobacz [zarządzanie pamięcią](/windows/desktop/memory/memory-management) w zestawie Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Alokacja ramek](../mfc/memory-management-frame-allocation.md)

- [Alokacja sterty](../mfc/memory-management-heap-allocation.md)

- [Przydzielanie pamięci dla tablic](../mfc/memory-management-examples.md)

- [Cofanie przydziału pamięci dla tablicy ze sterty](../mfc/memory-management-examples.md)

- [Przydzielanie pamięci dla struktury danych](../mfc/memory-management-examples.md)

- [Przydzielanie pamięci dla obiektu](../mfc/memory-management-examples.md)

- [Bloki pamięci o zmiennych rozmiarach](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
