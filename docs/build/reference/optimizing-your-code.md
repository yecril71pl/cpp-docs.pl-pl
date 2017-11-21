---
title: Optymalizacja kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.assetid: 4f33e6c7-9870-43b3-9c2f-d7e44f764971
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3da29e9a0269c4748f10d9e8ba926103305239e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="optimizing-your-code"></a>Optymalizacja kodu
Dzięki optymalizacji pliku wykonywalnego, można osiągnąć kompromis między szybkość wykonywania szybkiego i rozmiar mały kod. W tym temacie omówiono niektóre mechanizmy, które Visual C++ w celu zapewnienia optymalizacji kodu.  
  
## <a name="language-features"></a>Funkcje językowe  
 W poniższych tematach opisano niektóre funkcje optymalizacji w języku C/C++.  
  
 [Optymalizacja Pragm i słów kluczowych](../../build/reference/optimization-pragmas-and-keywords.md)  
 Lista słowa kluczowe i pragmy, że można użyć w kodzie do zwiększenia wydajności.  
  
 [Opcje kompilatora w rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md)  
 Lista **/O** opcje kompilatora, które dotyczą wykonywania rozmiar szybkości łącza lub kodu.  
  
 [Deklarator odwołania do wartości r: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)  
 Odwołania wartościowane prawostronnie obsługuje wykonania *Przenieś semantyki*. Jeśli przeniesienie semantyki są używane do implementowania biblioteki szablonów i wydajności aplikacji korzystających z tych szablonów może znacznie poprawić.  
  
### <a name="the-optimize-pragma"></a>Optymalizacja Pragma  
 Jeśli sekcji zoptymalizowanego kodu powoduje występowanie błędów i spowolnienie, możesz użyć [zoptymalizować](../../preprocessor/optimize.md) pragma, aby wyłączyć funkcję optymalizacji dla tej sekcji.  
  
 Umieść kod między dwoma pragm w następujący sposób.  
  
```  
#pragma optimize("", off)  
// some code here   
#pragma optimize("", on)  
```  
  
## <a name="programming-practices"></a>Rozwiązania w zakresie programowania  
 Podczas kompilowania kodu przy użyciu optymalizacji można zauważyć dodatkowych komunikatów ostrzegawczych. Jest to zachowanie oczekiwane, ponieważ ostrzeżenia odnosić się tylko do zoptymalizowanego kodu. Wiele problemów optymalizacji można uniknąć, jeżeli uwzględnianie tych ostrzeżeń.  
  
 Paradoxically optymalizacji programu szybkości może spowodować kodu działać wolniej. Jest to spowodowane niektórych optymalizacji dla szybkości zwiększyć rozmiar kodu. Na przykład ze śródwierszowaniem funkcji eliminuje obciążenie wywołania funkcji. Jednak ze śródwierszowaniem zbyt dużej ilości kodu może Twoje program był tak duży, że numer strony pamięci wirtualnej błędów zwiększa. W związku z tym szybkości zdobytych wyeliminowanie wywołania funkcji mogą zostać utracone do wymiany pamięci.  
  
 W poniższych tematach opisano dobrych praktyk programowania.  
  
 [Wskazówki dotyczące poprawiania kodu wrażliwego na czas](../../build/reference/tips-for-improving-time-critical-code.md)  
 Techniki tworzenia kodu lepiej może zapewnić lepszą wydajność. W tym temacie sugeruje kodowania techniki, które mogą pomóc Ci upewnij się, że pomyślnie wykonać części kodu wrażliwego na czas.  
  
 [Najlepsze praktyki optymalizacji](../../build/reference/optimization-best-practices.md)  
 Zawiera ogólne wskazówki dotyczące jak najlepiej zoptymalizować aplikacji.  
  
## <a name="debugging-optimized-code"></a>Debugowanie zoptymalizowanego kodu  
 Optymalizacja może zmienić kod, który został utworzony przez kompilator, dlatego zaleca debugowania aplikacji i mierzenie jego wydajności i następnie optymalizacji kodu.  
  
 Podstawowe informacje o tym, jak można debugować można znaleźć w następujących tematach.  
  
-   [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
-   [Typowe problemy podczas tworzenia kompilacji wydania](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
 Poniższe tematy zawierają bardziej zaawansowane informacje dotyczące debugowania.  
  
-   [Porady: debugowanie zoptymalizowanego kodu](/visualstudio/debugger/how-to-debug-optimized-code)  
  
-   [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](../../build/reference/why-floating-point-numbers-may-lose-precision.md)  
  
 Wybór następujące tematy zawierają informacje dotyczące sposobu optymalizacji tworzenia ładowania oraz wykonywania kodu.  
  
-   [Poprawianie wydajności kompilatora](../../build/reference/improving-compiler-throughput.md)  
  
-   [Korzystanie z nazwy funkcji bez () nie tworzy kodu](../../build/reference/using-function-name-without-parens-produces-no-code.md)  
  
-   [Optymalizowanie zestawu wbudowanego](../../assembler/inline/optimizing-inline-assembly.md)  
  
-   [Określanie Optymalizacja kompilatora Projekt ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)  
  
-   [Jakich technik optymalizacji należy użyć, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](../../build/dll-frequently-asked-questions.md#mfc_optimization)  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]jak w celu skrócenia czasu ładowania biblioteki DLL metody, zobacz "Optymalizowanie DLL obciążenia wydajności w czasie" w kolumnie "Pod maską" w "MSDN Magazine" na [biblioteki MSDN Library](http://go.microsoft.com/fwlink/?linkid=556) witryny sieci Web.  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]minimalizowanie stronicowania w aplikacjach, zobacz "Poprawę środowiska uruchomieniowego wydajności z Smooth pracy Ustaw narzędzie" i "Zwiększanie wydajności środowiska wykonawczego o sprawnego funkcjonowania zestaw narzędzi — część 2" w kolumnie "Bugslayer" w "MSDN Magazine" na [MSDN Biblioteka](http://go.microsoft.com/fwlink/?linkid=556) witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)