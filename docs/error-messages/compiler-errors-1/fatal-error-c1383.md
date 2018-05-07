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
ms.openlocfilehash: ae5e16959597e16f25320778be4d4b45ca5950e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1383"></a>Błąd krytyczny C1383
— Opcja kompilatora /GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego  
  
 C1383 występuje w poprzedniej wersji środowiska CLR za pomocą nowszej kompilatora oraz w przypadku kompilacji z **/CLR** i   **/GL.**  
  
 Aby rozwiązać, nie należy używać **/GL** z **/CLR** lub zainstaluj wersję środowiska CLR, które zostały wydane z kompilujący.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).