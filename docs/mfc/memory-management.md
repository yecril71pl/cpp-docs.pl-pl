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
ms.openlocfilehash: 5d81bd0a8bdd24059951cba5c8b69751b3d1db86
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508270"
---
# <a name="memory-management"></a>Zarządzanie pamięcią

W tej grupie artykułów opisano, jak korzystać z usług ogólnego przeznaczenia biblioteka MFC (MFC) związanych z zarządzaniem pamięcią. Alokacja pamięci można podzielić na dwie główne kategorie: alokacje ramek i alokacje sterty.

Jedną z głównych różnic między tymi dwoma technikami alokacji jest to, że dzięki alokacji ramki zazwyczaj pracujesz z rzeczywistym blokiem pamięci, podczas gdy z alokacją sterty zawsze uzyskuje się wskaźnik do bloku pamięci. Kolejną istotną różnicą między dwoma schematami jest to, że obiekty ramek są automatycznie usuwane, natomiast obiekty sterty muszą być jawnie usuwane przez programistę.

Informacje inne niż MFC dotyczące zarządzania pamięcią w programach dla systemu Windows znajdują się w temacie [Zarządzanie pamięcią](/windows/win32/memory/memory-management) w Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Alokacja ramek](../mfc/memory-management-frame-allocation.md)

- [Alokacja sterty](../mfc/memory-management-heap-allocation.md)

- [Przydzielanie pamięci dla tablicy](../mfc/memory-management-examples.md)

- [Cofanie przydziału pamięci dla tablicy ze sterty](../mfc/memory-management-examples.md)

- [Przydzielanie pamięci dla struktury danych](../mfc/memory-management-examples.md)

- [Przydzielanie pamięci dla obiektu](../mfc/memory-management-examples.md)

- [Bloki pamięci o zmiennym rozmiarze](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
