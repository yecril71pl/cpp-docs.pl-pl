---
title: Błąd krytyczny C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 4ab96c0516ee5593a969669c03ae22f0c211ae27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626135"
---
# <a name="fatal-error-c1383"></a>Błąd krytyczny C1383

— Opcja kompilatora /GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego języka wspólnego

C1383 występuje podczas korzystania z poprzedniej wersji środowiska uruchomieniowego języka wspólnego za pomocą kompilatora nowsza, a podczas kompilowania z **/CLR** i   **/GL.**

Aby rozwiązać problem, nie należy używać **/GL** z **/CLR** lub zainstaluj wersję środowiska uruchomieniowego języka wspólnego dostarczanej z kompilatora.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).