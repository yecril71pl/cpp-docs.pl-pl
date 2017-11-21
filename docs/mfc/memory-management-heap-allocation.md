---
title: "Zarządzanie pamięcią: Stercie alokacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8be6dabf4eaae1c76ebe31c35ad5b7b30743953
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-heap-allocation"></a>Zarządzanie pamięcią: alokacja sterty
Stos jest zarezerwowana na potrzeby alokacji pamięci programu. Istnieje obszar oprócz kodu programu i stosu. C — programy typowych funkcji `malloc` i **wolnego** można przydzielić i cofnięcia przydzielenia pamięci sterty. Wersja debugowania MFC zapewnia zmodyfikowanej wersji wbudowanych operatorów C++ **nowe** i **usunąć** można przydzielić i cofnięcie przydziału obiektów w pamięci sterty.  
  
 Jeśli używasz **nowe** i **usunąć** zamiast `malloc` i **wolnego**, jest możliwość debugowania zawiera ulepszenia zarządzania pamięcią biblioteki klas , które mogą być przydatne w wykrywanie przecieków pamięci. Podczas budowania programu z wersji MFC, wersje standard **nowe** i **usunąć** operatory umożliwiają wydajne przydzielić i cofnięcia przydzielenia pamięci (wydanej wersji programu MFC nie zawiera zmodyfikowanej wersji tych operatorów).  
  
 Należy pamiętać, że łączny rozmiar obiektów przydzielony na stosie jest ograniczona tylko przez ilość dostępnej pamięci wirtualnej w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią](../mfc/memory-management.md)

