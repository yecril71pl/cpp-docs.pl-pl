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
ms.workload: cplusplus
ms.openlocfilehash: c957b78eeb506e9f1f91a670cf5cc4d52ad72878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania
Zmienna zadeklarowana na poziomie wewnętrznym z **statycznych** Specyfikator klasy składującej ma globalny okres istnienia, ale nie jest widoczna tylko w bloku, w którym jest zadeklarowany. Stałe ciągi, przy użyciu **statycznych** jest przydatne, ponieważ jego eliminuje koszty częste inicjowania w funkcjach często nazywane.  
  
## <a name="remarks"></a>Uwagi  
Jeśli nie można zainicjować jawnie **statycznych** zmiennej, jest inicjowany do 0 domyślnie. Wewnątrz funkcji **statycznych** powoduje magazynu do przydzielenia i służy jako definicji. Zmienne statyczne wewnętrzne przechowywanie prywatne, stała widoczne dla tylko jednej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
[Klasy magazynu w języku C](c-storage-classes.md)  
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)  