---
title: Kompilatora (poziom 4) ostrzeżenie C4985 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8f0b62a72d61ee061fd996f93638acba9e7ebb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301093"
---
# <a name="compiler-warning-level-4-c4985"></a>Kompilator C4985 ostrzegawcze (poziom 4)
"Nazwa symbolu": Brak atrybutów w poprzedniej deklaracji.  
  
 Microsoft źródła kodu adnotacji języka (SAL) adnotacje w bieżącej metody deklaracji lub definicji różnią się od adnotacji wcześniejszej deklaracji. W definicji i deklaracje metody należy użyć tej samej adnotacji SAL.  
  
 SAL zapewnia zbiór adnotacje, które służą do opisywania, jak funkcja używa jego parametrów, założenia, które ułatwia ich temat i gwarancji, który pozwala na zakończenie. Adnotacje są zdefiniowane w pliku nagłówka sal.h.  
  
 Należy zauważyć, że nie rozwinie makra SAL, chyba że projektu był [/ analyze](../../build/reference/analyze-code-analysis.md) określona flaga. Po określeniu **/ analyze**, kompilator może zgłosić C4985, nawet jeśli nie ostrzeżenia i błędy pojawił się bez **/ analyze**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Użyj tej samej adnotacji SAL w definicji metody i wszystkie jego deklaracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Adnotacje SAL](../../c-runtime-library/sal-annotations.md)