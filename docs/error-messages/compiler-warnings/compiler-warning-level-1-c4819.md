---
title: Kompilator ostrzeżenie (poziom 1) C4819 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac468bc605c261b66f47fdf40efd1a01a5383d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074282"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilator ostrzeżenie (poziom 1) C4819

Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (liczba). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.

C4819 występuje, gdy plik źródłowy ANSI jest skompilowany w systemie ze stroną kodową, która nie może reprezentować wszystkie znaki w pliku.

Aby rozwiązać C4819, Zapisz plik w formacie Unicode. W programie Visual Studio, wybierz **pliku**, **zaawansowane opcje zapisywania**. W **zaawansowane opcje zapisywania** okna dialogowego Wybierz kodowanie, które może reprezentować wszystkie znaki w pliku — na przykład, UTF-8 — a następnie wybierz **OK**.