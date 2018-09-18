---
title: Kompilator ostrzeżenie (poziom 3) C4192 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671a8c83dcadcaa89372e53b6c3d677c5810b4a5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114413"
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilator ostrzeżenie (poziom 3) C4192

automatycznie pomija "name" podczas importowania biblioteki typów "library"

A `#import` biblioteka zawiera element, *nazwa*, która jest również zdefiniowane w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, takich jak nazwy **IUnknown** lub identyfikator GUID często są zdefiniowane w bibliotece typów duplikowania definicji z nagłówków systemu. `#import` wykryje te elementy i odmawiają dołączać je w plikach nagłówkowych .tlh i .tli.

Aby zmienić to zachowanie, użyj `#import` atrybuty [no_auto_exclude —](../../preprocessor/no-auto-exclude.md) i [include()](../../preprocessor/include-parens.md).