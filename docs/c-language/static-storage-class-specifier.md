---
title: "Specyfikator statycznej klasy składującej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a51dfc10ac0ae05a67a280b4b76c2c92eb57a0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania
Zmienna zadeklarowana na poziomie wewnętrznym z **statycznych** Specyfikator klasy składującej ma globalny okres istnienia, ale nie jest widoczna tylko w bloku, w którym jest zadeklarowany. Stałe ciągi, przy użyciu **statycznych** jest przydatne, ponieważ jego eliminuje koszty częste inicjowania w funkcjach często nazywane.  
  
## <a name="remarks"></a>Uwagi  
Jeśli nie można zainicjować jawnie **statycznych** zmiennej, jest inicjowany do 0 domyślnie. Wewnątrz funkcji **statycznych** powoduje magazynu do przydzielenia i służy jako definicji. Zmienne statyczne wewnętrzne przechowywanie prywatne, stała widoczne dla tylko jednej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
[Klasy magazynu w języku C](c-storage-classes.md)  
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)  