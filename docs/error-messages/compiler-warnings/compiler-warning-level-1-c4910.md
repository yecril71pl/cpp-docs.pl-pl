---
title: Kompilator ostrzeżenie (poziom 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: f0d1df0a383b6646d52fc2babc53ca656d49ace6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428200"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilator ostrzeżenie (poziom 1) C4910

"\<identyfikator >": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem

Utworzenie wystąpienia jawnego szablonu o nazwie  *\<identyfikator >* jest modyfikowany przez oba `__declspec(dllexport)` i `extern` słów kluczowych. Jednak te słowa kluczowe są wzajemnie się wykluczają. `__declspec(dllexport)` — Słowo kluczowe oznacza, że wystąpienia klasy szablonu, podczas gdy `extern` — słowo kluczowe oznacza, że nie tworzy automatycznie klasy szablonu.

## <a name="see-also"></a>Zobacz też

[Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)