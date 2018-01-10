---
title: "Błąd narzędzi konsolidatora LNK1309 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1309
dev_langs: C++
helpviewer_keywords: LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 425fb564ae2bd099746fc9b76b496595caa10a0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1309"></a>Błąd narzędzi konsolidatora LNK1309
Moduł type1 wykrył; Nieprawidłowy z przełącznikiem /CLRIMAGETYPE:type2  
  
 Typ obrazu CLR żądano **clrimagetype** , ale konsolidator nie może utworzyć obrazu tego typu, ponieważ co najmniej jednego modułu były niezgodne z danym typem.  
  
 Na przykład jeśli określisz zostanie wyświetlony LNK1309 **/CLRIMAGETYPE:safe** i przekaż Moduł skompilowany z **/CLR: pure**.  
  
 Widoczne będzie także LNK1309 przy próbie tworzenie aplikacji częściowo zaufanej czysty CLR, za pomocą .lib ptrustu [d]. Aby uzyskać informacje na temat tworzenia częściowo zaufanych aplikacji, zobacz [jak: utworzyć częściowo aplikacji zaufanej przez usunięcie zależności w pliku DLL biblioteki CRT](../../dotnet/create-a-partially-trusted-application.md).  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [clrimagetype (określenie typu z obrazu CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).