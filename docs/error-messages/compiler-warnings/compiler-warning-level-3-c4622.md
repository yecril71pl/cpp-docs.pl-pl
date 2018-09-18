---
title: Kompilator ostrzeżenie (poziom 3) C4622 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d91e3c914d6c3feeb9d2326c94efe2bc54ac98f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023244"
---
# <a name="compiler-warning-level-3-c4622"></a>Kompilator ostrzeżenie (poziom 3) C4622

zastępowanie informacji o debugowaniu utworzonych podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: 'Plik'

Informacje CodeView w określonym pliku zostało utracone, jeśli został skompilowany przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcji (Używanie prekompilowanych nagłówków).

Zmień nazwę pliku obiektu (przy użyciu [/Fo](../../build/reference/fo-object-file-name.md)) podczas tworzenia lub przy użyciu prekompilowanego nagłówka pliku i link, za pomocą nowego pliku obiektu.