---
title: Ostrzeżenie kompilatora (poziom 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174781"
---
# <a name="compiler-warning-level-1-c4910"></a>Ostrzeżenie kompilatora (poziom 1) C4910

"\<identyfikator >": "__declspec (dllexport)" i "extern" są niezgodne z jawnym wystąpieniem

Jawne utworzenie wystąpienia szablonu o nazwie *\<identyfikator >* jest modyfikowane przez `__declspec(dllexport)` i `extern` słowa kluczowe. Jednak te słowa kluczowe wykluczają się wzajemnie. Słowo kluczowe `__declspec(dllexport)` oznacza wystąpienie klasy szablonu, natomiast słowo kluczowe `extern` oznacza, że nie tworzy automatycznie wystąpienia klasy szablonu.

## <a name="see-also"></a>Zobacz też

[Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)
