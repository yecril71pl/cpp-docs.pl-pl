---
title: Ostrzeżenie kompilatora (poziom 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175821"
---
# <a name="compiler-warning-level-1-c4276"></a>Ostrzeżenie kompilatora (poziom 1) C4276

"Function": nie dostarczono prototypu; przyjęto, że nie ma parametrów

Gdy przyjmujesz adres funkcji z konwencją wywoływania [__stdcall](../../cpp/stdcall.md) , musisz nadać prototyp, aby kompilator mógł utworzyć nazwę dekoracyjną funkcji. Ponieważ *Funkcja* nie ma prototypu, kompilator, podczas tworzenia nazwy dekoracyjnej, zakłada, że funkcja nie ma parametrów.
