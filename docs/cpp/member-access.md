---
title: "Dostęp do elementu członkowskiego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18348c3d59457b7920f7902687f0220121c30e2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="member-access"></a>Dostęp do elementu członkowskiego
Dostęp do elementu członkowskiego klasy mogą być kontrolowane przez przeciążanie operatora dostępu do elementu członkowskiego (**->**). Ten operator jest uznawany za operatora jednoargumentowego w ten sposób użycia i funkcji przeciążenia operatora musi być funkcją członkowską klasy. W związku z tym jest deklaracja dla tych funkcji:  
  
## <a name="syntax"></a>Składnia  
  
```  
  
class-type *operator->()  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie *typu klasy* jest nazwa klasy, do której należy ten operator. Funkcja operatora dostępu do elementu członkowskiego musi być niestatyczną funkcją członkowską.  
  
 Ten operator jest używana (często w połączeniu z operatora wyłuskania wskaźnika) do zaimplementowania "wskaźniki inteligentne" sprawdzania poprawności wskaźniki przed wyłuskania lub liczba użycia.  
  
 **.** operator dostępu do elementu członkowskiego nie może być przeciążony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)