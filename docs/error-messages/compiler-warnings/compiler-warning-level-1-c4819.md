---
title: "Kompilatora (poziom 1) ostrzeżenie C4819 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4819
dev_langs: C++
helpviewer_keywords: C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea22f9462ee674610ae3bbd2a55d86a048a63c83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilator C4819 ostrzegawcze (poziom 1)
Plik zawiera znak, który nie może być reprezentowany w bieżącej stronie kodowej (numer). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.  
  
 C4819 występuje, gdy plik źródłowy ANSI jest skompilowana w systemie stronę kodową, która nie może reprezentować wszystkie znaki w pliku.  
  
 Aby rozwiązać C4819, Zapisz plik w formacie Unicode. W programie Visual Studio, wybierz **pliku**, **zaawansowane opcje zapisywania**. W **zaawansowane opcje zapisywania** okno dialogowe Wybierz kodowanie, które reprezentują wszystkie znaki w pliku — na przykład UTF-8 — a następnie wybierz pozycję **OK**.