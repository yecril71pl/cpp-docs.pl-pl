---
title: Ostrzeżenie kompilatora (poziom 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174235"
---
# <a name="compiler-warning-level-3-c4278"></a>Ostrzeżenie kompilatora (poziom 3) C4278

> "*Identyfikator*": identyfikator w bibliotece typów "*TLB*" jest już makrem; Użyj kwalifikatora "Rename"

W przypadku korzystania z [#import](../../preprocessor/hash-import-directive-cpp.md)identyfikator w importowanym elemencie TypeLib próbuje zadeklarować *Identyfikator*identyfikatora. Jednak ten symbol jest już prawidłowy.

Użyj atrybutu `#import` **Zmień nazwę** , aby przypisać alias do symbolu w bibliotece typów.
