---
title: Błąd CXX0030 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500350"
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator

Wyrażenie nie evaluatable

Ewaluator wyrażeń debugera nie można uzyskać wartości dla wyrażenia, jak zostały napisane. Jedną z prawdopodobnych przyczyn jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzeni adresowej programu (wyłuskanie wskaźnika o wartości null jest jednym z przykładów). Windows nie zezwala na dostęp do pamięci, która znajduje się poza przestrzeni adresowej programu.

Możesz chcieć Napisz ponownie wyrażenie przy użyciu nawiasów można określić kolejność oceny.

Ten błąd jest taka sama jak CAN0030.