---
title: Błąd kompilatora C2592
ms.date: 11/04/2016
f1_keywords:
- C2592
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
ms.openlocfilehash: 2ea5919f073f2fd608dca332e721be0669760a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600151"
---
# <a name="compiler-error-c2592"></a>Błąd kompilatora C2592

"class": "base_class_2" jest odziedziczone po "base_class_1" i nie może być ponownie określone

Można określić tylko klas bazowych, które nie dziedziczą z innych klas bazowych. W tym przypadku tylko `base_class_1` jest wymagana w specyfikacji `class` ponieważ `base_class_1` już dziedziczy `base_class_2`.