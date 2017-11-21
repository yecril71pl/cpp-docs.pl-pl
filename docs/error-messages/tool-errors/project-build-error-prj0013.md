---
title: "Błąd PRJ0013 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0013
dev_langs: C++
helpviewer_keywords: PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a5c382cc0c47340c591acf3f44642118ebdf02f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu
Zasoby systemowe mogą być krytycznie mała. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.  
  
 Ten błąd wskazuje, że brakuje zasobów systemowych. Aby rozwiązać ten problem, należy zmniejszyć obciążenie zasobów systemowych przez inne procesy/aplikacje.  
  
 Ten błąd może również wystąpić, jeśli poziom zabezpieczeń jest za mało, aby utworzyć potoków (zobacz [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).