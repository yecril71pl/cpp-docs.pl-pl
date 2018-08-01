---
title: Słowa kluczowe dziedziczenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cadeefc9ec150aedcb99f1ed531a3478aecfce89
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408417"
---
# <a name="inheritance-keywords"></a>Słowa kluczowe dziedziczenia
**Microsoft Specific**  
  
```  
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;  
```  
  
 gdzie:  
  
 *Nazwa klasy*  
 Nazwa deklarowanej klasy.  
  
 C++ umożliwia deklarację wskaźnika do składowej klasy przed definicją klasy. Na przykład:  
  
```cpp 
class S;  
int S::*p;  
```  
  
 W powyższym kodzie `p` jest deklarowana jako wskaźnik do liczby całkowitej składowej klasy S. Jednak `class S` ma jeszcze nie została zdefiniowana w niniejszym kodzie; go została tylko zadeklarowana. Gdy kompilator napotka taki wskaźnik, musi stworzyć uogólnioną reprezentację wskaźnika. Rozmiar reprezentacji zależy od określonego modelu dziedziczenia. Istnieją cztery sposoby określania modelu dziedziczenia w kompilatorze:  
  
-   W środowisku IDE, w obszarze **reprezentacja wskaźnika do elementu członkowskiego**  
  
-   W wierszu polecenia za pomocą [/vmg](../build/reference/vmb-vmg-representation-method.md) przełącznika  
  
-   Za pomocą [pointers_to_members](../preprocessor/pointers-to-members.md) pragma  
  
-   Za pomocą słów kluczowych dziedziczenia **__single_inheritance**, **__multiple_inheritance**, i **__virtual_inheritance**. Technika ta kontroluje model dziedziczenia na podstawie klasy.  
  
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
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Słowa kluczowe](../cpp/keywords-cpp.md)