---
title: Ostrzeżenie kompilatora (poziom 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: a3f29cb895da8c06ed43dd5c9956426f3f6014f1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810718"
---
# <a name="compiler-warning-level-1-c4910"></a>Ostrzeżenie kompilatora (poziom 1) C4910

"\<identyfikator >": "__declspec (dllexport)" i "extern" są niezgodne z jawnym wystąpieniem

Jawne utworzenie wystąpienia szablonu o nazwie *\<identyfikator >* jest modyfikowane przez `__declspec(dllexport)` i `extern` słowa kluczowe. Jednak te słowa kluczowe wykluczają się wzajemnie. Słowo kluczowe `__declspec(dllexport)` oznacza wystąpienie klasy szablonu, natomiast słowo kluczowe `extern` oznacza, że nie tworzy automatycznie wystąpienia klasy szablonu.

## <a name="see-also"></a>Zobacz także

[Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)