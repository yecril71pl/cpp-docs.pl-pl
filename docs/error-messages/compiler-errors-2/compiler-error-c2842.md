---
title: Błąd kompilatora C2842 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20967ab4cd047f62a5cf692c91fec90148b4f470
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118820"
---
# <a name="compiler-error-c2842"></a>Błąd kompilatora C2842

"class": zarządzanej lub typu WinRT nie musi definiować własnego "operator new" ani "operator delete"

Definiowanie swoich własnych ** nowy operator lub **operatora delete** Zarządzanie alokacji pamięci na natywnej stercie. Odwołanie do klasy nie można jednak zdefiniować te operatory, ponieważ są przydzielane tylko na stosie zarządzanym.


Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2842.

```
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
