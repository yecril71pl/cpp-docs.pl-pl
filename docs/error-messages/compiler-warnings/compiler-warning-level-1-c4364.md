---
title: Ostrzeżenie kompilatora (poziom 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 716f440cddc3889ec719ef3b295a0d076175be93
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966515"
---
# <a name="compiler-warning-level-1-c4364"></a>Ostrzeżenie kompilatora (poziom 1) C4364

\#przy użyciu dla zestawu "plik" wcześniej widoczny w lokalizacji (line_number) bez atrybutu as_friend; nie as_friend zastosowane

Dyrektywa `#using` została powtórzona dla danego pliku metadanych, ale kwalifikator `as_friend` nie był używany w pierwszym wystąpieniu; Kompilator zignoruje drugi `as_friend`.

Aby uzyskać więcej informacji, zobacz [zaprzyjaźnioneC++zestawy ()](../../dotnet/friend-assemblies-cpp.md).

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