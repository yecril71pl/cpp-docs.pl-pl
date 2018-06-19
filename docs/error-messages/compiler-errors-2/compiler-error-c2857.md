---
title: C2857 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246350"
---
# <a name="compiler-error-c2857"></a>C2857 błąd kompilatora
"#include" instrukcja określona z opcją wiersza polecenia /Ycfilename nie został znaleziony w pliku źródłowym  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcji Nazwa dołączanego pliku, który nie znajduje się w pliku źródłowym kompilowany.  
  
 Przyczyną tego błędu `#include` instrukcji w bloku kompilacja warunkowa, który nie jest skompilowany.