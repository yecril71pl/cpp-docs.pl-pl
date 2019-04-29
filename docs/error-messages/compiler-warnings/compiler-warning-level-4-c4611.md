---
title: Kompilator ostrzeżenie (poziom 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349675"
---
# <a name="compiler-warning-level-4-c4611"></a>Kompilator ostrzeżenie (poziom 4) C4611

Interakcja między "function" i zniszczeniem obiektu języka C++ nie jest przenośna

Na niektórych platformach funkcje, które obejmują **catch** mogą nie obsługiwać semantyki obiektów języka C++ likwidacji, gdy komputer znajduje się poza zakresem.

Aby uniknąć nieoczekiwanego zachowania, należy unikać **catch** w funkcjach, które mają konstruktory i destruktory.

To ostrzeżenie zostanie wyświetlone tylko raz; zobacz [warning elementu pragma](../../preprocessor/warning.md).