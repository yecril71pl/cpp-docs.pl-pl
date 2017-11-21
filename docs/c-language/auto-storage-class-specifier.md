---
title: "automatycznie Specyfikator klasy składującej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e80f6057a26ba7655df0a04d75dcaec2c4856ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="auto-storage-class-specifier"></a>Specyfikator automatycznej klasy magazynowania
**Automatycznie** Specyfikator klasy składującej deklaruje zmienną automatycznej zmiennej lokalnej okres istnienia. **Automatycznie** zmiennej jest widoczna tylko w bloku, w którym jest zadeklarowany. Deklaracje **automatycznie** zmiennych mogą obejmować inicjatorów, zgodnie z opisem w [inicjowania](../c-language/initialization.md). Ponieważ zmiennych o **automatycznie** Klasa magazynu nie jest inicjowany automatycznie, należy albo jawnie zainicjować je po ich zadeklarować lub przypisać je wartościami początkowymi instrukcje w bloku. Wartości niezainicjowanej **automatycznie** zmienne są niezdefiniowane. (Lokalnej zmiennej **automatycznie** lub **zarejestrować** Klasa magazynu jest inicjowana każdorazowo, jeśli zostanie podany, inicjator jest w zakresie.)  
  
 Wewnętrznego **statycznych** można zainicjować zmiennej (zmienna statyczna z lokalnej lub zasięgu bloku) z adresem wszelkich zewnętrznych lub **statycznych** elementu, ale nie z adresu innego **automatycznie**  elementu, ponieważ adres **automatycznie** element nie jest stałą.  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../cpp/auto-keyword.md)