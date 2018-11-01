---
title: Błąd PRJ0030 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488078"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu

Wystąpił błąd rozszerzania makra. Oceń rekursja przekroczyła 32 poziomy dla $(makro).

Ten błąd jest spowodowany przez rekursji w makrach. Na przykład jeśli ustawisz **katalog pośredni** właściwości (zobacz [strona właściwości ogólnych (projekt)](../../ide/general-property-page-project.md)) $ (IntDir), będziesz mieć rekursji.

Aby rozwiązać ten problem, nie zostanie zdefiniowana, makr lub właściwości w odniesieniu do makra, które służą do definiowania.