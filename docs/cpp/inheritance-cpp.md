---
title: Dziedziczenie (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8538418b6457994162500dea013f2addd4269849
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inheritance--c"></a>Dziedziczenie (C++)
W tej sekcji wyjaśniono, jak za pomocą klasy pochodne tworzyć rozszerzalne programy.  
  
## <a name="overview"></a>Omówienie  
 Nowe klasy mogą pochodzić z istniejącej klasy przy użyciu mechanizmu o nazwie "dziedziczenia" (zobacz początku informacji w [pojedyncze dziedziczenie](../cpp/single-inheritance.md)). Klasy, które są używane w operacji wyprowadzenia są nazywane "klasy podstawowe" konkretnej klasy pochodnej. Klasa pochodna jest deklarowany przy użyciu następującej składni:  
  
```  
 class Derived : [virtual] [access-specifier] Base  
{  
   // member list  
};  
 class Derived : [virtual] [access-specifier] Base1,  
 [virtual] [access-specifier] Base2, . . .  
{  
   // member list  
};  
```  
  
 Po znaczniku (nazwa) dla klasy dwukropek pojawi się następuje lista podstawowa specyfikacji.  Klasy podstawowe, więc o nazwie zostało zadeklarowane wcześniej.  Specyfikacje podstawowej może zawierać specyfikatora dostępu, które jest jednym z kluczowych **publicznego**, `protected` lub `private`.  Te specyfikatory dostępu znajdują się przed nazwą klasy podstawowej i mają zastosowanie tylko do tej klasy podstawowej.  Te specyfikatorów kontroli klasy pochodnej uprawnienia do używania elementów członkowskich klasy podstawowej.  Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) informacji dotyczących dostępu do elementów członkowskich klasy podstawowej.  W przypadku pominięcia specyfikatora dostępu, dostęp do tej bazy jest uznawany za `private`.  Specyfikacje podstawowe mogą zawierać słowa kluczowego **wirtualnego** wskazująca wirtualnego dziedziczenia.  To słowo kluczowe może pojawić się przed lub po specyfikatorze dostępu, jeśli istnieje.  Użycie wirtualnego dziedziczenia klasy podstawowej jest określana jako wirtualna klasa podstawowa.  
  
 Można określić wiele klas podstawowych, oddzielonych przecinkami.  Jeśli określono pojedyncza klasa podstawowa, model dziedziczenia jest [pojedyncze dziedziczenie](../cpp/single-inheritance.md). Jeśli określono więcej niż jedną klasę podstawową, nosi nazwę modelu dziedziczenia [dziedziczenie wielokrotne](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca),  
  
 Omówiono następujące zagadnienia:  
  
-   [Pojedyncze dziedziczenie](../cpp/single-inheritance.md)  
  
-   [Dziedziczenie wielokrotne](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [Wiele klas podstawowych](../cpp/multiple-base-classes.md)  
  
-   [Funkcje wirtualne](../cpp/virtual-functions.md)  
  
-   [Jawne zastąpienia](../cpp/explicit-overrides-cpp.md)  
  
-   [Klasy abstrakcyjne](../cpp/abstract-classes-cpp.md)  
  
-   [Podsumowanie reguł zakresu](../cpp/summary-of-scope-rules.md)  
  
 [__Super](../cpp/super.md) i [__interface](../cpp/interface.md) słowa kluczowe są opisane w tej sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)