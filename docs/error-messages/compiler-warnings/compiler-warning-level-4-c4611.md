---
title: Ostrzeżenie kompilatora (poziom 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198305"
---
# <a name="compiler-warning-level-4-c4611"></a>Ostrzeżenie kompilatora (poziom 4) C4611

Interakcja między "funkcją" C++ i zniszczeniem obiektu nie jest przenośna

Na niektórych platformach funkcje, które obejmują funkcję **catch** , mogą C++ nie obsługiwać semantyki obiektów niszczenia, gdy jest poza zakresem.

Aby uniknąć nieoczekiwanego zachowania, należy unikać używania **catch** w funkcjach, które mają konstruktory i destruktory.

To ostrzeżenie jest wysyłane tylko raz; Zobacz [pragma warning](../../preprocessor/warning.md).
