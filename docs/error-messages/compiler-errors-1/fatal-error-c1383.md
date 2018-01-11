---
title: "Błąd krytyczny C1383 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1383
dev_langs: C++
helpviewer_keywords: C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24e9d7652c96c84f94bafbf2c808f2e5430037b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1383"></a>Błąd krytyczny C1383
— Opcja kompilatora /GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego  
  
 C1383 występuje w poprzedniej wersji środowiska CLR za pomocą nowszej kompilatora oraz w przypadku kompilacji z **/CLR** i   **/GL.**  
  
 Aby rozwiązać, nie należy używać **/GL** z **/CLR** lub zainstaluj wersję środowiska CLR, które zostały wydane z kompilujący.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).