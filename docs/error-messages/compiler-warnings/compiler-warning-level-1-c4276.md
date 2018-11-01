---
title: Kompilator ostrzeżenie (poziom 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586917"
---
# <a name="compiler-warning-level-1-c4276"></a>Kompilator ostrzeżenie (poziom 1) C4276

'Funkcja': bez prototypu podane; Założono Brak parametrów

Po wykonaniu adresu funkcji z atrybutem [__stdcall](../../cpp/stdcall.md) konwencji wywoływania, musisz udzielić prototyp dzięki czemu kompilator może tworzyć dekorowane nazwy funkcji. Ponieważ *funkcja* ma bez prototypu kompilatora, tworząc nazwę z atrybutami, zakłada się, funkcja nie ma parametrów.