---
title: Kompilator ostrzeżenie (poziom 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 56b27596296b87edcc6de406e7b6621d5723815d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402232"
---
# <a name="compiler-warning-level-3-c4192"></a>Kompilator ostrzeżenie (poziom 3) C4192

automatycznie pomija "name" podczas importowania biblioteki typów "library"

A `#import` biblioteka zawiera element, *nazwa*, która jest również zdefiniowane w nagłówkach systemu Win32. Ze względu na ograniczenia bibliotek typów, takich jak nazwy **IUnknown** lub identyfikator GUID często są zdefiniowane w bibliotece typów duplikowania definicji z nagłówków systemu. `#import` wykryje te elementy i odmawiają dołączać je w plikach nagłówkowych .tlh i .tli.

Aby zmienić to zachowanie, użyj `#import` atrybuty [no_auto_exclude —](../../preprocessor/no-auto-exclude.md) i [include()](../../preprocessor/include-parens.md).