---
title: Błąd krytyczny C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 83eb5e01eac377b8f19a0e94dc1518e3ed557c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165647"
---
# <a name="fatal-error-c1854"></a>Błąd krytyczny C1854

> Nie można zastąpić informacji utworzonej podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: "*filename*"

Możesz określić [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcja po określeniu [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) opcji dla tego samego pliku.

Aby rozwiązać ten problem, ogólnie rzecz biorąc, ustawić tylko jeden plik projektu jest kompilowana za pomocą **/Yc** opcji, a następnie ustaw wszystkie inne pliki można skompilować przy użyciu **/Yu** opcji. Aby uzyskać szczegółowe informacje na temat użytkowania **/Yc** opcja i ustaw go w środowisku IDE programu Visual Studio, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md). Aby uzyskać więcej informacji na temat korzystania z wstępnie skompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/creating-precompiled-header-files.md).
