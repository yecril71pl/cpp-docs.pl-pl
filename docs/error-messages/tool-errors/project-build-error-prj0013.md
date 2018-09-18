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
ms.openlocfilehash: f7a151ca34d680a517c405e5cb6f91c18d35bedd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102648"
---
# <a name="project-build-error-prj0013"></a>Błąd PRJ0013 kompilacji projektu

Zasoby systemowe mogą być krytycznie mała. Nie można utworzyć potoku wymaganego do uruchomienia kompilacji.

Ten błąd wskazuje, że brakuje zasobów systemowych. Aby rozwiązać ten problem, należy zmniejszyć obciążenie zasobów systemowych przez inne procesy/aplikacje.

Ten błąd może wystąpić, gdy poziom zabezpieczeń jest niewystarczająca do tworzenia potoków (zobacz [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).