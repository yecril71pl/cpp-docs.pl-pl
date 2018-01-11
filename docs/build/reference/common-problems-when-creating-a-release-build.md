---
title: Typowe problemy podczas tworzenia kompilacji wydania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44b5528a2d6bedaaaa7ddce582f58042e084b3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="common-problems-when-creating-a-release-build"></a>Typowe problemy podczas tworzenia kompilacji wydania
Podczas tworzenia będzie zazwyczaj kompilacji i testowania z kompilacji debugowania projektu. Jeśli późniejszego kompilowania aplikacji dla kompilacji wydania, mogą wystąpić naruszenie zasad dostępu.  
  
 Poniższa lista zawiera podstawowe różnice między debugowania i kompilacji wydania (nondebug). Istnieją inne różnice, ale poniżej przedstawiono podstawowe różnice, które mogłyby spowodować awarię aplikacji w kompilacji wydania, jeśli działa w trybie debugowania.  
  
-   [Układ sterty](#_core_heap_layout)  
  
-   [Kompilacja](#_core_compilation)  
  
-   [Obsługa wskaźnika](#_core_pointer_support)  
  
-   [Optymalizacje](#_core_optimizations)  
  
 Zobacz [GZ (Catch błędy kompilacji wydania w kompilacji debugowania)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) błędy w kompilacjach debugowania kompilacji opcję kompilatora, aby uzyskać informacje o wersji catch.  
  
##  <a name="_core_heap_layout"></a>Układ sterty  
 Układ sterty będzie przyczynę około dziewięćdziesięciu procent widocznych problemów, gdy aplikacja działa w debugowania, ale nie wersji.  
  
 Podczas kompilowania projektu do debugowania używasz alokatora debugowania. To oznacza, że wszystkie alokacji pamięci mają bajtów guard umieszczona wokół nich. Te bajtów guard wykryć Zastąp pamięci. Układ sterty różni się od wersji i debugowania wersje, Zastąp pamięci nie może utworzyć wszelkie problemy w kompilacji debugowania, ale mogą mieć wpływ krytyczny w kompilacji wydania.  
  
 Aby uzyskać więcej informacji, zobacz [Sprawdź, czy zastąpić pamięci](../../build/reference/checking-for-memory-overwrites.md) i [na użytek debugowania kompilacji do sprawdzenia zastąpić pamięci](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).  
  
##  <a name="_core_compilation"></a>Kompilacja  
 Wiele makr MFC i wielu zmian implementacji MFC podczas kompilacji w wersji. W szczególności ASSERT — makro daje w wyniku postanowienia kompilacji wydania, więc brak znaleziono w potwierdzenia kodu zostaną wykonane. Aby uzyskać więcej informacji, zobacz [zbadać instrukcje ASSERT](../../build/reference/using-verify-instead-of-assert.md).  
  
 Niektóre funkcje są wbudowane, zwiększenia szybkości w kompilacji wydania. Ogólnie rzecz biorąc optymalizacji są włączone w kompilacji wydania. Różne alokatora jest również używana.  
  
##  <a name="_core_pointer_support"></a>Obsługa wskaźnika  
 Brak informacji o debugowaniu usuwa Dopełnienie z aplikacji. W kompilacji wydania wskaźniki stray mają większe prawdopodobieństwo wskazujący niezainicjowanej pamięci zamiast wskazujące na informacje o debugowaniu.  
  
##  <a name="_core_optimizations"></a>Optymalizacje  
 W zależności od charakteru niektórych segmenty kodu optymalizacji kompilatora może wygenerować nieoczekiwany kod. Jest to najmniej prawdopodobną przyczyną problemów kompilacji wydania, ale czasami wystąpić. Rozwiązania, zobacz [optymalizacji kodu](../../build/reference/optimizing-your-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacje wydania](../../build/reference/release-builds.md)   
 [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)