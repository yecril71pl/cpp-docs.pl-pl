---
title: Błąd ewaluatora wyrażeń CXX0030 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102817"
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator

Wyrażenie nie evaluatable

Ewaluator wyrażeń debugera nie można uzyskać wartości dla wyrażenia, jak zostały napisane. Jedną z prawdopodobnych przyczyn jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzeni adresowej programu (wyłuskanie wskaźnika o wartości null jest jednym z przykładów). Windows nie zezwala na dostęp do pamięci, która znajduje się poza przestrzeni adresowej programu.

Możesz chcieć Napisz ponownie wyrażenie przy użyciu nawiasów można określić kolejność oceny.

Ten błąd jest taka sama jak CAN0030.