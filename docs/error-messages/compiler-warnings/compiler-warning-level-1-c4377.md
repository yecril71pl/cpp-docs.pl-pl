---
title: Ostrzeżenie kompilatora (poziom 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: b75b6bee88d0b72e77b32e58ae2f4634a9c30fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187001"
---
# <a name="compiler-warning-level-1-c4377"></a>Ostrzeżenie kompilatora (poziom 1) C4377

typy natywne są domyślnie prywatne; -d1PrivateNativeTypes jest przestarzały

W poprzednich wersjach typy natywne w zestawach były domyślnie publiczne, a wewnętrzna, niezaudokumentowana opcja kompilatora ( **/d1PrivateNativeTypes**) została użyta do udostępnienia ich jako Private.

Wszystkie typy, natywne i CLR, są teraz domyślnie prywatne w zestawie, więc **/d1PrivateNativeTypes** nie jest już potrzebne.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4377.

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```
