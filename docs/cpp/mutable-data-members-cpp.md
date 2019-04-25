---
title: Modyfikowalne elementy członkowskie danych (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 8d592eb97f70bfc26c075317c57ec4d5c78e3956
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301594"
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