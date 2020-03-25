---
title: Błąd CXX0030 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195620"
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator

wyrażenie nie jest do oceny

Ewaluatora wyrażeń w debugerze nie może uzyskać wartości dla wyrażenia jako zapisania. Jedną z możliwych przyczyn jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzenią adresową programu (na przykład można wycofać wskaźnik o wartości null). System Windows nie zezwala na dostęp do pamięci spoza przestrzeni adresowej programu.

Możesz chcieć ponownie napisać wyrażenie przy użyciu nawiasów, aby kontrolować kolejność obliczeń.

Ten błąd jest identyczny z CAN0030.
