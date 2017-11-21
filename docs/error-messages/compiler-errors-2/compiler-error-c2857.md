---
title: "C2857 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2857
dev_langs: C++
helpviewer_keywords: C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca0f2b8847600096c9e39de24c58e6a0021fa83f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2857"></a>C2857 błąd kompilatora
"#include" instrukcja określona z opcją wiersza polecenia /Ycfilename nie został znaleziony w pliku źródłowym  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcji Nazwa dołączanego pliku, który nie znajduje się w pliku źródłowym kompilowany.  
  
 Przyczyną tego błędu `#include` instrukcji w bloku kompilacja warunkowa, który nie jest skompilowany.