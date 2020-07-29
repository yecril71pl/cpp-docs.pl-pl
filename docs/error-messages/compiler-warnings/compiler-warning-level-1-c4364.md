---
title: Ostrzeżenie kompilatora (poziom 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 5423a5525f9bef4d949bfee2de058fe19d0ec181
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220044"
---
# <a name="compiler-warning-level-1-c4364"></a>Ostrzeżenie kompilatora (poziom 1) C4364

\#Użycie dla zestawu "plik" wcześniej widziano w lokalizacji (line_number) bez atrybutu as_friend; nie as_friend zastosowane

`#using`Dyrektywa została powtórzona dla danego pliku metadanych, ale **`as_friend`** kwalifikator nie był używany w pierwszym wystąpieniu; kompilator zignoruje drugi **`as_friend`** .

Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C4364.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
