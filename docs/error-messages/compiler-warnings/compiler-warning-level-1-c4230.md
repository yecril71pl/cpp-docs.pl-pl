---
title: Ostrzeżenie kompilatora (poziom 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: be402eed4474dd736ab237cfb5c7986741338eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163274"
---
# <a name="compiler-warning-level-1-c4230"></a>Ostrzeżenie kompilatora (poziom 1) C4230

anachronizm użyte: Modyfikatory/kwalifikatory przeplatane; kwalifikator został zignorowany

Użycie kwalifikatora przed modyfikatorem firmy Microsoft, takim jak `__cdecl`, jest nieaktualne.

## <a name="example"></a>Przykład

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
