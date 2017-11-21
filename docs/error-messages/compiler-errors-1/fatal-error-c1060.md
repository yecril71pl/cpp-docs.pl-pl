---
title: "Błąd krytyczny C1060 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1060
dev_langs: C++
helpviewer_keywords: C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36abe3a63515dcb3b8f07ce5d0d169329ed5f7ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1060"></a>Błąd krytyczny C1060
za mało miejsca na stercie dla kompilatora  
  
 System operacyjny lub biblioteki wykonawczej nie można wypełnić żądanie pamięci.  
  
### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Aby naprawić ten błąd, spróbuj następujących rozwiązań  
  
1.  Jeśli kompilator generuje także błędy [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) i [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), użyj [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcję kompilatora, aby zmniejszyć limit alokacji pamięci. Więcej miejsca na stercie jest dostępne dla aplikacji po obniżeniu pozostałych alokacji pamięci.  
  
     Jeśli [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcji jest już ustawiony, spróbuj go usunąć. Miejsce na stercie może wyczerpane, ponieważ limit alokacji pamięci określonego w opcji jest zbyt duża. Kompilator używa domyślny limit, po usunięciu [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcji.  
  
2.  Jeśli kompilacja na platformie 64-bitowych, należy użyć zestawu narzędzi kompilatora 64-bitowych. Aby uzyskać informacje, zobacz [porady: Włączanie 64-bitowych Visual C++ narzędzi w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  W 32-bitowego systemu Windows, spróbuj użyć [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) boot.ini przełącznika.  
  
4.  Zwiększ rozmiar pliku wymiany systemu Windows.  
  
5.  Zamknij inne uruchomione programy.  
  
6.  Wyeliminuj niepotrzebne pliki dołączane.  
  
7.  Na przykład wyeliminować niepotrzebne zmienne globalne, przydzielając pamięć dynamicznie zamiast deklarowanie dużą tablicę.  
  
8.  Usuń nieużywane deklaracje.  
  
9. Podziel bieżący plik na mniejsze pliki.