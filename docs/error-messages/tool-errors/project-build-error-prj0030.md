---
title: Błąd PRJ0030 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811479"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu

Wystąpił błąd rozszerzania makra. Oceń rekursja przekroczyła 32 poziomy dla $(makro).

Ten błąd jest spowodowany przez rekursji w makrach. Na przykład jeśli ustawisz **katalog pośredni** właściwości (zobacz [strona właściwości ogólnych (projekt)](../../build/reference/general-property-page-project.md)) $ (IntDir), będziesz mieć rekursji.

Aby rozwiązać ten problem, nie zostanie zdefiniowana, makr lub właściwości w odniesieniu do makra, które służą do definiowania.