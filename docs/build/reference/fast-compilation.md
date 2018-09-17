---
title: Szybka kompilacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926c63d3d556d1aa9b85a7ce97e93b60e7c2ea23
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722271"
---
# <a name="fast-compilation"></a>Szybka kompilacja

Aby zwiększyć szybkość sieci kompiluje:

- Użyj [minimalną ponowną kompilację](../../build/reference/gm-enable-minimal-rebuild.md), w którym kompilator języka C++ następuje rekompilacja pliku źródłowego tylko wtedy, gdy jest on zależny od zmiany do klasy w pliku nagłówkowym.

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md) i użyj [prekompilowanego nagłówka opcje](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)