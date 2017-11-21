---
title: "Błąd krytyczny C1854 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1854
dev_langs: C++
helpviewer_keywords: C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d35a3aae8f52f28e8775e09d23355e931420bfee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1854"></a>Błąd krytyczny C1854
  
> Nie można zastąpić informacji utworzonej podczas tworzenia prekompilowanego nagłówka w pliku obiektu: "*filename*"  
  
Podana [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcji po określeniu [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) opcji dla tego samego pliku.  
  
Aby rozwiązać ten problem, ogólnie rzecz biorąc, ustaw tylko jeden plik w projekcie ma być kompilowana przy użyciu **/Yc** opcji i ustaw wszystkie pliki skompilować przy użyciu **/Yu** opcji. Aby uzyskać więcej informacji dotyczących korzystania z **/Yc** opcja i ustaw go w środowisku IDE programu Visual Studio, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md). Aby uzyskać więcej informacji na temat używania prekompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md).  
