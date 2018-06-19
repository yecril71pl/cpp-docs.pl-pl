---
title: Kompilatora (poziom 1) ostrzeżenie C4819 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 718e0783c3f7afcc9af958f7940f437ac4c944b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283383"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilator C4819 ostrzegawcze (poziom 1)
Plik zawiera znak, który nie może być reprezentowany w bieżącej stronie kodowej (numer). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.  
  
 C4819 występuje, gdy plik źródłowy ANSI jest skompilowana w systemie stronę kodową, która nie może reprezentować wszystkie znaki w pliku.  
  
 Aby rozwiązać C4819, Zapisz plik w formacie Unicode. W programie Visual Studio, wybierz **pliku**, **zaawansowane opcje zapisywania**. W **zaawansowane opcje zapisywania** okno dialogowe Wybierz kodowanie, które reprezentują wszystkie znaki w pliku — na przykład UTF-8 — a następnie wybierz pozycję **OK**.