---
title: Kompilator ostrzeżenie (poziom 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 88a41c7f9edb1d2a9f6d4547336a77bd5e362882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401751"
---
# <a name="compiler-warning-level-3-c4622"></a>Kompilator ostrzeżenie (poziom 3) C4622

zastępowanie informacji o debugowaniu utworzonych podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: 'Plik'

Informacje CodeView w określonym pliku zostało utracone, jeśli został skompilowany przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcji (Używanie prekompilowanych nagłówków).

Zmień nazwę pliku obiektu (przy użyciu [/Fo](../../build/reference/fo-object-file-name.md)) podczas tworzenia lub przy użyciu prekompilowanego nagłówka pliku i link, za pomocą nowego pliku obiektu.