---
title: Błąd kompilatora C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325575"
---
# <a name="compiler-error-c2842"></a>Błąd kompilatora C2842

> "*klasy*": zarządzanej lub typu WinRT nie musi definiować własnego "operator new" ani "operator delete"

## <a name="remarks"></a>Uwagi

Definiowanie swoich własnych **nowy operator** lub **operatora delete** Zarządzanie alokacji pamięci na natywnej stercie. Odwołanie do klasy nie można jednak zdefiniować te operatory, ponieważ są przydzielane tylko na stosie zarządzanym.

Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2842.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
