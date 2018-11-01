---
title: Błąd krytyczny C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: feb385161c9bc13d89052b4947174fbdce7a0d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457385"
---
# <a name="fatal-error-c1854"></a>Błąd krytyczny C1854

> Nie można zastąpić informacji utworzonej podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: "*filename*"

Możesz określić [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcja po określeniu [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) opcji dla tego samego pliku.

Aby rozwiązać ten problem, ogólnie rzecz biorąc, ustawić tylko jeden plik projektu jest kompilowana za pomocą **/Yc** opcji, a następnie ustaw wszystkie inne pliki można skompilować przy użyciu **/Yu** opcji. Aby uzyskać szczegółowe informacje na temat użytkowania **/Yc** opcja i ustaw go w środowisku IDE programu Visual Studio, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md). Aby uzyskać więcej informacji na temat korzystania z wstępnie skompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md).
