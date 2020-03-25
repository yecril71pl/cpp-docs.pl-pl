---
title: Ostrzeżenie kompilatora (poziom 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 46f07227b5df62938cc51a7be4cf4f3595a0d947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174522"
---
# <a name="compiler-warning-level-1-c4953"></a>Ostrzeżenie kompilatora (poziom 1) C4953

> *Funkcja "Function*" została edytowana od czasu zebrania danych profilowych, dane profilowe nie są używane

W przypadku korzystania z [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)Kompilator wykrył Moduł wejściowy, który został ponownie skompilowany po `/LTCG:PGINSTRUMENT` i ma funkcję (*funkcję*), która była edytowana, a istniejące uruchomienia testów znalazły funkcję jako kandydat dla dekreślenia. Jednak w wyniku ponownego kompilowania modułu funkcja nie będzie już kandydatem do wykreślania.

To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, uruchom polecenie `/LTCG:PGINSTRUMENT`, wykonaj ponownie wszystkie przebiegi testowe i uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zastąpione błędem w przypadku użycia `/LTCG:PGOPTIMIZE`.
