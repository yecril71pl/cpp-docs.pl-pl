---
title: Błąd PRJ0030 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099925"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu

Wystąpił błąd rozszerzania makra. Oceń rekursja przekroczyła 32 poziomy dla $(makro).

Ten błąd jest spowodowany przez rekursji w makrach. Na przykład jeśli ustawisz **katalog pośredni** właściwości (zobacz [strona właściwości ogólnych (projekt)](../../ide/general-property-page-project.md)) $ (IntDir), będziesz mieć rekursji.

Aby rozwiązać ten problem, nie zostanie zdefiniowana, makr lub właściwości w odniesieniu do makra, które służą do definiowania.