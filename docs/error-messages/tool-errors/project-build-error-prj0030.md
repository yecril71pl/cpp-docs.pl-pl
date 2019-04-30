---
title: Błąd PRJ0030 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385410"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu

Wystąpił błąd rozszerzania makra. Oceń rekursja przekroczyła 32 poziomy dla $(makro).

Ten błąd jest spowodowany przez rekursji w makrach. Na przykład jeśli ustawisz **katalog pośredni** właściwości (zobacz [strona właściwości ogólnych (projekt)](../../build/reference/general-property-page-project.md)) $ (IntDir), będziesz mieć rekursji.

Aby rozwiązać ten problem, nie zostanie zdefiniowana, makr lub właściwości w odniesieniu do makra, które służą do definiowania.