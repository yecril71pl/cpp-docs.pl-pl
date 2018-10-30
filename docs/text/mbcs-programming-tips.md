---
title: Porady dotyczące programowania MBCS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a88fffbfc42dd6e7386ec43e55f2013f2548b6f5
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204473"
---
# <a name="mbcs-programming-tips"></a>Porady dotyczące programowania MBCS

W nowych wdrożeniach należy używać kodowania znaków Unicode dla wszystkich ciągów, które prawdopodobnie mogą zobaczyć użytkownicy końcowi. MBCS jest technologią starszą, która została zastąpiona przez Unicode. Ta sekcja dostarcza wskazówek dla programistów, którzy muszą utrzymywać istniejące programy, które używają MBCS i gdy nie jest praktyczne, aby przekonwertować do formatu Unicode. Porady dotyczą aplikacjach MFC i aplikacji napisanych bez MFC. Tematy obejmują:

- [Ogólne porady dotyczące programowania MBSC](../text/general-mbcs-programming-advice.md)

- [Inkrementacja i dekrementacja wskaźników](../text/incrementing-and-decrementing-pointers.md)

- [Indeksy bajtowe](../text/byte-indices.md)

- [Ostatni znak w ciągu](../text/last-character-in-a-string.md)

- [Przypisanie znaku](../text/character-assignment.md)

- [Porównywanie znaków](../text/character-comparison.md)

- [Przepełnienie buforu](../text/buffer-overflow.md)

## <a name="see-also"></a>Zobacz też

[Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)