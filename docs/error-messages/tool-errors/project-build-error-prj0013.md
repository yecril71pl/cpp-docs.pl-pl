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
ms.openlocfilehash: aeb0ac9011697c440667a538bd1805780810fb4a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221562"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu
Zasoby systemowe mogą być krytycznie mała. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.  
  
 Ten błąd wskazuje, że brakuje zasobów systemowych. Aby rozwiązać ten problem, należy zmniejszyć obciążenie zasobów systemowych przez inne procesy/aplikacje.  
  
 Ten błąd może wystąpić, gdy poziom zabezpieczeń jest niewystarczająca do tworzenia potoków (zobacz [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).