---
title: Błąd krytyczny C1854 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83450169ec928bb77e46916619c84b3b9a3443a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029393"
---
# <a name="fatal-error-c1854"></a>Błąd krytyczny C1854

> Nie można zastąpić informacji utworzonej podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: "*filename*"

Możesz określić [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcja po określeniu [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) opcji dla tego samego pliku.

Aby rozwiązać ten problem, ogólnie rzecz biorąc, ustawić tylko jeden plik projektu jest kompilowana za pomocą **/Yc** opcji, a następnie ustaw wszystkie inne pliki można skompilować przy użyciu **/Yu** opcji. Aby uzyskać szczegółowe informacje na temat użytkowania **/Yc** opcja i ustaw go w środowisku IDE programu Visual Studio, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md). Aby uzyskać więcej informacji na temat korzystania z wstępnie skompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md).
