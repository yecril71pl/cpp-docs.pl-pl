---
title: "Błąd krytyczny C1128 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1128
dev_langs: C++
helpviewer_keywords: C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22b53914fba8ab5d5c31d8f7ed0a2e3db52aad5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1128"></a>Błąd krytyczny C1128
Liczba sekcji przekroczyła limit formatu pliku obiektowego: skompiluj z parametrem/bigobj  
  
 Plik .obj przekroczona liczba dopuszczalny sekcje, ograniczenia formatu pliku obiektu COFF.  
  
 Osiągnięcie tego ograniczenia sekcji mogą być wynikiem przy użyciu [/Gy](../../build/reference/gy-enable-function-level-linking.md) i kompilacji debugowania; **/Gy** niektóre funkcje przejść na ich własnych sekcje COMDAT. Kompilacja debugowania ma sekcji informacji o debugowaniu, dla każdej funkcji COMDAT.  
  
 C1128 może również być spowodowane istnieje zbyt wiele funkcji śródwierszowych.  
  
 Aby rozwiązać ten problem, podzielić na wiele plików kodu źródłowego pliku źródłowego, kompilować bez **/Gy**, lub skompiluj z  [ /bigobj (Zwiększ ilość sekcji w. Plik obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Jeśli nie można skompilować z **/Gy**, musisz określić optymalizacje oddzielnie, ponieważ **/O2** i **/O1** zarówno oznacza **/Gy**.  
  
 Jeśli to możliwe skompiluj bez informacji debugowania.  
  
 Może być również konieczne ma określonych wystąpień szablonów w plików kodu źródłowego w oddzielnych, a nie o kompilator Emituj je.  
  
 Podczas przenoszenia kodu, C1128 prawdopodobnie pojawi się najpierw przy użyciu x64 kompilatora i znacznie później z x86 kompilatora. x64 będzie zawierać co najmniej 4 sekcji skojarzone z każdej funkcji skompilowany **/Gy** lub wbudowanego z szablonów lub klasy wbudowany: code pdata i debugowanie informacji i prawdopodobnie xdata.  X86 nie będziesz mieć pdata.