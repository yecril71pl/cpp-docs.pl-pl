---
title: Błąd PRJ0030 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192513"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu

Błąd rozwinięcia makra. Obliczanie rekursji przekroczyło 32 poziomów dla $ (makro).

Ten błąd jest spowodowany przez rekursję w makrach. Na przykład jeśli ustawisz właściwość **katalogu pośredniego** (patrz [ogólna Strona właściwości (projekt)](../../build/reference/general-property-page-project.md)) do $ (IntDir), będziesz mieć rekursję.

Aby rozwiązać ten problem, nie należy definiować makr ani właściwości w warunkach makr, które są używane do definiowania.
