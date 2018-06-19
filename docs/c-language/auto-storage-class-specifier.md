---
title: automatycznie Specyfikator klasy składującej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4054b723c1e44c94be9d112f6bfbd74db8f857ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381376"
---
# <a name="auto-storage-class-specifier"></a>Specyfikator automatycznej klasy magazynowania
**Automatycznie** Specyfikator klasy składującej deklaruje zmienną automatycznej zmiennej lokalnej okres istnienia. **Automatycznie** zmiennej jest widoczna tylko w bloku, w którym jest zadeklarowany. Deklaracje **automatycznie** zmiennych mogą obejmować inicjatorów, zgodnie z opisem w [inicjowania](../c-language/initialization.md). Ponieważ zmiennych o **automatycznie** Klasa magazynu nie jest inicjowany automatycznie, należy albo jawnie zainicjować je po ich zadeklarować lub przypisać je wartościami początkowymi instrukcje w bloku. Wartości niezainicjowanej **automatycznie** zmienne są niezdefiniowane. (Lokalnej zmiennej **automatycznie** lub **zarejestrować** Klasa magazynu jest inicjowana każdorazowo, jeśli zostanie podany, inicjator jest w zakresie.)  
  
 Wewnętrznego **statycznych** można zainicjować zmiennej (zmienna statyczna z lokalnej lub zasięgu bloku) z adresem wszelkich zewnętrznych lub **statycznych** elementu, ale nie z adresu innego **automatycznie**  elementu, ponieważ adres **automatycznie** element nie jest stałą.  
  
## <a name="see-also"></a>Zobacz też  
 [Auto, słowo kluczowe](../cpp/auto-keyword.md)