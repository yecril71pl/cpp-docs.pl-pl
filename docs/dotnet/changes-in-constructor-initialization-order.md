---
title: "Zmiany w kolejności inicjowania konstruktorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 499855ec5052c039e007df8348db094aee356411
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-constructor-initialization-order"></a>Zmiany w kolejności inicjowania konstruktorów
Kolejność inicjowania dla konstruktorów klasy zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
## <a name="comparison-of-constructor-initialization-order"></a>Porównanie kolejności inicjowania konstruktorów  
 W obszarze rozszerzeń zarządzanych dla języka C++ Konstruktor inicjowania wystąpił w następującej kolejności:  
  
1.  Konstruktor klasy podstawowej, jeśli istnieje, jest wywoływana.  
  
2.  Listy inicjowania klasy jest obliczane.  
  
3.  Treść kodu konstruktora klasy jest wykonywana.  
  
 Kolejność wykonywania konwencjami sam jak natywnego programowania w języku C++. W nowym języku Visual C++ określa kolejność wykonywania następujących klas CLR:  
  
1.  Listy inicjowania klasy jest obliczane.  
  
2.  Konstruktor klasy podstawowej, jeśli istnieje, jest wywoływana.  
  
3.  Treść kodu konstruktora klasy jest wykonywana.  
  
 Należy zauważyć, że ta zmiana ma zastosowanie tylko do klasy CLR; macierzystych klas w programie Visual C++ są nadal zgodne z konwencjami poprzedniej. W obu przypadkach te reguły Kaskadowo w górę łańcuchu całej hierarchii danej klasy.  
  
 Rozważmy poniższy przykład kodu przy użyciu rozszerzeń zarządzanych dla języka C++:  
  
```  
__gc class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
__gc class B : public A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 Po kolejności inicjowania konstruktorów opisane powyżej, firma Microsoft powinny być widoczne następujące kolejność wykonywania, gdy nowe wystąpienia klasy `B` są wykonane:  
  
1.  Konstruktor klasy podstawowej `A` jest wywoływana. `_n` Elementu członkowskiego jest ustawiana na `1`.  
  
2.  Na liście inicjowania dla klasy `B` oceny. `_m` Elementu członkowskiego jest ustawiana na `1`.  
  
3.  Treść kodu klasy `B` jest wykonywana.  
  
 Teraz należy wziąć pod uwagę taki sam kod w nowej składni Visual C++:  
  
```  
ref class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
ref class B : A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 Kolejność wykonywania, gdy nowe wystąpienia klasy `B` są tworzone w nowym składnia jest następująca:  
  
1.  Na liście inicjowania dla klasy `B` oceny. `_m` Elementu członkowskiego jest ustawiana na `0` (`0` niezainicjowaną wartość `_m` elementu członkowskiego klasy).  
  
2.  Konstruktor klasy podstawowej `A` jest wywoływana. `_n` Elementu członkowskiego jest ustawiana na `1`.  
  
3.  Treść kodu klasy `B` jest wykonywana.  
  
 Należy pamiętać, że podobne składni daje różne wyniki dla tych przykładów kodu. Konstruktor klasy `B` zależy od wartości z klasy podstawowej `A` zainicjować jego elementów członkowskich. Jednak konstruktora dla klasy `A` nie została jeszcze wywołana. Takie zależności mogą być szczególnie niebezpieczne dziedziczonej klasie jest zależna od pamięci lub zasobów alokacji w konstruktorze klasy podstawowej.  
  
## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Jakie oznacza to, przechodząc od rozszerzeń zarządzanych dla języka C++, Visual C++ 2010  
 W wielu przypadkach zmiany kolejności wykonywania konstruktorów klas powinny być przezroczyste dla programisty, ponieważ nie pojęcie zachowanie klasy dziedziczone mieć klas podstawowych. Jednak jak zilustrować te przykłady kodu, konstruktorów klasy dziedziczone mogą znacznie wpływać podczas ich inicjowania list są zależne od wartości elementów członkowskich klasy podstawowej. Podczas przenoszenia kodu rozszerzeń Managed Extensions for C++ do nowej składni, należy wziąć pod uwagę przenoszenie takie konstrukcje treść konstruktora klasy, których wykonanie musi występować jako ostatnia.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Konstruktory](../cpp/constructors-cpp.md)   
 