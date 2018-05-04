---
title: Dostęp do elementu członkowskiego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8896e473f1a419f24636d7c503924b51426be24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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