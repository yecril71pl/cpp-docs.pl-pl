---
title: Niewłaściwy dostęp do złożenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c322ff9e411cc6c9ef845fdd9a289a9ed5c49d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383595"
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia
**ANSI 3.3.2.3** elementu Członkowskiego Unii obiektu jest dostępny przy użyciu elementu Członkowskiego innego typu  
  
 Jeśli zadeklarowano złożenie dwóch typów jest przechowywany w jedną wartość, ale Unii jest dostępny z innym typem, wyniki są niepewna.  
  
 Na przykład związek **float** i `int` jest zadeklarowany. A **float** wartość jest przechowywana, ale program później dostęp do wartości jako `int`. W takiej sytuacji, wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowita nie będzie wiarygodne.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)