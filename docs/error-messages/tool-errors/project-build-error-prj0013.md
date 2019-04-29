---
title: Błąd PRJ0013 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: 868b50bdac3931465103b6b4893f7bc4d030c16d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359452"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu

Zasoby systemowe mogą być krytycznie mała. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.

Ten błąd wskazuje, że brakuje zasobów systemowych. Aby rozwiązać ten problem, należy zmniejszyć obciążenie zasobów systemowych przez inne procesy/aplikacje.

Ten błąd może wystąpić, gdy poziom zabezpieczeń jest niewystarczająca do tworzenia potoków (zobacz [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).