---
title: Słowa kluczowe dziedziczenia
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: f0aae655540b4d3f9130d9840d77e0abcf270cc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374103"
---
# <a name="inheritance-keywords"></a>Słowa kluczowe dziedziczenia

**Specyficzne dla firmy Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

gdzie:

*nazwa klasy*<br/>
Nazwa deklarowanej klasy.

C++ umożliwia deklarację wskaźnika do składowej klasy przed definicją klasy. Przykład:

```cpp
class S;
int S::*p;
```

W powyższym `p` kodzie jest zadeklarowany jako wskaźnik do elementu członkowskiego liczby całkowitej klasy S. Jednak `class S` nie został jeszcze zdefiniowany w tym kodzie; została tylko zadeklarowana. Gdy kompilator napotka taki wskaźnik, musi stworzyć uogólnioną reprezentację wskaźnika. Rozmiar reprezentacji zależy od określonego modelu dziedziczenia. Istnieją cztery sposoby określania modelu dziedziczenia w kompilatorze:

- W IDE w obszarze **Odwzorować wskaźnik do elementu członkowskiego**

- W wierszu polecenia za pomocą przełącznika [/vmg](../build/reference/vmb-vmg-representation-method.md)

- Korzystanie z [pragmy pointers_to_members](../preprocessor/pointers-to-members.md)

- Korzystanie ze słów kluczowych dziedziczenia **__single_inheritance** **, __multiple_inheritance**i **__virtual_inheritance**. Technika ta kontroluje model dziedziczenia na podstawie klasy.

    > [!NOTE]
    >  Jeśli zawsze deklarowany jest wskaźnik do składowej klasy po zdefiniowaniu klasy, nie trzeba używać żadnej z tych opcji.

Deklarowanie wskaźnika do składowej klasy przed definicją klasy wpływa na rozmiar i prędkość wynikowego pliku wykonywalnego. Im bardziej złożone dziedziczenie używane przez klasy, tym większa liczba bajtów jest potrzebna do reprezentowania wskaźnika do składowej klasy i więcej kodu jest wymagane do interpretacji wskaźnika. Pojedyncze dziedziczenie jest najmniej skomplikowane, a dziedziczenie wirtualne jest najbardziej złożone.

Jeśli powyższy przykład zmienimy na:

```cpp
class __single_inheritance S;
int S::*p;
```

niezależnie od opcji wiersza polecenia lub pragm, wskaźniki do elementów członkowskich `class S` będą wykorzystywały najmniejszą możliwą reprezentację.

> [!NOTE]
> Taka sama wczesna reprezentacja wskaźnika składowej klasy powinna występować w każdej jednostce translacji, która deklaruje wskaźniki do składowych tej klasy, a deklaracja powinna występować przed deklaracją wskaźników do składowych.

Aby uzyskać zgodność z poprzednimi wersjami, **_single_inheritance** **, _multiple_inheritance**i **_virtual_inheritance** są synonimami **dla __single_inheritance,** **__multiple_inheritance**i **__virtual_inheritance,** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
