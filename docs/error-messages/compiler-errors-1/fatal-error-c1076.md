---
title: Błąd krytyczny C1076 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1076
dev_langs:
- C++
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c02cc55280202b9ce576dc1e771b3428837209c8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465986"
---
# <a name="fatal-error-c1076"></a>Błąd krytyczny C1076
limit kompilatora : limit sterty wewnętrznej osiągnięty; użyj /Zm, aby określić wyższy limit  
  
 Ten błąd może być spowodowany przez zbyt wiele symboli lub zbyt wiele wystąpień szablonu.  
  
 Aby rozwiązać ten błąd:  
  
1.  Użyj [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcję, aby ustawić limit pamięci kompilatora na wartość określoną w [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) komunikat o błędzie. Aby uzyskać więcej informacji o tym, jak ustawić tę wartość w programie Visual Studio, zobacz sekcję Uwagi w [/Zm (Określ wstępnie skompilowany nagłówek Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Jeśli używasz kompilatorów dla hostów 32-bitowych w 64-bitowym systemie operacyjnym, użyj kompilatorów dla hostów 64-bitowych. Aby uzyskać więcej informacji, zobacz [porady: Włączanie 64-bitowego zestawu narzędzi Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  Wyeliminuj niepotrzebne pliki dołączane.  
  
4.  Wyeliminuj niepotrzebne zmienne globalne — na przykład poprzez przydzielanie pamięci dynamicznie zamiast deklarowania dużej tablicy.  
  
5.  Usuń nieużywane deklaracje.  
  
6.  Podziel duże funkcje na mniejsze.  
  
7.  Podziel duże klasy na mniejsze.  
  
8.  Podziel bieżący plik na mniejsze pliki.  
  
 Jeśli C1076 pojawia się natychmiast po uruchomieniu kompilacji, wartość określona dla **/Zm** prawdopodobnie jest zbyt duża dla Twojego programu. Zmniejsz **/Zm** wartości.