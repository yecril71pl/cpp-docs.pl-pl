---
title: Ostrzeżenie kompilatora (poziom 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: d94347df17bac01334cfd85c2bd9f6c8a98b5fc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174599"
---
# <a name="compiler-warning-level-1-c4951"></a>Ostrzeżenie kompilatora (poziom 1) C4951

> *Funkcja "Function*" została edytowana od czasu zebrania danych profilowych, dane profilu funkcji nie zostały użyte

Funkcja została edytowana w module wejściowym do [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), tak aby dane profilu były teraz nieprawidłowe. Moduł wejściowy został ponownie skompilowany po **/LTCG: PGINSTRUMENT** i ma funkcję (*funkcję*) z innym przepływem sterowania niż w module w czasie operacji **/LTCG: PGINSTRUMENT** .

To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, uruchom polecenie **/LTCG: PGINSTRUMENT**, wykonaj ponownie wszystkie przebiegi testowe i uruchom **/LTCG: PGOPTIMIZE**.

To ostrzeżenie zostanie zastąpione błędem, jeśli użyto **/LTCG: PGOPTIMIZE** .
