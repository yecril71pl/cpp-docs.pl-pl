---
title: Modyfikowalne elementy członkowskie danych (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179344"
---
# <a name="mutable-data-members-c"></a>Modyfikowalne elementy członkowskie danych (C++)

To słowo kluczowe może być stosowane tylko do niestatycznych i niestałych elementów członkowskich danych klasy. Jeśli element członkowski danych jest zadeklarowany jako **modyfikowalny**, dozwolone jest przypisanie wartości do tego elementu członkowskiego danych z funkcji składowej **const** .

## <a name="syntax"></a>Składnia

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Uwagi

Na przykład poniższy kod zostanie skompilowany bez błędu, ponieważ `m_accessCount` został zadeklarowany jako **modyfikowalny**i w związku z tym może być modyfikowany przez `GetFlag`, mimo że `GetFlag` jest funkcją członkowską const.

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

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
