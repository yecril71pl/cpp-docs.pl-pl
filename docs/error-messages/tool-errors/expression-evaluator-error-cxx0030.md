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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359803"
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator

Wyrażenie nie evaluatable

Ewaluator wyrażeń debugera nie można uzyskać wartości dla wyrażenia, jak zostały napisane. Jedną z prawdopodobnych przyczyn jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzeni adresowej programu (wyłuskanie wskaźnika o wartości null jest jednym z przykładów). Windows nie zezwala na dostęp do pamięci, która znajduje się poza przestrzeni adresowej programu.

Możesz chcieć Napisz ponownie wyrażenie przy użyciu nawiasów można określić kolejność oceny.

Ten błąd jest taka sama jak CAN0030.