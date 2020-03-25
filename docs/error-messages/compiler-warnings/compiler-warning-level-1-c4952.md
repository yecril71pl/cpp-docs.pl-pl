---
title: Ostrzeżenie kompilatora (poziom 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: 560705edeb0bbdd6be760736a8d4a19d914133d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174573"
---
# <a name="compiler-warning-level-1-c4952"></a>Ostrzeżenie kompilatora (poziom 1) C4952

> "*Function*": nie znaleziono danych profilowych w bazie danych programu "*pgd_file*"

W przypadku korzystania z [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)Kompilator wykrył Moduł wejściowy, który został ponownie skompilowany po `/LTCG:PGINSTRUMENT` i ma nową funkcję (*funkcję*).

To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, uruchom polecenie `/LTCG:PGINSTRUMENT`, wykonaj ponownie wszystkie przebiegi testowe i uruchom `/LTCG:PGOPTIMIZE`.

To ostrzeżenie zostanie zastąpione błędem w przypadku użycia `/LTCG:PGOPTIMIZE`.
