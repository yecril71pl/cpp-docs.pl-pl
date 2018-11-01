---
title: 'Zarządzanie pamięcią: alokacja sterty'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: 0c669fa611193b9a04e4854c84dec604e585991c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641158"
---
# <a name="memory-management-heap-allocation"></a>Zarządzanie pamięcią: alokacja sterty

Stos jest zastrzeżona na potrzeby alokacji pamięci programu. To obszar, oprócz kodu programu i stosu. Typowe programów C, użyj funkcji **— funkcja malloc** i **bezpłatne** można przydzielić i cofanie przydziału pamięci sterty. Wersja do debugowania MFC udostępnia zmodyfikowanej wersji wbudowanych operatorów C++ **nowe** i **Usuń** można przydzielić i cofanie przydziału obiektów w pamięci sterty.

Zastosowania **nowe** i **Usuń** zamiast **— funkcja malloc** i **bezpłatne**, będą mogli korzystać z zalet biblioteki klas Zarządzanie pamięcią debugowania rozszerzenia, które mogą być przydatne podczas wykrywania przecieków pamięci. Podczas budowania programu z wersji biblioteki MFC, wersje standard **nowe** i **Usuń** operatory zapewnia skuteczny sposób przydzielania i cofnąć jej przydział pamięci (wydanej wersji programu MFC nie zawiera zmodyfikowanej wersji te operatory).

Należy pamiętać, że łączny rozmiar obiektów zaalokowanych na stosie jest ograniczona jedynie ilością dostępnej pamięci wirtualnej w systemie.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią](../mfc/memory-management.md)

