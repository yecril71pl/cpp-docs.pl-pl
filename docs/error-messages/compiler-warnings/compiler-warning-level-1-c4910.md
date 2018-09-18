---
title: Kompilator ostrzeżenie (poziom 1) C4910 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6db959e467ea449a66feb3ee07c202f4dee002
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018954"
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilator ostrzeżenie (poziom 1) C4910

"\<identyfikator >": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem

Utworzenie wystąpienia jawnego szablonu o nazwie  *\<identyfikator >* jest modyfikowany przez oba `__declspec(dllexport)` i `extern` słów kluczowych. Jednak te słowa kluczowe są wzajemnie się wykluczają. `__declspec(dllexport)` — Słowo kluczowe oznacza, że wystąpienia klasy szablonu, podczas gdy `extern` — słowo kluczowe oznacza, że nie tworzy automatycznie klasy szablonu.

## <a name="see-also"></a>Zobacz też

[Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)