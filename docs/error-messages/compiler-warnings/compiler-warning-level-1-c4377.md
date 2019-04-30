---
title: Kompilator ostrzeżenie (poziom 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410428"
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