---
title: Błąd PRJ0013 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: c78f029a3fb0e89913ce9b5ce221569e67d8faf6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509927"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu

Zasób systemowy może być krytycznie niski. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.

Ten błąd wskazuje, że zasoby systemu są niskie. Aby rozwiązać ten problem, Zmniejsz użycie zasobów systemowych przez inne procesy/aplikacje.

Ten błąd może również wystąpić, jeśli poziom zabezpieczeń jest niewystarczający do tworzenia potoków (zobacz [potok](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)).