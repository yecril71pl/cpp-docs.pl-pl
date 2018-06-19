---
title: Błąd PRJ0013 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0013
dev_langs:
- C++
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d055043d5c7e7b030557ab03ceb7181c664ce01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318779"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu
Zasoby systemowe mogą być krytycznie mała. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.  
  
 Ten błąd wskazuje, że brakuje zasobów systemowych. Aby rozwiązać ten problem, należy zmniejszyć obciążenie zasobów systemowych przez inne procesy/aplikacje.  
  
 Ten błąd może również wystąpić, jeśli poziom zabezpieczeń jest za mało, aby utworzyć potoków (zobacz [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).