---
title: Ostrzeżenie D9043 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 747f3cadd050b8f36c13fd28ae123f7a6dbdfb05
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992099"
---
# <a name="command-line-warning-d9043"></a>Ostrzeżenie D9043 dla wiersza polecenia

Nieprawidłowa wartość "warning_level" dla "compiler_option"; Zakładając, że "4999"; Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń

## <a name="example"></a>Przykład

Poniższy przykład generuje C9043.

```cpp
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```
