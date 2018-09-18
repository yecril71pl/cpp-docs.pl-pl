---
title: Błąd krytyczny C1383 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98f6fe881b2cdc46d4d2848d6faf850381f54c7b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062192"
---
# <a name="fatal-error-c1383"></a>Błąd krytyczny C1383

— Opcja kompilatora /GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego języka wspólnego

C1383 występuje podczas korzystania z poprzedniej wersji środowiska uruchomieniowego języka wspólnego za pomocą kompilatora nowsza, a podczas kompilowania z **/CLR** i   **/GL.**

Aby rozwiązać problem, nie należy używać **/GL** z **/CLR** lub zainstaluj wersję środowiska uruchomieniowego języka wspólnego dostarczanej z kompilatora.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).