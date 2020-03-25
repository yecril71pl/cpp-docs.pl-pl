---
title: Błąd kompilatora C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165878"
---
# <a name="compiler-error-c3728"></a>Błąd kompilatora C3728

"zdarzenie": zdarzenie nie ma metody podniesienia

Metadane utworzone przy użyciu języka, takie jak C#, które nie zezwalają na wywoływanie zdarzenia spoza klasy, w której został zdefiniowany, został dołączony do dyrektywy [#using](../../preprocessor/hash-using-directive-cpp.md) , a program wizualny C++ korzystający z programowania CLR próbował podnieść zdarzenie.

Aby zgłosić zdarzenie w programie utworzonym w języku takim jak C#, Klasa zawierająca zdarzenie musi także definiować metodę publiczną, która wywołuje zdarzenie.
