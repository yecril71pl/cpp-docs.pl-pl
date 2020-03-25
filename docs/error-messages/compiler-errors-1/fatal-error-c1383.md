---
title: Błąd krytyczny C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 6c0be830cb56b760f1397ea2b2f81b42a87e9ba6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203089"
---
# <a name="fatal-error-c1383"></a>Błąd krytyczny C1383

Opcja kompilatora/GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego języka wspólnego

C1383 występuje w przypadku używania poprzedniej wersji środowiska uruchomieniowego języka wspólnego z nowszym kompilatorem i podczas kompilowania z **/CLR** i **/GL.**

Aby rozwiązać ten problem, należy użyć opcji **/GL** with **/CLR** lub zainstalować wersję środowiska uruchomieniowego języka wspólnego, która została dostarczona z kompilatorem.

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/GL (Optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).
