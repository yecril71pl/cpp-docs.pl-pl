---
title: Błąd krytyczny C1005 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44040416fe94c2117938aa70c9e241cb5cd832fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1005"></a>Błąd krytyczny C1005
zbyt długi ciąg dla buforu  
  
 Ciąg w pośredniego pliku kompilatora nastąpiło przepełnienie buforu.  
  
 Ten błąd można uzyskać po parametr przekazywany do jednej [/Fd](../../build/reference/fd-program-database-file-name.md) lub [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) — opcje kompilatora jest większy niż 256 bajtów.