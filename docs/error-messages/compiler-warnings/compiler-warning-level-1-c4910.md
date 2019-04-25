---
title: Kompilator ostrzeżenie (poziom 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242893"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilator ostrzeżenie (poziom 1) C4910

"\<identyfikator >": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem

Utworzenie wystąpienia jawnego szablonu o nazwie  *\<identyfikator >* jest modyfikowany przez oba `__declspec(dllexport)` i `extern` słów kluczowych. Jednak te słowa kluczowe są wzajemnie się wykluczają. `__declspec(dllexport)` — Słowo kluczowe oznacza, że wystąpienia klasy szablonu, podczas gdy `extern` — słowo kluczowe oznacza, że nie tworzy automatycznie klasy szablonu.

## <a name="see-also"></a>Zobacz także

[Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)