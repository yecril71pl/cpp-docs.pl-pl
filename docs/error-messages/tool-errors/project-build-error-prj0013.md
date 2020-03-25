---
title: Błąd PRJ0013 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: d769899faa940f2754db4d2428a4d7c416b49fa4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192734"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu

Zasób systemowy może być krytycznie niski. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.

Ten błąd wskazuje, że zasoby systemu są niskie. Aby rozwiązać ten problem, Zmniejsz użycie zasobów systemowych przez inne procesy/aplikacje.

Ten błąd może również wystąpić, jeśli poziom zabezpieczeń jest niewystarczający do tworzenia potoków (zobacz [potok](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)).
