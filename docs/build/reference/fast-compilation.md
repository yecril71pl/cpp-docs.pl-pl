---
title: Szybka kompilacja
ms.date: 11/04/2016
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
ms.openlocfilehash: ab3171d7bb6d85cbe010e0efce39eda14b166527
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667661"
---
# <a name="fast-compilation"></a>Szybka kompilacja

Aby zwiększyć szybkość sieci kompiluje:

- Użyj [minimalną ponowną kompilację](../../build/reference/gm-enable-minimal-rebuild.md), w którym kompilator języka C++ następuje rekompilacja pliku źródłowego tylko wtedy, gdy jest on zależny od zmiany do klasy w pliku nagłówkowym.

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md) i użyj [prekompilowanego nagłówka opcje](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)