---
title: "Niewłaściwy dostęp do złożenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54eeffebcc20846666c6ebb6a2951f8d55a5b8c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia
**ANSI 3.3.2.3** elementu Członkowskiego Unii obiektu jest dostępny przy użyciu elementu Członkowskiego innego typu  
  
 Jeśli zadeklarowano złożenie dwóch typów jest przechowywany w jedną wartość, ale Unii jest dostępny z innym typem, wyniki są niepewna.  
  
 Na przykład związek **float** i `int` jest zadeklarowany. A **float** wartość jest przechowywana, ale program później dostęp do wartości jako `int`. W takiej sytuacji, wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowita nie będzie wiarygodne.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)