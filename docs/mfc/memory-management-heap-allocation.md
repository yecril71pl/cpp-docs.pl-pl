---
title: 'Zarządzanie pamięcią: Alokacja sterty'
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
ms.openlocfilehash: 93eee5cbfe1cd49042a9080f06657e751640de69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219480"
---
# <a name="memory-management-heap-allocation"></a>Zarządzanie pamięcią: Alokacja sterty

Stos jest zastrzeżona na potrzeby alokacji pamięci programu. To obszar, oprócz kodu programu i stosu. Typowe programów C, użyj funkcji **— funkcja malloc** i **bezpłatne** można przydzielić i cofanie przydziału pamięci sterty. Wersja do debugowania MFC udostępnia zmodyfikowanej wersji wbudowanych operatorów C++ **nowe** i **Usuń** można przydzielić i cofanie przydziału obiektów w pamięci sterty.

Zastosowania **nowe** i **Usuń** zamiast **— funkcja malloc** i **bezpłatne**, będą mogli korzystać z zalet biblioteki klas Zarządzanie pamięcią debugowania rozszerzenia, które mogą być przydatne podczas wykrywania przecieków pamięci. Podczas budowania programu z wersji biblioteki MFC, wersje standard **nowe** i **Usuń** operatory zapewnia skuteczny sposób przydzielania i cofnąć jej przydział pamięci (wydanej wersji programu MFC nie zawiera zmodyfikowanej wersji te operatory).

Należy pamiętać, że łączny rozmiar obiektów zaalokowanych na stosie jest ograniczona jedynie ilością dostępnej pamięci wirtualnej w systemie.

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią](../mfc/memory-management.md)
