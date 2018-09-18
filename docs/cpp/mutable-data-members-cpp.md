---
title: Modyfikowalne składowe danych (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de0a208341e6a687d1319c4d8d60cc8671555dd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107004"
---
# <a name="mutable-data-members-c"></a>Modyfikowalne elementy członkowskie danych (C++)

This — słowo kluczowe dotyczą wyłącznie elementy członkowskie danych niestatyczna i wartości innej niż stała klasy. Zadeklarowana składowa danych **mutable**, a następnie jest legalne, aby przypisać wartość do tego elementu członkowskiego danych, z **const** funkcja elementu członkowskiego.

## <a name="syntax"></a>Składnia

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Uwagi

Na przykład, poniższy kod zostanie skompilowana bez błędów, ponieważ `m_accessCount` został zadeklarowany jako **mutable**i może być modyfikowana przez `GetFlag` mimo że `GetFlag` jest funkcją składową const.

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)