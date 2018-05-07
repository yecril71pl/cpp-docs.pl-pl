---
title: Błąd krytyczny C1005 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ff7f5dbc1f9ecb66c54f52fae4a38d1e4d4664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1005"></a>Błąd krytyczny C1005
zbyt długi ciąg dla buforu  
  
 Ciąg w pośredniego pliku kompilatora nastąpiło przepełnienie buforu.  
  
 Ten błąd można uzyskać po parametr przekazywany do jednej [/Fd](../../build/reference/fd-program-database-file-name.md) lub [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) — opcje kompilatora jest większy niż 256 bajtów.