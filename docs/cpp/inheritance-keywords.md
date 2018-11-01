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
ms.openlocfilehash: 656ee7ed38c24c9f3b8881f84d8e33ca81e3d936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462975"
---
# <a name="inheritance-keywords"></a>Słowa kluczowe dziedziczenia

**Microsoft Specific**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

gdzie:

*Nazwa klasy*<br/>
Nazwa deklarowanej klasy.

C++ umożliwia deklarację wskaźnika do składowej klasy przed definicją klasy. Na przykład:

```cpp
class S;
int S::*p;
```

W powyższym kodzie `p` jest deklarowana jako wskaźnik do liczby całkowitej składowej klasy S. Jednak `class S` ma jeszcze nie została zdefiniowana w niniejszym kodzie; go została tylko zadeklarowana. Gdy kompilator napotka taki wskaźnik, musi stworzyć uogólnioną reprezentację wskaźnika. Rozmiar reprezentacji zależy od określonego modelu dziedziczenia. Istnieją cztery sposoby określania modelu dziedziczenia w kompilatorze:

- W środowisku IDE, w obszarze **reprezentacja wskaźnika do elementu członkowskiego**

- W wierszu polecenia za pomocą [/vmg](../build/reference/vmb-vmg-representation-method.md) przełącznika

- Za pomocą [pointers_to_members](../preprocessor/pointers-to-members.md) pragma

- Za pomocą słów kluczowych dziedziczenia **__single_inheritance**, **__multiple_inheritance**, i **__virtual_inheritance**. Technika ta kontroluje model dziedziczenia na podstawie klasy.

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
>  Taka sama wczesna reprezentacja wskaźnika składowej klasy powinna występować w każdej jednostce translacji, która deklaruje wskaźniki do składowych tej klasy, a deklaracja powinna występować przed deklaracją wskaźników do składowych.

W celu zgodności z poprzednimi wersjami **_single_inheritance**, **_multiple_inheritance**, i **_virtual_inheritance** są synonimy **__ pojedynczego dziedziczenia**, **__multiple_inheritance**, i **__virtual_inheritance** chyba że — opcja kompilatora [/Za \(wyłączyć język rozszerzenia)](../build/reference/za-ze-disable-language-extensions.md) jest określony.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)