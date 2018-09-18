---
title: Kompilator ostrzeżenie (poziom 1) C4377 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613ebe183b61c6b9894ed3b726f90061e2b24ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047177"
---
# <a name="compiler-warning-level-1-c4377"></a>Kompilator ostrzeżenie (poziom 1) C4377

typy natywne są domyślnie; prywatny -d1PrivateNativeTypes jest przestarzały

W poprzednich wersjach natywnych typów w zestawach były publiczne domyślnie i — opcja kompilatora nieudokumentowane, wewnętrzne (**/d1PrivateNativeTypes**) został użyty do oznacz je jako prywatne.

Wszystkie typy natywne i CLR, są teraz domyślnie w zestawie, prywatny tak **/d1PrivateNativeTypes** nie jest już potrzebny.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4377.

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```