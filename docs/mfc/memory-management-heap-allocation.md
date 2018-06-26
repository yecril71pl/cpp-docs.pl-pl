---
title: 'Zarządzanie pamięcią: Stercie alokacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7ef166201103b1544d0a36d82452b485af75418
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928612"
---
# <a name="memory-management-heap-allocation"></a>Zarządzanie pamięcią: alokacja sterty
Stos jest zarezerwowana na potrzeby alokacji pamięci programu. Istnieje obszar oprócz kodu programu i stosu. Typowych programów C korzystanie z funkcji **— funkcja malloc** i **wolnego** można przydzielić i cofnięcia przydzielenia pamięci sterty. Wersja debugowania MFC zapewnia zmodyfikowanej wersji wbudowanych operatorów C++ **nowe** i **usunąć** można przydzielić i cofnięcie przydziału obiektów w pamięci sterty.  
  
 Jeśli używasz **nowe** i **usunąć** zamiast **— funkcja malloc** i **wolnego**, można skorzystać z biblioteki klas Zarządzanie pamięcią debugowania ulepszeń, które mogą być przydatne w wykrywanie przecieków pamięci. Podczas budowania programu z wersji MFC, wersje standard **nowe** i **usunąć** operatory umożliwiają wydajne przydzielić i cofnięcia przydzielenia pamięci (wydanej wersji programu MFC nie zawiera zmodyfikowanej wersji tych operatorów).  
  
 Należy pamiętać, że łączny rozmiar obiektów przydzielony na stosie jest ograniczona tylko przez ilość dostępnej pamięci wirtualnej w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią](../mfc/memory-management.md)

