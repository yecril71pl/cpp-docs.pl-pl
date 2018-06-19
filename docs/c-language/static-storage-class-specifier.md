---
title: Specyfikator statycznej klasy składującej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7d61e39eb706721ddf936f88f5df02a6eddf96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386319"
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania
Zmienna zadeklarowana na poziomie wewnętrznym z **statycznych** Specyfikator klasy składującej ma globalny okres istnienia, ale nie jest widoczna tylko w bloku, w którym jest zadeklarowany. Stałe ciągi, przy użyciu **statycznych** jest przydatne, ponieważ jego eliminuje koszty częste inicjowania w funkcjach często nazywane.  
  
## <a name="remarks"></a>Uwagi  
Jeśli nie można zainicjować jawnie **statycznych** zmiennej, jest inicjowany do 0 domyślnie. Wewnątrz funkcji **statycznych** powoduje magazynu do przydzielenia i służy jako definicji. Zmienne statyczne wewnętrzne przechowywanie prywatne, stała widoczne dla tylko jednej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
[Klasy magazynu w języku C](c-storage-classes.md)  
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)  