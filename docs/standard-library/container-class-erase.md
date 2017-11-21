---
title: Kontener Class::erase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 92be2dd430babc621e5f4b1f89999cf0e498306a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="container-classerase"></a>Kontener Class::erase
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
 Usuwa element.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,  
    iterator last);
```  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez *_Where*. Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`). Obie zwracają iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub [zakończenia](../standard-library/container-class-end.md) Jeżeli nie zawiera żadnego takiego elementu.  
  
 Funkcje Członkowskie Zgłoś wyjątek, tylko wtedy, gdy operacja kopiowania zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Sample Container — klasa](../standard-library/sample-container-class.md)
